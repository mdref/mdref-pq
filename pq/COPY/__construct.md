# void pq\COPY::__construct(pq\Connection $conn, string $expression, int $direction[, string $options = NULL])

Start a COPY operation.

## Params:

* pq\Connection $conn  
  The connection to use for the COPY operation.
* string $expression  
  The expression generating the data to copy.
* int $direction  
  Data direction (pq\COPY::FROM_STDIN or pq\COPY::TO_STDOUT).
* Optional string $options = NULL  
  Any COPY options (see the [official PostgreSQL documentaion](http://www.postgresql.org/docs/current/static/sql-copy.html) for details.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
