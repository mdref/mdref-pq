# void pq\Transaction::__construct(pq\Connection $conn[, bool $async = FALSE[, int $isolation = pq\Transaction::READ_COMMITTED[, bool $readonly = FALSE[, bool $deferrable = FALSE]]]])

Start a transaction.
See pq\Connection::startTransaction().

## Params:

* pq\Connection $conn  
  The connection to start the transaction on.
* Optional bool $async = FALSE  
  Whether to start the transaction [asynchronously](pq/Connection/: Asynchronous Usage).
* Optional int $isolation = pq\Transaction::READ_COMMITTED  
  The transaction isolation level (defaults to pq\Connection::$defaultTransactionIsolation).
* Optional bool $readonly = FALSE  
  Whether the transaction is readonly (defaults to pq\Connection::$defaultTransactionReadonly).
* Optional bool $deferrable = FALSE  
  Whether the transaction is deferrable (defaults to pq\Connection::$defaultTransactionDeferrable).

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException


## Example:

	<?php
	
	$connection = new pq\Connection;
	$transaction = new pq\Transaction(
		$connection, FALSE, pq\Transaction::REPEATABLE_READ);
	
	?>
