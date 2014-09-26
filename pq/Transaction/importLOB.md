# int pq\Transaction::importLOB(string $local_path[, int $oid = pq\LOB::INVALID_OID)

Import a local file into a *large object*.

## Params:

* string $local_path  
  A path to a local file to import.
* Optional int $oid = pq\LOB::INVALID_OID  
  The target OID. A new *large object* will be created if INVALID_OID.

## Returns:

* int, the (new) OID of the *large object*.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

## Example:

	<?php
	
	$connection = new pq\Connection;
	$transaction = $connection->startTransaction();
	
	$oid = $transaction->importLOB(__FILE__);
	$lob = $transaction->openLOB($oid);
	
	var_dump($lob);
	
	?>

Yields:

	object(pq\LOB)#5 (3) {
	  ["transaction"]=> {
	  	...
	  }
	  ["oid"]=>
	  int(74492)
	  ["stream"]=>
	  resource(6) of type (stream)
	}
