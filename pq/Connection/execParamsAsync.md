# pq\Result pq\Connection::execParamsAsync(string $query, array $params[, array $types = NULL])

[Asynchronously](pq/Connection/: Asynchronous Usage) [execute an SQL query](pq/Connection: Executing Queries) with properly escaped parameters substituted.

> ***NOTE***:  
  If pq\Connection::$unbuffered is TRUE, each call to pq\Connection::getResult() will generate a distinct pq\Result containing exactly one row.

## Params:

* string $query  
  The query to execute.
* array $params  
  The parameter list to substitute.
* Optional array $types = NULL  
  Corresponding list of type OIDs for the parameters.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\RuntimeException
* pq\Exception\BadMethodCallException

