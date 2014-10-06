# bool pq\COPY::get(string &$data)

Receive data from the server during pq\Result::COPY_OUT state.

## Params:

* string &$data  
  Data read from the server.

## Returns:

* bool, success.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
