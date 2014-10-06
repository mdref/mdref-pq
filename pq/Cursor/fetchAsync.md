# void pq\Cursor::fetchAsync([string $spec = "1"[, callable $callback = NULL]])

[Asynchronously](pq/Connection/: Asynchronous Usage) fetch rows from the cursor.
See pq\Cursor::fetch().

## Params:

* Optional string $spec = "1"  
  What to fetch.
* Optional callable $callback as function(pq\Result $res)  
  A callback to execute when the result is ready.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
