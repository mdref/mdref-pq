# void pq\Connection::unlisten(string $channel)

Stop listening for notifications on channel $channel.
See pq\Connection::listen().

## Params:

* string $channel  
  The name of a channel which is currently listened on.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException


## Example:

	<?php
	
	$conn = new pq\Connection;
	$conn->listen("foo", function($channel, $message, $backend_pid) {
		printf("Got message '%s' on channel '%s' from backend %d\n", 
			$message, $channel, $backend_pid);
	});
	
	$conn->notify("foo", "bar");
	$conn->unlisten("foo");
	
	?>
