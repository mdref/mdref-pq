# void pq\Statement::__construct(pq\Connection $conn, string $name, string $query[, array $types = NULL[, bool $async = FALSE]])

Prepare a new statement.
See pq\Connection::prepare().

## Params:

* pq\Connection $conn  
  The connection to prepare the statement on.
* string $name  
  The name identifying this statement.
* string $query  
  The actual query to prepare.
* Optional array $types = NULL  
  A list of corresponding query parameter type OIDs.
* Optional bool $async = FALSE  
  Whether to prepare the statement [asynchronously](pq/Connection/: Asynchronous Usage).

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
* pq\Exception\DomainException

## Example:

	<?php
	
	$connection = new pq\Connection;
	$statement = new pq\Statement(
		$connection,
		"my_statement",
		"SELECT \$1",
		[pq\Types::INT4]
	);
	
	$result = $statement->exec([123]);
	$result->fetchCol($col);
	
	echo "Got: $col\n";
	
	?>

Yields:

	Got: 123
