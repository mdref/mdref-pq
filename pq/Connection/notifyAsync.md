# void pq\Connection::notifyAsync(string $channel, string $message)

[Asynchronously](pq/Connection/: Asynchronous Usage) start notifying all listeners on $channel with $message.

## Params:

* string $channel  
  The channel to notify.
* string $message  
  The message to send.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

## Example:

	<?php
	
	$conn = new pq\Connection;
	$conn->notifyAsync("queue", "Hello World!");
	
	?>
