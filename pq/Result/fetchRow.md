# mixed pq\Result::fetchRow([int $fetch_type = pq\Result::$fetchType])

Iteratively fetch a row.

## Params:

* Optional int $fetch_type = pq\Result::$fetchType  
  The type the return value should have, see pq\Result::FETCH_* constants.

## Returns:

* array, numerically indexed for pq\Result::FETCH_ARRAY
* array, associatively indexed for pq\Result::FETCH_ASSOC
* object, stdClass instance for pq\Result::FETCH_OBJECT
* NULL, when iteration ends.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

## Example:

<?php

	try {
		$connection = new pq\Connection;
		
		$result = $connection->exec("SELECT id, name, email FROM accounts WHERE email LIKE '_@%'");
		
		while (list($id, $name, $email) = $result->fetchRow())  {
			echo "ID:   {$id}\n";
			echo "Name: {$name}\n";
			echo "Mail: {$email}\n\n";
		}
	} catch (\pq\Exception $e) {
		echo $e->getMessage(), "\n";
	}

	?>
