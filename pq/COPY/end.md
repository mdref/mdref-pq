# void pq\COPY::end([string $error = NULL])

End the COPY operation to the server during pq\Result::COPY_IN state.

## Params:

* Optional string $error = NULL  
  If set, the COPY operation will abort with provided message.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
