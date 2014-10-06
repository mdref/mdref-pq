# array pq\Result::map([mixed $keys = 0[, mixed $vals = NULL]])

Fetch the complete result set as a simple map, a *multi dimensional array*, each dimension indexed by a column.

## Params:

* Optional mixed $keys = 0  
  The the column indices/names used to index the map.
* Optional mixed $vals = NULL  
  The column indices/names which should build up the leaf entry of the map.

## Returns:

* array, the mapped columns.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

## Example:

	<?php

	try {
		$connection = new pq\Connection;
		
		$result = $connection->exec("SELECT a,b,c from generate_series(1,3) a, 
													   generate_series(4,6) b, 
													   generate_series(7,9) c");

		foreach($result->map(array(0,1,2)) as $a => $aa) {
			foreach ($aa as $b => $bb) {
				foreach ($bb as $c => $res) {
					printf("%s,%s,%s = %s   ", $a, $b, $c, implode(",", $res));
				}
				printf("\n");
			}
			printf("\n");
		}
	} catch (\pq\Exception $e) {
		echo $e->getMessage(), "\n";
	}

	?>


It should produce:

	1,4,7 = 1,4,7   1,4,8 = 1,4,8   1,4,9 = 1,4,9   
	1,5,7 = 1,5,7   1,5,8 = 1,5,8   1,5,9 = 1,5,9   
	1,6,7 = 1,6,7   1,6,8 = 1,6,8   1,6,9 = 1,6,9   

	2,4,7 = 2,4,7   2,4,8 = 2,4,8   2,4,9 = 2,4,9  // This should help generate maps 
	2,5,7 = 2,5,7   2,5,8 = 2,5,8   2,5,9 = 2,5,9  // of f.e. statistical data with   
	2,6,7 = 2,6,7   2,6,8 = 2,6,8   2,6,9 = 2,6,9  // some GROUP BYs etc.           

	3,4,7 = 3,4,7   3,4,8 = 3,4,8   3,4,9 = 3,4,9   
	3,5,7 = 3,5,7   3,5,8 = 3,5,8   3,5,9 = 3,5,9   
	3,6,7 = 3,6,7   3,6,8 = 3,6,8   3,6,9 = 3,6,9   
