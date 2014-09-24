# pq\Result pq\Connection::exec(string $query)

[Execute one or multiple SQL queries](pq/Connection/: Executing Queries) on the connection.

> ***NOTE:***  
> Only the last result will be returned, if the query string contains more than one SQL query.


## Params:

* string $query  
  The queries to send to the server, separated by semi-colon.

## Returns:

* pq\Result

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
* pq\Exception\DomainException


## Example:

	<?php
	
	$connection = new pq\Connection;
	$result = $connection->exec("SELECT 1");
	
	?>
