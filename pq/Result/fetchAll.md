# array pq\Result::fetchAll([int $fetch_type = pq\Result::$fetchType])

Fetch all rows at once.

## Params:

* Optional int $fetch_type = pq\Result::$fetchType  
  The type the return value should have, see pq\Result::FETCH_* constants.

## Returns:

* array, all fetched rows.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException

## Example:

	<?php

	try {
		$connection = new pq\Connection;
		
		$result = $connection->exec("SELECT id, name, email FROM accounts WHERE email LIKE '_@%'");
		
		foreach ($result->fetchAll(pq\Result::FETCH_OBJECT) as $row)  {
			echo "ID:   {$row->id}\n";
			echo "Name: {$row->name}\n";
			echo "Mail: {$row->email}\n\n";
		}
	} catch (\pq\Exception $e) {
		echo $e->getMessage(), "\n";
	}

	?>

