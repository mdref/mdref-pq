# pq\Connection: General Usage

What is needed to create, check and reset a connection.

## Creating a connection:

Creating a connection to the PostgreSQL server is as simple as:

	<?php

	$connection = new pq\Connection("dbname=test user=test password=test");

	?>

The first argument to the Connection constructor is a ***connection string*** as described [in the PostgreSQL documentation](http://www.postgresql.org/docs/current/static/libpq-connect.html#LIBPQ-CONNSTRING).

Optional ***flags*** are accepted as second argument. See [connection flag constants](pq/Connection#Connection.Flags:).

### Creating a persistent connection:

	<?php

	$connection = new pq\Connection("dbname=test user=test password=test", pq\Connection::PERSISTENT);

	?>

### Creating an asynchronously opened connection:

	<?php

	$connection = new pq\Connection("dbname=test user=test password=test", pq\Connection::ASYNC);

	?>

## Checking the connection status:

The connection object provides a ***public readonly*** property pq\Connection::$status, which value can be one of the [connection status constants](pq/Connection#Connection.Status:).

	<?php

	switch ($connection->status) {
	case pq\Connection::OK:
	  // connection complete
	  break;
	case pq\Connection::BAD:
	  $connection->reset();
	  break;
	default:
	  // connection in progress
	  break;
	}

	?>

## Resetting the connection:

	<?php

	$connection->reset();

	?>

Attempt to close the connection to the server and reestablish a new connection with the same connection parameters previously used.

## Closing the connection:

	<?php

	$connection = NULL;

	?>

### Non-persistent connections:

A ***non-persistent*** connection will be closed when all references to the pq\Connection object are gone.

### Persistent connections:

A ***persistent*** connection will be recycled, when it is not referenced any longer.

There is also some cleanup performed, so that subsequent usage is as unimpaired as possible:

* any active asynchronous queries are canceled
* any pending results of asynchronous queries are fetched and cleared
* ```ROLLBACK``` if pq\Connection::$transactionStatus is anything but pq\Connection::TRANS_IDLE
* ```RESET ALL``` to reset any changed session variables
* ```UNLISTEN``` for each listened notification channel
