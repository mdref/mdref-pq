# pq\Statement pq\Connection::prepare(string $name, string $query[, array $types = NULL])

Prepare a named statement for later execution with pq\Statement::execute().

## Params:

* string $name  
  The identifying name of the prepared statement.
* string $query  
  The query to prepare.
* Optional array $types = NULL  
  An array of type OIDs for the substitution parameters.

## Returns:

* pq\Statement, a prepared statement instance.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException


## Example:

	<?php
	
	$connection = new pq\Connection;
	
	$statement = $connection->prepare(
		"example", 
		"SELECT a from generate_series(1,9) a WHERE a > \$1", 
		[pq\Types::INT4]);
	$result = $statement->exec([5]);
	
	var_dump($result->fetchAllCols(0));
	
	?>

Yields:

	array(4) {
	  [0]=>
	  int(6)
	  [1]=>
	  int(7)
	  [2]=>
	  int(8)
	  [3]=>
	  int(9)
	}

