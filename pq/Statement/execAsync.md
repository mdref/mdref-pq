# void pq\Statement::execAsync([array $params = NULL])

[Asynchronously](pq/Connection/: Asynchronous Usage) execute the prepared statement.

## Params:

* Optional array $params = NULL  
  Any parameters to substitute in the preapred statement (defaults to any bou
  nd variables).

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

