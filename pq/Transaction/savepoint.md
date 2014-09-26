# void pq\Transaction::savepoint()

Create a `SAVEPOINT` within this transaction.

> ***NOTE:***  
  pq\Transaction tracks an internal counter as savepoint identifier.
  
## Params:

None.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException


## Example:

	<?php
	
	$connection = new pq\Connection;
	$transaction = $connection->startTransaction();
	
	// create a savepoint
	$transaction->savepoint();
	// create another savepoint
	$transaction->savepoint();
	
	// rollback to previous savepoint
	$transaction->rollback();
	// release first savepoint
	$transaction->commit();
	// commit transaction
	$transaction->commit();
	
	?>
