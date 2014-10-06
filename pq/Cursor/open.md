# void pq\Cursor::open()

Reopen a cursor.
This is a no-op on already open cursors.

> ***NOTE:***  
  Only cursors closed by pq\Cursor::close() will be reopened.

## Params:

None.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
