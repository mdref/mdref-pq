# array pq\Statement::desc()

Describe the parameters of the prepared statement.

## Params:

None.

## Returns:

* array, list of type OIDs of the substitution parameters.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
* pq\Exception\DomainException

## Example:

	<?php
	
	$connection = new pq\Connection;
	$types = new pq\Types($connection);
	$statement = $connection->prepare("st1", 
		"SELECT \$1, \$2", [pq\Types::XML, pq\Types::JSON]);
	$description = $statement->desc();
	
	foreach($description as $typeOid) {
		echo $types[$typeOid]->typname, "\n";
	}
	
	?>

Yields:

	xml
	json
