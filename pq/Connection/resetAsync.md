# void pq\Connection::resetAsync()

[Asynchronously](pq/Connection/: Asynchronous Usage) reset a possibly broken connection to a working state.

## Params:

None.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException


## Example:

	<?php

	$c->resetAsync();

	// wait until the stream becomes writable
	$w = array($c->socket);
	$r = $e = null;
	
	if (stream_select($r, $w, $e, null)) {
	
	  // loop until the connection is established
	  while (true) {
	  
		switch ($c->poll()) {
		
		case pq\Connection::POLLING_READING:
		  // we should wait for the stream to be read-ready
		  $r = array($c->socket);
		  stream_select($r, $w, $e, NULL);
		  break;

		case pq\Connection::POLLING_WRITING:
		  // we should wait for the stream to be write-ready
		  $w = array($c->socket);
		  $r = $e = null;
		  stream_select($r, $w, $e, null);
		  break;

		case pq\Connection::POLLING_FAILED:
		  printf("Connection failed: %s\n", $c->errorMessage);
		  break 2;

		case pq\Connection::POLLING_OK:
		  printf("Connection completed\n");
		  break 2;
		}
	}
	
	?>

