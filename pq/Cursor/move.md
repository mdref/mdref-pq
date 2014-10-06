# pq\Result pq\Cursor::move([string $spec = "1"])

Move the cursor.
See pq\Cursor::fetch().

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

See the [official PostgreSQL documentaion](http://www.postgresql.org/docs/current/static/sql-move.html) for details.

## Returns:

* pq\Result, command status.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
