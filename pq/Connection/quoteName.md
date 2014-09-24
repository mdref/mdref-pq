# string pq\Connection::quoteName(string $name)

Quote an identifier for safe usage as name.

> ***NOTE:***  
  Beware of case-sensitivity.

## Params:

* string $name  
  The name to quote.

## Returns:

* string, the quoted identifier.
* FALSE, if quoting fails.

## Throws:

* pq\Exception\BadMethodCallException
