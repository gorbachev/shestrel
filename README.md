shestrel
========

A set of simple shell scripts for working with kestrel queues. Commands supported are:

* kget: read from a queue
* kset: write to a queue
* ksize: show queue size
* kflush: flush a queue
* kflush_all: flush all queues
* kcopy: copy all items from one queue to another queue
* kpopulate: write many items to a queue

## Exit codes
Commands exit with status 0 upon success. 
Exit status 1 indicates a problem with the command arguments.
kget exits with status 2 if the queue is empty.

## Examples
    $ ksize foo
    0
    $ kpopulate foo 100
    $ ksize foo
    100
    $ kflush foo
    $ ksize foo
    0
    $ kpopulate foo 23
    $ kget foo
    value_0
    $ ksize foo
    22
    $ kset foo another_value
    $ ksize foo
    23
    $ kcopy foo bar
    Copied 23 items
    $ ksize foo
    0
    $ ksize bar
    23
    $ kpopulate foo 100
    $ ksize foo
    100
    $ ksize bar
    23
    $ kflush_all
    Flushed all queues.
    $ ksize foo
    0
    $ ksize bar
    0