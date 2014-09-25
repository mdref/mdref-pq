# array pq\Result::desc()

Describe a prepared statement.

> ***NOTE:***  
  This will only return meaningful information for a result of pq\Statement::desc().

## Params:

None.

## Returns:

* array, list of parameter type OIDs for the prepared statement.

## Throws:

* pq\Exception\BadMethodCallException


## Example:

	<?php
	
	$connection = new pq\Connection;
	$types = new pq\Types($connection);
	$statement = $connection->prepare("test1", "SELECT NOW() - \$1");
	$description = $statement->desc();

	printf("%s\n", $types[$description[0]]->typname);

	?>

Yields:

	timestamptz
