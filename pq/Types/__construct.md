# void pq\Types::__construct(pq\Connection $conn[, array $namespaces = NULL)

Create a new instance populated with information obtained from the `pg_type` relation.

## Params:

* pq\Connection $conn  
  The connection to use.
* Optional array $namespaces = NULL  
  Which namespaces to query (defaults to `public` and `pg_catalog`).

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
