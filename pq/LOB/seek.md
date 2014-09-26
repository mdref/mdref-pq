# int pq\LOB::seek(int $offset[, int $whence = SEEK_SET])

Seek to a position within the *large object*.

## Params:

* int $offset  
  The position to seek to.
* Optional int $whence = SEEK_SET  
  From where to seek (SEEK_SET, SEEK_CUR or SEEK_END).

## Returns:

* int, the new position.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
