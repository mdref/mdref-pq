# void pq\Cursor::moveAsync([string $spec = "1"])

[Asynchronously](pq/Connection/: Asynchronous Usage) move the cursor.
See pq\Cursor::move().

## Params:

* Optional string $spec = "1"  
  What to fetch.
* Optional callable $callback as function(pq\Result $res)  
  A callback to execute when the command completed.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
