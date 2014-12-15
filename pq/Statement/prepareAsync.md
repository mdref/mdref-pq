# void pq\Statement::prepareAsync()

[Asynchronously](pq/Connection/: Asynchronous Usage) re-prepare a statement that has been
deallocated. This is a no-op on already open statements.

## Params:

None.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

