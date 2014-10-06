# void pq\Cursor::__construct(pq\Connection $conn, int $flags, string $query[, bool $async = FALSE])

Declare a cursor.
See pq\Connection::declare().

## Params:

* pq\Connection $connection  
  The connection on which the cursor should be declared.
* int $flags  
  See pq\Cursor constants.
* string $query  
  The query for ehich the cursor should be opened.
* bool $async  
  Whether to declare the cursor [asynchronously](pq/Connection/: Asynchronous Usage).

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
