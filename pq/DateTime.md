# class pq\DateTime extends DateTime implements JsonSerializable

A simple DateTime wrapper with predefined formats which supports stringification and JSON.

## Formats:

Type | Format
-----|-------
pq\Types::DATE | "Y-m-d"
pq\Types::ABSTIME | "Y-m-d H:i:s"
pq\Types::TIMESTAMP | "Y-m-d H:i:s.u"
pq\Types::TIMESTAMPTZ | "Y-m-d H:i:s.uO"

> ***NOTE:***  
  Date/time values will conly be converted to pq\DateTime and from DateTime if the pq\Result::CONV_DATETIME bit is set in pq\Result::$autoConvert.

## Properties:

* public string $format = "Y-m-d H:i:s.uO"  
  The default format of any date/time type automatically converted by pq\Result (depends on the actual type of the column).



