# class pq\Cursor

Declare a cursor.

## Constants:

* BINARY  
  Causes the cursor to return data in binary rather than in text format. You probably do not want to use that.
* INSENSITIVE  
  The data returned by the cursor should be unaffected by updates to the tables underlying the cursor that take place after the cursor was opened.
* WITH_HOLD  
  The cursor should stay usable after the transaction that created it was successfully committed.
* SCROLL  
  Force that rows can be retrieved in any order from the cursor.
* NO_SCROLL  
  Force that rows are only retrievable in sequiential order.

> ***NOTE:***  
  See the [notes in the official PostgreSQL documentation](http://www.postgresql.org/docs/current/static/sql-declare.html#SQL-DECLARE-NOTES) for more information.

## Properties:

* public (readonly) pq\Connection $connection  
  The connection the cursor was declared on.
* public (readonly) string $name  
  The identifying name of the cursor.
