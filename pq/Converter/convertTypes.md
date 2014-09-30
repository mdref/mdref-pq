# array pq\Converter::convertTypes()

Announce which types the implementing converter can handle.

## Params:

None.

## Returns:

* array, OIDs of handled types.

## Example:

	<?php
	
	abstract class Example implements pq\Converter {
		function convertTypes() {
			return [pq\Types::UUID];
		}
	}
	
	?>
