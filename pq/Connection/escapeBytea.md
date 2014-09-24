# string pq\Connection::escapeBytea(string $binary)

Escape binary data for use within a query with the type bytea.

> ***NOTE:***  
  The result is not wrapped in single quotes.

## Params:

* string $binary  
  The binary data to escape.

## Returns:

* string, the escaped binary data.
* FALSE, if escaping fails.

## Throws:

* pq\Exception\BadMethodCallException
