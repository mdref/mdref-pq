# void pq\Connection::listenAsync(string $channel, callable $listener)

[Asynchronously](pq/Connection/: Asynchronous Usage) start listening on $channel for notifcations.
See pq\Connection::listen().

## Params:

* string $channel  
  The channel to listen on.
* callable $listener as function(string $channel, string $message, int $pid)  
  A callback automatically called whenever a notification on $channel arrives.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
