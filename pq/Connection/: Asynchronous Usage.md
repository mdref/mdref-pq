# pq\Connection: Asynchronous Usage

Whenever you start an asynchronous operation, you will have to probe pq\Connection::poll() to determine the current status of the operation.

You can then use the ***public readonly*** property pq\Connection::$socket with ```stream_select()``` to wait for read/write-readiness.

> ***NOTE:***
You cannot use the connection for anything else while an asynchronous operation is active.

## Connect or reset asynchronously:

First, you can establish or reset a connection asynchronously.

### Start asynchronous connect:

	<?php
	
	$c = new pq\Connection(null, pq\Connection::ASYNC);
	
	?>

### Start asynchronous reset:

	<?php

	$c->resetAsync();

	?>

### Complete asynchronous operation:

Keep in mind that you have to test for write-readiness once *before* starting the polling loop on connect/reset.

	<?php
	
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


If you use an appropriate timeout in the ```stream_select()``` call and do something else at the end of the while loop, you probably got the idea...

## Execute queries asynchronously:

	<?php

	$c = new pq\Connection;
	$c->execAsync("SELECT 1+2+3; SELECT 2,3,4", function ($res) {
	  var_dump($res);
	});

	?>

The body of the while loop looks slightly different, when executing queries asynchronously, because you only have to wait for read-readiness.

You can use the ***public readonly*** property pq\Connection::$busy to test if a call to pq\Connection::getResult() would block, and if so wait for read-readiness and then call pq\Connection::poll().

	<?php

	do {
	  while ($c->busy) {
		$r = array($c->socket);
		$w = $e = null;
		if (stream_select($r, $w, $e, null)) {
		  $c->poll();
		}
	  }
	} while ($c->getResult());

	?>

If pq\Connection::getResult() returns NULL, there's nothing more in the pipeline.
