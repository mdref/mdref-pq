# void pq\Statement::bind(int $param_no, mixed &$param_ref)

Bind a variable to an input parameter.
  
## Params:

* int $param_no  
  The parameter index to bind to.
* mixed &$param_ref  
  The variable to bind.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException


## Example:

	<?php
	
	$connection = new pq\Connection;
	$statement = $connection->prepare("st1", 
		"SELECT \$1 as first, \$2 as second", [pq\Types::INT4, pq\Types::INT4]);
	
	$statement->bind(1, $first);
	$statement->bind(2, $second);
	
	$first = 1;
	$second = 2;
	
	$result = $statement->exec();
	foreach ($result->fetchRow(pq\Result::FETCH_ASSOC) as $col => $val) {
		printf("%10s = %s\n", $col, $val);
	}
	
	?>

Yields:

	 first = 1
	second = 2
