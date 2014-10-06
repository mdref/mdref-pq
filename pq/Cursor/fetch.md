# pq\Result pq\Cursor::fetch([string $spec = "1"])

Fetch rows from the cursor.
See pq\Cursor::move().

## Params:

* Optional string $spec = "1"  
  What to fetch.

### Fetch argument:

FETCH and MOVE usually accepts arguments like the following, where `count` is the number of rows:

* NEXT
* PRIOR
* FIRST
* LAST
* ABSOLUTE `count`
* RELATIVE `count`
* `count`
* ALL
* FORWARD
* FORWARD `count`
* FORWARD ALL
* BACKWARD
* BACKWARD `count`
* BACKWARD ALL

See the [official PostgreSQL documentaion](http://www.postgresql.org/docs/current/static/sql-fetch.html) for details.

## Returns:

* pq\Result, the fetched row(s).

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

## Example:

	<?php
	
	$c = new pq\Connection;
	$p = new pq\Cursor($c, "mycursor", pq\Cursor::WITH_HOLD,
		"SELECT * FROM generate_series(0,29) s WHERE (s%2)=0");
	
	for ($r = $p->fetch(2); $r->numRows; $p->move(1), $r = $p->fetch(2)) {
		foreach ($r as $row) {
			foreach ($row as $col) {
				echo "	$col";
			}
			echo "\n";
		}
	}
	
	?>

Yields:

	0
	2
	6
	8
	12
	14
	18
	20
	24
	26
