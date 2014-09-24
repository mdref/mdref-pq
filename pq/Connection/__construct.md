# void pq\Connection::__construct([string $dsn = ""[, int $flags = 0]])

Create a new PostgreSQL connection.
See also [General Usage](pq/Connection/: General Usage).

## Params:
* Optional string $dsn = ""  
  A ***connection string*** as described [in the PostgreSQL documentation](http://www.postgresql.org/docs/current/static/libpq-connect.html#LIBPQ-CONNSTRING).
* Optional int $flags = 0  
  See [connection flag constants](pq/Connection#Connection.Flags:).

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

## Example:

	<?php

	$connection = new pq\Connection("dbname=test user=test password=test",
		pq\Connection::ASYNC | pq\Connection::PERSISTENT);

	?>


