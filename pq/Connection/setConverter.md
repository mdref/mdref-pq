# void pq\Connection::setConverter(pq\ConverterInterface $converter)

Set a data type converter.

## Params:

* pq\ConverterInterface $converter  
  An instance implementing pq\ConverterInterface.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException

## Example:

	<?php
	
	class HStoreConverter implements pq\ConverterInterface
	{
		private $oids;
		
		function __construct(pq\Types $types) {
			$this->oids = [$types["hstore"]->oid];
		}
		
		function convertTypes() {
			return $this->oids;
		}
		
		function convertFromString($string) {
			return eval("return [$string];");
		}
		
		function convertToString($data) {
			$string = "";
			foreach ($data as $k => $v) {
				if (isset($v)) {
					$string .= sprintf("\"%s\"=>\"%s\",", addslashes($k), addslashes($v));
				} else {
					$string .= sprintf("\"%s\"=>NULL,", addslashes($k));
				}
			}
			return $string;
		}
	}
	$connection = new pq\Connection;
	$types = new pq\Types($connection);
	
	$connection->setConverter(new HStoreConverter($types));
	
	$result = $connection->execParams("SELECT \$1", [
		[
			"k1" => "v1",
			"k2" => "v2",
			"k3" => null
		]
	], [
		$types["hstore"]->oid
	]);
	
	var_dump(current($result->fetchAll()));
	
	?>

Yields:

	  array(1) {
		[0]=>
		array(3) {
		  ["k1"]=>
		  string(2) "v1"
		  ["k2"]=>
		  string(2) "v2"
		  ["k3"]=>
		  NULL
		}
	  }
