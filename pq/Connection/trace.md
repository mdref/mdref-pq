# bool pq\Connection::trace([resource $stream])

Trace protocol communication with the server.

> ***NOTE:***  
  Calling pq\Connection::trace() without parameter or NULL stops tracing.

## Params:

* Optional resource $stream = NULL  
  The resource to which the protocol trace will be output.  
  (The stream must be castable to STDIO).

## Returns:

* bool, success.

## Throws:

* pq\Exception\BadMethodCallException
