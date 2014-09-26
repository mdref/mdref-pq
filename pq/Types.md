# class pq\Types implements ArrayAccess

Accessor to the PostgreSQL `pg_type` relation.

> ***NOTE:***  
  The following OID constants are obtained from stock PostgreSQL 9.3.5. Types from f.e. extensions can be accessed through the ArrayAccess interface of pq\Types.

## Example:

	<?php
	
	$connection = new pq\Connection;
	$types = new pq\Types($connection);
	foreach ($types["int2vector"] as $key=>$val) {
		printf("%-20s = %s\n", $key, is_bool($val) ? ($val?'t':'f') : $val);
	}
	
	?>

Yields:

	oid                  = 22
	typname              = int2vector
	typnamespace         = 11
	typowner             = 10
	typlen               = -1
	typbyval             = f
	typtype              = b
	typcategory          = A
	typispreferred       = f
	typisdefined         = t
	typdelim             = ,
	typrelid             = 0
	typelem              = 21
	typarray             = 1006
	typinput             = int2vectorin
	typoutput            = int2vectorout
	typreceive           = int2vectorrecv
	typsend              = int2vectorsend
	typmodin             = -
	typmodout            = -
	typanalyze           = -
	typalign             = i
	typstorage           = p
	typnotnull           = f
	typbasetype          = 0
	typtypmod            = -1
	typndims             = 0
	typcollation         = 0
	typdefaultbin        = 
	typdefault           = 
	typacl               = 


## Constants:

* BOOL  
  OID of the `bool` type.
* BYTEA  
  OID of the `bytea` type.
* CHAR  
  OID of the `char` type.
* NAME  
  OID of the `name` type.
* INT8  
  OID of the `int8` type.
* INT2  
  OID of the `int2` type.
* INT2VECTOR  
  OID of the `int2vector` type.
* INT4  
  OID of the `int4` type.
* REGPROC  
  OID of the `regproc` type.
* TEXT  
  OID of the `text` type.
* OID  
  OID of the `oid` type.
* TID  
  OID of the `tid` type.
* XID  
  OID of the `xid` type.
* CID  
  OID of the `cid` type.
* OIDVECTOR  
  OID of the `oidvector` type.
* PG_TYPE  
  OID of the `pg_type` type.
* PG_ATTRIBUTE  
  OID of the `pg_attribute` type.
* PG_PROC  
  OID of the `pg_proc` type.
* PG_CLASS  
  OID of the `pg_class` type.
* JSON  
  OID of the `json` type.
* XML  
  OID of the `xml` type.
* XMLARRAY  
  OID of the `xmlarray` type.
* JSONARRAY  
  OID of the `jsonarray` type.
* PG_NODE_TREE  
  OID of the `pg_node_tree` type.
* SMGR  
  OID of the `smgr` type.
* POINT  
  OID of the `point` type.
* LSEG  
  OID of the `lseg` type.
* PATH  
  OID of the `path` type.
* BOX  
  OID of the `box` type.
* POLYGON  
  OID of the `polygon` type.
* LINE  
  OID of the `line` type.
* LINEARRAY  
  OID of the `linearray` type.
* FLOAT4  
  OID of the `float4` type.
* FLOAT8  
  OID of the `float8` type.
* ABSTIME  
  OID of the `abstime` type.
* RELTIME  
  OID of the `reltime` type.
* TINTERVAL  
  OID of the `tinterval` type.
* UNKNOWN  
  OID of the `unknown` type.
* CIRCLE  
  OID of the `circle` type.
* CIRCLEARRAY  
  OID of the `circlearray` type.
* MONEY  
  OID of the `money` type.
* MONEYARRAY  
  OID of the `moneyarray` type.
* MACADDR  
  OID of the `macaddr` type.
* INET  
  OID of the `inet` type.
* CIDR  
  OID of the `cidr` type.
* BOOLARRAY  
  OID of the `boolarray` type.
* BYTEAARRAY  
  OID of the `byteaarray` type.
* CHARARRAY  
  OID of the `chararray` type.
* NAMEARRAY  
  OID of the `namearray` type.
* INT2ARRAY  
  OID of the `int2array` type.
* INT2VECTORARRAY  
  OID of the `int2vectorarray` type.
* INT4ARRAY  
  OID of the `int4array` type.
* REGPROCARRAY  
  OID of the `regprocarray` type.
* TEXTARRAY  
  OID of the `textarray` type.
* OIDARRAY  
  OID of the `oidarray` type.
* TIDARRAY  
  OID of the `tidarray` type.
* XIDARRAY  
  OID of the `xidarray` type.
* CIDARRAY  
  OID of the `cidarray` type.
* OIDVECTORARRAY  
  OID of the `oidvectorarray` type.
* BPCHARARRAY  
  OID of the `bpchararray` type.
* VARCHARARRAY  
  OID of the `varchararray` type.
* INT8ARRAY  
  OID of the `int8array` type.
* POINTARRAY  
  OID of the `pointarray` type.
* LSEGARRAY  
  OID of the `lsegarray` type.
* PATHARRAY  
  OID of the `patharray` type.
* BOXARRAY  
  OID of the `boxarray` type.
* FLOAT4ARRAY  
  OID of the `float4array` type.
* FLOAT8ARRAY  
  OID of the `float8array` type.
* ABSTIMEARRAY  
  OID of the `abstimearray` type.
