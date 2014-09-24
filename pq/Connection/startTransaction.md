# pq\Transaction pq\Connection::startTransaction([int $isolation = pq\Transaction::READ_COMMITTED[, bool $readonly = FALSE[, bool $deferrable = FALSE]]])

Begin a transaction.

## Params:

* Optional int $isolation = pq\Transaction::READ_COMMITTED  
  Any pq\Transaction isolation level constant  
  (defaults to pq\Connection::$defaultTransactionIsolation).
* Optional bool $readonly = FALSE  
  Whether the transaction executes only reads  
  (defaults to pq\Connection::$defaultTransactionReadonly).
* Optional bool $deferrable = FALSE  
  Whether the transaction is deferrable  
  (defaults to pq\Connection::$defaultTransactionDeferrable).

> ***NOTE:***  
  A transaction can only be deferrable if it also is readonly and serializable.  
  See the official [PostgreSQL documentaion](http://www.postgresql.org/docs/current/static/sql-set-transaction.html) for further information.

## Returns:

* pq\Transaction, a begun transaction instance.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException


## Example:

	<?php
	
	$transaction = (new pq\Connection)->startTransaction(
		pq\Transaction::SERIALIZABLE, true, true);
	$result = $transaction->connection->exec(
		"SELECT * FROM generate_series(1,3)");
	
	?>
