# pq\LOB pq\Transaction::createLOB([int $mode = pq\LOB::RW])

Create a new *large object* and open it.
See pq\Transaction::openLOB().

## Params:

* Optional int $mode = pq\LOB::RW  
  How to open the *large object* (read, write or both; see pq\LOB constants).

## Returns:

* pq\LOB, instance of the new *large object*.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

## Example:

	<?php
	
	$connection = new pq\Connection;
	$transaction = $connection->startTransaction();
	
	$lob = $transaction->createLOB();
	$lob->write("Hello World!");
	
	// close the LOB before unlinking
	$oid = $lob->oid;
	$lob = null;
	
	$transaction->unlinkLOB($oid);
	$transaction->commit();
	
	?>
