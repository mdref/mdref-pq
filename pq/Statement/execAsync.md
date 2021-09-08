# void pq\Statement::execAsync([array $params = NULL, [callable $cb = NULL]])

[Asynchronously](pq/Connection/:%20Asynchronous%20Usage) execute the prepared statement.

## Params:

* Optional array $params = NULL  
  Any parameters to substitute in the prepared statement (defaults to any bou
  nd variables).
* Optional callable $cb as function(\pq\Result $res) : void  
  Result handler callback.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

