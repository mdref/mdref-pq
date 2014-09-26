# int pq\LOB::write(string $data)

Write data to the *large object*.

## Params:

* string $data  
  The data that should be writte to the current position.

## Returns:

* int, the number of bytes written.

## Throw:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

## Example:

	<?php
	
	$connection = new pq\Connection;
	$transaction = $connection->startTransaction();
	
	$transaction->createLOB()->write("Hello World!");
	$transaction->rollback();
	
	?>
