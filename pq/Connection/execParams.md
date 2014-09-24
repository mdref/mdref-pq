# pq\Result pq\Connection::execParams(string $query, array $params[, array $types = NULL])

[Execute an SQL query](pq/Connection: Executing Queries) with properly escaped parameters substituted.

## Params:

* string $query  
  The query to execute.
* array $params  
  The parameter list to substitute.
* Optional array $types = NULL  
  Corresponding list of type OIDs for the parameters.

## Returns:

* pq\Result

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\RuntimeException
* pq\Exception\DomainException

## Example:

	<?php
	$c = new pq\Connection;
	
	$result = $c->execParams("SELECT int($1) * s, int($2) * s, int($3) * s 
		FROM generate_series(1,3) s", array(1,2,3));
	
	?>
