# void pq\Connection::notify(string $channel, string $message)

Notify all listeners on $channel with $message.

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
	$conn->notify("queue", "Hello World!");
	
	?>
