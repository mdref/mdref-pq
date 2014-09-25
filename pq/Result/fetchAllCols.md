# array pq\Result::fetchAllCols([int $col = 0])

Fetch all rows of a single column.

## Params:

* Optional int $col = 0  
  The column name or index to fetch.

## Returns:

* array, list of column values.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

## Example:

	<?php
	
	/* Of the following result set:

					id | name
					---|------
					 1 | ann
					 2 | barb 
					 3 | john 
					 4 | mike 
					
	*/
	
	$result->fetchAllCols(0);	/* 	this call would fetch:
									array(4) {
										int(1),
										int(2),
										int(3),
										int(4)
									}
								*/
								
	$result->fetchAllCols("name");	/* 	this call would fetch:
										array(4) {
											string(3) "ann",
											string(4) "barb",
											string(4) "john",
											string(4) "mike"
										}
									*/
