# pq\Result: Overview

An synchronous pq\Connection::exec*() call, or calls to pq\Connection::getResult() after using [asynchronous queries](pq/Connection/: Asynchronous Usage) returns an instance of pq\Result on success. See [Query execution](pq/Connection/: Executing Queries), optionally with [types](pq/Types/: Overview) and [Prepared Statements](pq/Statement) for details about how to execute queries.

## Fetch types:

pq\Result supports the follwing fetch types:

* pq\Result::FETCH_ARRAY  
  Fetch the row as ***numerically indexed array***.
* pq\Result::FETCH_ASSOC  
  Fetch the row as ***associative array*** indexed by column name.
* pq\Result::FETCH_OBJECT  
  Fetch the row as stdClass ***object***.

The fetch type is inherited from pq\Connection::$defaultFetchType can be set through the ***public*** property named pq\Result::$fetchType, to be used when no fetch type is specified in the call to a fetch method.

## Number of rows:

The number of rows can be obtained from the ***public readonly*** property pq\Result::$numRows, or passing the result instance, which implements the Countable interface, to the count() function.

## Number of columns:

The number of columns each row has, can be obtained from the ***public readonly*** property pq\Result::$numCols.

## Fetching everything as an array of rows:

pq\Result::fetchAll() fetches the complete result set as an array of arrays or objects, depending on the default fetch type, as explained above, or the ***fetch type*** passed as first argument to the method.

	<?php

	try {
		$connection = new pq\Connection;
		
		$result = $connection->exec("SELECT id, name, email FROM accounts WHERE email LIKE '_@%'");
		
		foreach ($result->fetchAll(pq\Result::FETCH_OBJECT) as $row)  {
			echo "ID:   {$row->id}\n";
			echo "Name: {$row->name}\n";
			echo "Mail: {$row->email}\n\n";
		}
	} catch (\pq\Exception $e) {
		echo $e->getMessage(), "\n";
	}

	?>

pq\Result implements the virtual Traversable interface, so the above task can also be accomplished by this code:

	<?php

	try {
		$connection = new pq\Connection;
		$connection->defaultFetchType = pq\Result::FETCH_OBJECT;
		
		$result = $connection->exec("SELECT id, name, email FROM accounts WHERE email LIKE '_@%'");
		
		foreach ($result as $row)  {
			echo "ID:   {$row->id}\n";
			echo "Name: {$row->name}\n";
			echo "Mail: {$row->email}\n\n";
		}
	} catch (\pq\Exception $e) {
		echo $e->getMessage(), "\n";
	}

	?>

## Iteratively fetching row by row:

pq\Result::fetchRow() will return FALSE when the end of the result set has been reached.

	<?php

	try {
		$connection = new pq\Connection;
		
		$result = $connection->exec("SELECT id, name, email FROM accounts WHERE email LIKE '_@%'");
		
		while (list($id, $name, $email) = $result->fetchRow())  {
			echo "ID:   {$id}\n";
			echo "Name: {$name}\n";
			echo "Mail: {$email}\n\n";
		}
	} catch (\pq\Exception $e) {
		echo $e->getMessage(), "\n";
	}

	?>

As with most ```fetch*()``` methods, the fetch type can be passed as argument here, too.

## Fetching a single column by row:

Because a column value can be NULL or FALSE, pq\Result::fetchCol() stores the ***value*** into the first argument ***passed by reference***. The demanded ***column index/name*** can be passed as second argument, where ***column indices start with 0***, which is also the default.

	<?php

	try {
		$connection = new pq\Connection;
		
		$result = $connection->exec("SELECT email FROM accounts WHERE email LIKE '_@%'");
		
		while ($result->fetchCol($email))  {
			echo "Mail: {$email}\n";
		}
	} catch (\pq\Exception $e) {
		echo $e->getMessage(), "\n";
	}

	?>

When the end of the result set has been reached, pq\Result::fetchCol() will return FALSE.

> ***NOTE:***
> pq\Result::fetchCol() does not accept a fetch type argument.

## Fetching bound variables:

It is possible to bind variables to result columns by reference by calling pq\Result::bind() for each demanded column and then retreive the results by calling pq\Result::fetchBound() iteratively.

	<?php

	try {
		$connection = new pq\Connection;
		
		$result = $connection->exec("SELECT id, name, email FROM accounts WHERE email LIKE '_@%'");
		
		$result->bind("id", $id);
		$result->bind("name", $name);
		$result->bind("email", $email);
		
		while ($result->fetchBound()) {
			echo "ID:   {$id}\n";
			echo "Name: {$name}\n";
			echo "Mail: {$email}\n\n";
		}
	} catch (\pq\Exception $e) {
		echo $e->getMessage(), "\n";
	}

	?>


pq\Result::bind() expects the ***column index/name*** as first argument and the ***variable to bind by reference to this result column*** as second argument.

> ***NOTE:***
> pq\Result::fetchBound() does not accept a fetch type argument.

## Fetching simple maps:

pq\Result::map() fetches the complete result set as a simple map, a ***multi dimensional array***, each dimension indexed by a column.

Consider the following example:

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

pq\Result::map() optionally expects an ***array containing the column indices/names used to index the map*** as first argument, and uses the first column (at index 0) by default. The second argument can optionally be an ***array of column indices/names*** which should build up the leaf entry of the map. A ***fetch type*** can also be specified as optional third argument.
