# void pq\Connection::exec(string $query[, callable $callback])

[Asynchronously](pq/Connection/: Asynchronous Usage) [execute an SQL query](pq/Connection: Executing Queries) on the connection.

> ***NOTE***:  
  If pq\Connection::$unbuffered is TRUE, each call to pq\Connection::getResult() will generate a distinct pq\Result containing exactly one row.

## Params:

* string $query  
  The query to send to the server.
* Optional callable $callback as function(pq\Result $res)  
  The callback to execute when the query finishes.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

## Example:

	<?php
	
	$connection = new pq\Connection;
	$connection->execAsync("SELECT 1", function($res) {
		//...
	});
	$connection->getResult();
	
	?>
