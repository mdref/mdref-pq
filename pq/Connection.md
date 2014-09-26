# class pq\Connection

The connection to the PostgreSQL server.

See the [General Usage](pq/Connection/: General Usage) page for an introduction on how to use this class.

## Constants:
### Connection Flags:
* PERSISTENT  
(Re-)open a persistent connection.
* ASYNC  
If the connection is not already open, perform the connection attempt [asynchronously](pq/Connection/: Asynchronous Usage).

### Connection Status:
* OK  
Everything well; if a connection has been newly and synchronously created, the connection will always have this status right after creation.
* BAD  
Broken connection; consider pq\Connection::reset() or recreation.
* STARTED  
Waiting for connection to be made.
* MADE  
Connection okay; waiting to send.
* AWAITING_RESPONSE  
Waiting for a response from the server.
* AUTH_OK  
Received authentication; waiting for backend start-up to finish.
* SSL_STARTUP  
Negotiating SSL encryption.
* SETENV  
Negotiating environment-driven parameter settings.

### Transaction Status:
* TRANS_IDLE  
  No active transaction.
* TRANS_ACTIVE  
  A transaction command is in progress.
* TRANS_INTRANS  
  Idling in a valid transcation block.
* TRANS_INERROR  
  Idling in a failed transaction block.
* TRANS_UNKNOWN  
  Bad connection.

### Polling Status:
* POLLING_FAILED  
  The connection procedure has failed.
* POLLING_READING  
  Select for read-readiness.
* POLLING_WRITING  
  Select for write-readiness.
* POLLING_OK  
  The connection has been successfully made.

### Event Listener Types:
* EVENT_NOTICE  
  Register the event handler for notices.
* EVENT_RESULT  
  Register the event handler for any created results.
* EVENT_RESET  
  Register the event handler for connection resets.


## Properties:
* public (readonly) int $status  
  A [connection status constant](pq/Connection#Connection.Status:) value.
* public (readonly) int $transactionStatus  
  A [transaction status constant](pq/Connection#Transaction.Status:) value.
* public (readonly) resource $socket  
  The server socket resource.
* public (readonly) bool $busy  
  Whether the connection is busy with [asynchronous operations](pq/Connection/: Asynchronous Usage).
* public (readonly) string $errorMessage  
  Any error message on failure.
* public (readonly) array $eventHandlers  
  List of registered event handlers.
* public string $encoding = NULL  
  Connection character set.
* public bool $unbuffered = FALSE  
  Whether to fetch [asynchronous](pq/Connection/: Asynchronous Usage) results in unbuffered mode, i.e. each row generates a distinct pq\Result.

### Connection Information:
* public (readonly) string $db  
  The database name of the connection.
* public (readonly) string $user  
  The user name of the connection.
* public (readonly) string $pass  
  The password of the connection.
* public (readonly) string $host  
  The server host name of the connection.
* public (readonly) string $port  
  The port of the connection.
* public (readonly) string $options  
  The command-line options passed in the connection request.

### Inheritable Defaults:
* public int $defaultFetchType = pq\Result::FETCH_ARRAY  
  Default fetch type for future pq\Result instances.
* public int $defaultAutoConvert = pq\Result::CONV_ALL  
  Default conversion bitmask for future pq\Result instances.
* public int $defaultTransactionIsolation = pq\Transaction::READ_COMMITTED  
  Default transaction isolation level for future pq\Transaction instances.
* public bool $defaultTransactionReadonly = FALSE  
  Default transaction readonlyness for futire pq\Transaction instances.
* public bool $defaultTransactionDeferrable = FALSE  
  Default transaction deferrability for future pq\Transaction instances.
  
