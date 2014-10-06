# int pq\Connection::on(string $event, callable $callback)

Listen for an event.

## Params:

* string $event  
  Any pq\Connection::EVENT_*.
* callable $callback as function(pq\Connection $c[, pq\Result $r)  
  The callback to invoke on event.

## Returns:

* int, number of previously attached event listeners.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException

## Example:

	<?php
	
	$connection = new pq\Connection;
	$connection->on(pq\Connection::EVENT_RESULT, function($c, $r) {
		printf("Got result with %d rows\n", $r->numRows);
	});
	$connection->exec("SELECT * FROM generate_series(1,3)");
	
	?>

Yields:

	Got result with 3 rows
