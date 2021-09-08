# void pq\Cursor::__construct(pq\Connection $conn, string $name, int $flags, string $query[, bool $async = FALSE])

Declare a cursor.
See pq\Connection::declare().

## Params:

* pq\Connection $connection  
  The connection on which the cursor should be declared.
* string $name  
  The name of the cursor.
* int $flags  
  See pq\Cursor constants.
* string $query  
  The query for which the cursor should be opened.
* bool $async  
  Whether to declare the cursor [asynchronously](pq/Connection/:%20Asynchronous%20Usage).

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
