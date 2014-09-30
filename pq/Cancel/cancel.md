# void pq\Cancel::cancel()

Perform the cancellation request.

## Params:

None.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException


## Example:

	<?php
	
	$conn = new pq\Connection;
	$cancel = new pq\Cancel($conn);
	
	$conn->execAsync("SELECT pg_sleep(1)");
	$cancel->cancel();
	
	var_dump($conn->getResult());
	
	?>

Yields:

	object(pq\Result)#4 (8) {
	  ["status"]=>
	  int(7)
	  ["statusMessage"]=>
	  string(11) "FATAL_ERROR"
	  ["errorMessage"]=>
	  string(47) "ERROR:  canceling statement due to user request"
	  ["numRows"]=>
	  int(0)
	  ["numCols"]=>
	  int(0)
	  ["affectedRows"]=>
	  int(0)
	  ["fetchType"]=>
	  int(0)
	  ["autoConvert"]=>
	  int(65535)
	}
