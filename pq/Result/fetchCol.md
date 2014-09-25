# bool pq\Result::fetchCol(mixed &$ref[, mixed $col = 0])

Iteratively fetch a single column.

## Params:

* mixed $ref  
  The variable where the column value will be stored in.
* Optional mixed $col = 0  
  The column name or index.

## Returns:

* bool, success.
* NULL, when iteration ends.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

## Example:

	<?php

	try {
		$connection = new pq\Connection;
		
		$result = $connection->exec("SELECT email FROM accounts WHERE email LIKE '_@%'");
		
		while ($result->fetchCol($email))  {
			echo "Mail: {$email}\n";
		}
	} catch (\pq\Exception $e) {
		echo $e->getMessage(), "\n";
	}

	?>
