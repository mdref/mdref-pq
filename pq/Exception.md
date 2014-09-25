# interface pq\Exception

A base interface for all pq\Exception classes.

## Constants:

* INVALID_ARGUMENT  
  An invalid argument was passed to a method (pq\Exception\InvalidArgumentException).
* RUNTIME  
  A runtime exception occurred (pq\Exception\RuntimeException).
* CONNECTION_FAILED  
  The connection failed (pq\Exception\RuntimeException).
* IO  
  An input/output exception occurred (pq\Exception\RuntimeException).
* ESCAPE  
  Escaping an argument or identifier failed internally (pq\Exception\RuntimeException).
* UNINITIALIZED  
  An object's constructor was not called (pq\Exception\BadMethodCallException).
* BAD_METHODCALL  
  Calling this method was not expected (yet) (pq\Exception\BadMethodCallException).
* SQL  
  SQL syntax error (pq\Exception\DomainException).
* DOMAIN  
  Implementation domain error (pq\Exception\DomainException).
  

## Example:

	<?php
	
	try {
		$connection = new pq\Connection;
	} catch (pq\Exception $e) {
		printf("%s (%d)\n", $e->getMessage(), $e->getCode());
	}
	
	?>