* RELTIMEARRAY  
  OID of the `reltimearray` type.
* TINTERVALARRAY  
  OID of the `tintervalarray` type.
* POLYGONARRAY  
  OID of the `polygonarray` type.
* ACLITEM  
  OID of the `aclitem` type.
* ACLITEMARRAY  
  OID of the `aclitemarray` type.
* MACADDRARRAY  
  OID of the `macaddrarray` type.
* INETARRAY  
  OID of the `inetarray` type.
* CIDRARRAY  
  OID of the `cidrarray` type.
* CSTRINGARRAY  
  OID of the `cstringarray` type.
* BPCHAR  
  OID of the `bpchar` type.
* VARCHAR  
  OID of the `varchar` type.
* DATE  
  OID of the `date` type.
* TIME  
  OID of the `time` type.
* TIMESTAMP  
  OID of the `timestamp` type.
* TIMESTAMPARRAY  
  OID of the `timestamparray` type.
* DATEARRAY  
  OID of the `datearray` type.
* TIMEARRAY  
  OID of the `timearray` type.
* TIMESTAMPTZ  
  OID of the `timestamptz` type.
* TIMESTAMPTZARRAY  
  OID of the `timestamptzarray` type.
* INTERVAL  
  OID of the `interval` type.
* INTERVALARRAY  
  OID of the `intervalarray` type.
* NUMERICARRAY  
  OID of the `numericarray` type.
* TIMETZ  
  OID of the `timetz` type.
* TIMETZARRAY  
  OID of the `timetzarray` type.
* BIT  
  OID of the `bit` type.
* BITARRAY  
  OID of the `bitarray` type.
* VARBIT  
  OID of the `varbit` type.
* VARBITARRAY  
  OID of the `varbitarray` type.
* NUMERIC  
  OID of the `numeric` type.
* REFCURSOR  
  OID of the `refcursor` type.
* REFCURSORARRAY  
  OID of the `refcursorarray` type.
* REGPROCEDURE  
  OID of the `regprocedure` type.
* REGOPER  
  OID of the `regoper` type.
* REGOPERATOR  
  OID of the `regoperator` type.
* REGCLASS  
  OID of the `regclass` type.
* REGTYPE  
  OID of the `regtype` type.
* REGPROCEDUREARRAY  
  OID of the `regprocedurearray` type.
* REGOPERARRAY  
  OID of the `regoperarray` type.
* REGOPERATORARRAY  
  OID of the `regoperatorarray` type.
* REGCLASSARRAY  
  OID of the `regclassarray` type.
* REGTYPEARRAY  
  OID of the `regtypearray` type.
* UUID  
  OID of the `uuid` type.
* UUIDARRAY  
  OID of the `uuidarray` type.
* TSVECTOR  
  OID of the `tsvector` type.
* GTSVECTOR  
  OID of the `gtsvector` type.
* TSQUERY  
  OID of the `tsquery` type.
* REGCONFIG  
  OID of the `regconfig` type.
* REGDICTIONARY  
  OID of the `regdictionary` type.
* TSVECTORARRAY  
  OID of the `tsvectorarray` type.
* GTSVECTORARRAY  
  OID of the `gtsvectorarray` type.
* TSQUERYARRAY  
  OID of the `tsqueryarray` type.
* REGCONFIGARRAY  
  OID of the `regconfigarray` type.
* REGDICTIONARYARRAY  
  OID of the `regdictionaryarray` type.
* TXID_SNAPSHOT  
  OID of the `txid_snapshot` type.
* TXID_SNAPSHOTARRAY  
  OID of the `txid_snapshotarray` type.
* INT4RANGE  
  OID of the `int4range` type.
* INT4RANGEARRAY  
  OID of the `int4rangearray` type.
* NUMRANGE  
  OID of the `numrange` type.
* NUMRANGEARRAY  
  OID of the `numrangearray` type.
* TSRANGE  
  OID of the `tsrange` type.
* TSRANGEARRAY  
  OID of the `tsrangearray` type.
* TSTZRANGE  
  OID of the `tstzrange` type.
* TSTZRANGEARRAY  
  OID of the `tstzrangearray` type.
* DATERANGE  
  OID of the `daterange` type.
* DATERANGEARRAY  
  OID of the `daterangearray` type.
* INT8RANGE  
  OID of the `int8range` type.
* INT8RANGEARRAY  
  OID of the `int8rangearray` type.
* RECORD  
  OID of the `record` type.
* RECORDARRAY  
  OID of the `recordarray` type.
* CSTRING  
  OID of the `cstring` type.
* ANY  
  OID of the `any` type.
* ANYARRAY  
  OID of the `anyarray` type.
* VOID  
  OID of the `void` type.
* TRIGGER  
  OID of the `trigger` type.
* EVENT_TRIGGER  
  OID of the `event_trigger` type.
* LANGUAGE_HANDLER  
  OID of the `language_handler` type.
* INTERNAL  
  OID of the `internal` type.
* OPAQUE  
  OID of the `opaque` type.
* ANYELEMENT  
  OID of the `anyelement` type.
* ANYNONARRAY  
  OID of the `anynonarray` type.
* ANYENUM  
  OID of the `anyenum` type.
* FDW_HANDLER  
  OID of the `fdw_handler` type.
* ANYRANGE  
  OID of the `anyrange` type.

## Properties:

* public (readonly) pq\Connection $connection  
  The connection which was used to obtain type information.
