# pq\Result pq\Statement::exec([array $params = NULL])

Execute the prepared statement.

## Params:

* Optional array $params = NULL  
  Any parameters to substitute in the preapred statement (defaults to any bou
  nd variables).

## Returns:

* pq\Result, the result of the execution of the prepared statement.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

## Example:

	<?php
	
	$connection = new pq\Connection;
	$statement = $connection->prepare("st1", "SELECT int4(\$1)");
	$result = $statement->exec([123]);
	
	?>
