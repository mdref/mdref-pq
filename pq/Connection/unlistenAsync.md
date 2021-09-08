# void pq\Connection::unlistenAsync(string $channel)

[Asynchronously](pq/Connection/:%20Asynchronous%20Usage) stop listening for notifications on channel $channel.
See pq\Connection::unlisten() and pq\Connection::listenAsync().

## Params:

* string $channel  
  The name of a channel which is currently listened on.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

