# class pq\COPY

Fast import/export using COPY.

## Constants:

* FROM_STDIN  
  Start a COPY operation from STDIN to the PostgreSQL server.
* TO_STDOUT  
  Start a COPY operation from the server to STDOUT.

## Properties:

* public (readonly) pq\Connection $connection  
  The connection to the PostgreSQL server.
* public (readonly) string $expression  
  The expression of the COPY statement used to start the operation.
* public (readonly) int $direction  
  The drection of the COPY operation (pq\COPY::FROM_STDIN or pq\COPY::TO_STDOUT).
* public (readonly) string $options  
  Any additional options used to start the COPY operation.
