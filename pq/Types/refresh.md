# void pq\Types::refresh([array $namespaces = NULL])

Refresh type information from `pg_type`.

## Params:

* Optional array $namespaces = NULL  
  Which namespaces to query (defaults to `public` and `pg_catalog`).

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

