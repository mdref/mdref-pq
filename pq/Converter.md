# interface pq\Converter

Interface for type conversions.

## Example:

	<?php
	
	/**
	 * Naive geometric point
	 */
	class Point {
		public $x;
		public $y;
		function __construct($x, $y) {
			$this->x = $x;
			$this->y = $y;
		}
	}
	
	/**
	 * A simple Box
	 */
	class Box {
		public $p1;
		public $p2;
		function __construct(Point $p1, Point $p2) {
			$this->p1 = $p1;
			$this->p2 = $p2;
		}
	}
	
	/**
	 * Our converter handles only objects of type box
	 */
	class BoxConverter implements pq\Converter {
		private $oid;
		function __construct(pq\Types $types) {
			$this->oid = $types["box"]->oid;
		}
		
		/**
		 * @return array
		 * @see pq\Converter::convertTypes()
		 */
		function convertTypes() {
			return [$this->oid];
		}
		
		/**
		 * @return string
		 * @param $box Box
		 * @see pq\Converter::convertToString()
		 */
		function convertToString($box, $type) {
			return sprintf("(%F,%F),(%F,%F)", 
				$box->p1->x, $box->p1->y,
				$box->p2->x, $box->p2->y
			);
		}
		
		/**
		 * @return Box
		 * @param string $data
		 * @see pq\Converter::convertFromString()
		 */
		function convertFromString($data, $type) {
			list($p1x, $p1y, $p2x, $p2y) = sscanf($data, "(%f,%f),(%f,%f)");
			return new Box(new Point($p1x, $p1y), new Point($p2x, $p2y));
		}
	}
	
	$conn  = new pq\Connection;
	$types = new pq\Types($conn);
	$conv  = new BoxConverter($types);
	$inbox = new Box(new Point(1.1, 2.2), new Point(3.3, 4.4));
	
	$conn->setConverter($conv);
	$result = $conn->execParams("SELECT \$1", [$inbox], [$types["box"]->oid]);
	$result->fetchCol($outbox);
	
	var_dump($outbox);
	
	?> 

Yields:

	object(Box)#163 (2) {
	  ["p1"]=>
	  object(Point)#164 (2) {
		["x"]=>
		float(3.3)
		["y"]=>
		float(4.4)
	  }
	  ["p2"]=>
	  object(Point)#165 (2) {
		["x"]=>
		float(1.1)
		["y"]=>
		float(2.2)
	  }
	}
