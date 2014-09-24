# pq\Result pq\Connection::getResult()

Fetch the result of an [asynchronous](pq/Connection/: Asynchronous Usage) query.

If the query hasn't finished yet, the call will block until the result is available.

## Params:

None.

## Returns:

* NULL, if there has not been a query
* pq\Result, when the query has finished

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException

## Example:

	<?php
	
	$conn = new pq\Connection;
	$conn->execAsync("SELECT 1");
	
	// ...
	
	$result = $conn->getResult();
	
	?>
