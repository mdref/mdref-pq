# pq\Cursor pq\Connection::declareAsync(string $name, int $flags, string $query)

[Asynchronously](pq/Connection/: Asynchronous Usage) declare a cursor for a query.

> ***NOTE***:  
  If pq\Connection::$unbuffered is TRUE, each call to pq\Connection::getResult() will generate a distinct pq\Result containing exactly one row.

## Params:

* string $name  
  The identifying name of the cursor.
* int $flags  
  Any combination of pq\Cursor constants.
* string $query  
  The query for which to open a cursor.

## Returns:

* pq\Cursor, an open cursor instance.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\RuntimeException
* pq\Exception\BadMethodCallException
