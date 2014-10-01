# pq\Types AKA pg_type

The pq\Types class provides an easy interface to access information stored in PostgreSQL's pg_type relation, f.e. type OIDs and names.


The first argument to the pq\Types constructor must be an instance of pq\Connection.
An optional array of namespace names is expected as second argument, where 'public' and 'pg_catalog' are queried by default if no namespaces are specified.

	<?php
	
	$types = new pq\Types(new pq\Connection);
	
	?>

The types are standard objects indexed by OID and by name and accessible by array key/index:

	<?php
	
	$text = $types["text"];
	$text = $types[25];
	
	printf("TEXT type (oid=%d, name=%s)\n", $text->oid, $text->typname);
	
	?>

> ***NOTE:***  
  The pg_type relation fields have a ``typ`` prefix.

## Usage when [executing queries](pq/Connection/: Executing Queries)


	<?php
	
	$connection = new pq\Connection;
	$types = new pq\Types($connection);
	$result = $connection->execParams(
		"SELECT \$1 + \$2", 
		array(10, 20), 
		array($types["int4"]->oid, $types["int4"]->oid));
	
	?>

You can pass a type OID for each parameter of a pepared statement.  The PostgreSQL server will try to infer a type by context for any parameters for which no type OID was specified.

## Static types

pq\Types has class constants for the standard types' OIDs already defined.

	<?php
	$connection = new pq\Connection;
	$result = $connection->execParams("SELECT \$1 + \$2", 
		array(10, 20), 
		array(pq\Types::INT4, pq\Types::INT4));


### pq\Datetime

Date/time values will automatically be converted to pq\Datetime objects.

	<?php

	$conn = new pq\Connection();
	$data = $conn->exec("
		SELECT 
			 NOW()::date
			,NOW()::abstime
			,NOW()::timestamp
			,NOW()::timestamptz
	")->fetchRow(pq\Result::FETCH_ARRAY);

	foreach ($data as $datetime) {
		printf("%-40s (%s)\n", $datetime, $datetime->format);
	}
	
	?>

Outputs:

	2013-09-20                               (Y-m-d)
	2013-09-20 14:34:38                      (Y-m-d H:i:s)
	2013-09-20 14:34:38.494886               (Y-m-d H:i:s.u)
	2013-09-20 14:34:38.494886+0200          (Y-m-d H:i:s.uO)

## Custom converters

ext-pq provides the interface pq\Converter which one can implement to perform custom type conversions in a transparent manner. Consider the following naive example converting `HSTORE` columns on the fly:

	<?php

	class Hstore implements pq\Converter
	{
		private $oid;
		
		function __construct(pq\Types $types) {
			$this->oid = $types["hstore"]->oid;
		}
		
		function convertTypes() {
			return [$this->oid];
		}
		
		function convertFromString($string, $type) {
			return eval("return [$string];");
		}
		
		function convertToString($data, $type) {
			$string = "";
			foreach ($data as $k => $v) {
				$string .= "\"".addslashes($k)."\"=>";
				if (isset($v)) {
					$string .= "\"".addslashes($v)."\",";
				} else {
					$string .= "NULL,";
				}
			}
			return $string;
		}
	}

	$conn = new pq\Connection();
	$type = new pq\Types($conn);
	$conv = new Hstore($type);
	$conn->setConverter($conv);
	$conn->exec("SELECT '\"foo\"=>\"bar\"'::hstore hs")->fetchCol(0, $data);

	print_r($data);

	?>

Output would be the following:

	Array
	(
		[foo] => bar
	)
