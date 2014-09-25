# bool pq\Result::bind(mixed $col, mixed &$var)

Bind a variable to a result column.
See pq\Result::fetchBound().

## Params:

* mixed $col  
  The column name or index to bind to.
* mixed $var  
  The variable reference.

## Returns:

* bool, success.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException

## Example:

	<?php

	try {
		$connection = new pq\Connection;
		
		$result = $connection->exec("SELECT id, name, email FROM accounts WHERE email LIKE '_@%'");
		
		$result->bind("id", $id);
		$result->bind("name", $name);
		$result->bind("email", $email);
		
		while ($result->fetchBound()) {
			echo "ID:   {$id}\n";
			echo "Name: {$name}\n";
			echo "Mail: {$email}\n\n";
		}
	} catch (\pq\Exception $e) {
		echo $e->getMessage(), "\n";
	}

	?>

