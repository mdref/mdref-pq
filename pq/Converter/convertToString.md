# string pq\Converter::convertToString(mixed $value, int $type)

Convert a value to a string for use in a query.

## Params:

* mixed $value  
  The PHP value which should be converted to a string.
* int $type  
  The type OID the converter should handle. Irrelevant for singly-type converters.

## Returns:

* string, a textual represenation of the value accepted by the PostgreSQL server.

## Example:

	<?php
	
	abstract class Example implements pq\Converter {
		function convertToString($uuid, $type)  {
			return uuid_unparse($uuid);
		}
	}
	
	?>
