# void pq\Connection::listen(string $channel, callable $listener)

Listen on $channel for notifications.
See pq\Connection::unlisten().

## Params:

* string $channel  
  The channel to listen on.
* callable $listener as function(string $channel, string $message, int $pid)  
  A callback automatically called whenever a notification on $channel arrives.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

## Example:

	<?php
	
	$conn = new pq\Connection;
	$conn->listen("queue", function($channel, $message, $backend_pid) {
		printf("Connection on backend %d said %s\n", $backend_pid, $message);
	});
	
	?>
