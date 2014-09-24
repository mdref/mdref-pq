# pq\Statement pq\Connection::prepareAsync(string $name, string $query[, array $types = NULL])

[Asynchronously](pq/Connection/: Asynchronous Usage) prepare a named statement for later execution with pq\Statement::exec().

> ***NOTE***:  
  If pq\Connection::$unbuffered is TRUE, each call to pq\Connection::getResult() will generate a distinct pq\Result containing exactly one row.

## Params:

* string $name  
  The identifying name of the prepared statement.
* string $query  
  The query to prepare.
* Optional array $types = NULL  
  An array of type OIDs for the substitution parameters.

## Returns:

* pq\Statement, a prepared statement instance.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
