# string pq\LOB::read([int $length = 0x1000[, int &$read = NULL]])

Read a string of data from the current position of the *large object*.

## Params:

* Optional int $length = 0x1000  
  The amount of bytes to read from the *large object*.
* Optional int &$read = NULL  
  The amount of bytes actually read from the *large object*.

## Returns:

* string, the data read.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pa\Exception\RuntimeException

## Example:

	<?php
	
	$connection = new pq\Connection;
	$transaction = new pq\Transaction($connection);
	
	$data = $tansaction->openLOB(123)->read(100, $read);
	
	printf("Read %d bytes: '%s'\n", $read, $data);
	
	?>
