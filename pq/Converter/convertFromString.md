# mixed pq\Converter::convertFromString(string $data, int $type)

Convert a string received from the PostgreSQL server back to a PHP type.

## Params:

* string $data  
  String data received from the server.
* int $type    
  The type OID of the data. Irrelevant for single-type converters.

## Returns:

* mixed, the value converted to a PHP type.

## Example:

	<?php
	
	abstract class Example implements pq\Converter {
		function convertFromString($data, $type) {
			return uuid_parse($data);
		}
	}
	
	?>
