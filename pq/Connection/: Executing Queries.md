# Executing queries

ext/pq provides three means to execute queries against the PostgreSQL server:

* pq\Connection::exec()  
  Simple plain execution of a query.
* pq\Connection::execParams()  
  Automatic prepare & execute of an unnamed statement.
* pq\Connection::prepare() and pq\Statement::exec()  
  Explicit prepare & execute of an named statement.


## Simple plain execution of a query

pq\Connection::exec() accepts a single argument, a ***query string***, containing a single or multiple SQL queries, separated by semi-colon.  

	<?php
	$result = $c->exec("SELECT 1*s,2*s,3*s FROM generate_series(1,3) s");
	?>

An object of class pq\Result is returned on success. See [Fetching results](pq/: Fetching Results) for details.

> ***NOTE:***  
> Only the last result will be returned, if the query string contains more than one SQL query.


## Automatic prepare & execute of an unnamed statement

pq\Connection::execParams() accepts a ***query string*** with a single SQL query as first argument, which will be prepared as an unnamed statement.

The second argument is an ***array of parameters*** to execute the prepared statement with.

If the third argument is present, an ***array with pg_type OIDs***, those types will be used for the parameters. See [Using types](pq/: Using Types) for details.

	<?php
	$result = $c->execParams("SELECT int($1) * s, int($2) * s, int($3) * s FROM generate_series(1,3) s", array(1,2,3));
	?>

An object of class pq\Result is returned on success. See [Fetching results](pq/: Fetching Results) for details.


## Explicit prepare & execute of a named statement

pq\Connection::prepare() requires the ***statement name*** as string as first argument. This name is used later to refer to this prepared statement. See [Prepared statements](pq/: Prepared Statements) for details.

The second argument is a ***query string*** containing a single SQL query, which will be prepared on the server.

If the third argument is present, an ***array with pg_type OIDs***, those types will be used for the parameters. See [Using types](pq/: Using Types) for details.

	<?php
	
	$statement = $c->prepare("my_stm", "SELECT \$1::int*s,\$2::int*s,\$3::int*s FROM generate_series(1,3) s");
	$result = $statement->exec(array(1,2,3));
	
	?>

An object of class pq\Statement will be returned on success. See [Prepared statements](pq/: Prepared Statements) for details.
