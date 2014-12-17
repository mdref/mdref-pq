# class pq\Statement

A named prepared statement.
See pq\Connection::prepare().

## Properties:

* public (readonly) pq\Connection $connection  
  The connection to the server.
* public (readonly) string $name  
  The identifiying name of the prepared statement.
* public (readonly) string $query
  The query string used to prepare the statement.
* public (readonly) array $types
  List of corresponding query parameter type OIDs for the prepared statement.

