# pq\Cursor pq\Connection::declare(string $name, int $flags, string $query)

Declare a cursor for a query.

## Params:

* string $name  
  The identifying name of the cursor.
* int $flags  
  Any combination of pq\Cursor constants.
* string $query  
  The query for which to open a cursor.

## Returns:

* pq\Cursor, an open cursor instance.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\RuntimeException
* pq\Exception\BadMethodCallException

## Example:

	<?php

	$connection = new pq\Connection;
	
	$cursor = $connection->declare("example", pq\Cursor::WITH_HOLD,
		"SELECT * FROM generate_series(0,29) s WHERE (s%2)=0");
	
	for (	$result = $cursor->fetch(2); 
			$result->numRows; 
			$cursor->move(1), $result = $cursor->fetch(2)) {
		foreach ($result as $row) {
			foreach ($row as $col) {
				echo "	$col";
			}
			echo "\n";
		}
	}
	
	?>

Yields:

	0
	2
	6
	8
	12
	14
	18
	20
	24
	26
