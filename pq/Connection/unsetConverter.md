# void pq\Connection::unsetConverter(pq\ConverterInterface $converter)

Stop applying a data type converter.

## Params:

* pq\ConverterInterface $converter  
  A converter previously set with pq\Connection::setConverter().

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
