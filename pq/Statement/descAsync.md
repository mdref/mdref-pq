# void pq\Statement::descAsync(callable $callback)

[Asynchronously](pq/Connection/: Asynchronous Usage) describe the parameters of the prepared statement.

## Params:

* callable $callback as function(array $oids)  
  A callback to receive list of type OIDs of the substitution parameters.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
