# class pq\Result implements Traversable, Countable

A query result.

See [Fetching Results](pq/Result: Fetching Results) for a general overview.

## Constants:

### Status values:

* EMPTY_QUERY  
  The query sent to the server was empty.
* COMMAND_OK  
  The query did not generate a result set and completed successfully.
* TUPLES_OK  
  The query successfully generated a result set.
* SINGLE_TUPLE  
  The result contains a single row of the result set when using pq\Connection::$unbuffered.
* COPY_OUT  
  COPY data can be recevied from the server.
* COPY_IN  
  COPY data can be sent to the server.
* BAD_RESPONSE  
  The server sent a bad response.
* NONFATAL_ERROR  
  A nonfatal error (notice or warning) occurred.
* FATAL_ERROR  
  A fatal error occurred.


### Fetch types:

* FETCH_ARRAY  
  Fetch rows numerically indexed, where the index start with 0.
* FETCH_ASSOC  
  Fetch rows associatively indexed by column name.
* FETCH_OBJECT  
  Fetch rows as stdClass instance, where the column names are the property names.

### Conversion bits:

* CONV_BOOL  
  Automatically convert 'f' and 't' to FALSE and TRUE and vice versa.
* CONV_INT  
  Automatically convert integral strings to either int if it fits into maximum integer size and vice versa.
* CONV_FLOAT  
  Automatically convert floating point numbers.
* CONV_SCALAR  
  Do all scalar conversions listed above.
* CONV_ARRAY  
  Automatically convert arrays.
* CONV_DATETIME  
  Automatically convert date strings to pq\DateTime and vice versa.
* CONV_JSON  
  Automatically convert JSON.
* CONV_ALL  
  Do all of the above.


## Properties:

* public (readonly) int $status  
  A [status constant](pq/Result#Status.values:).
* public (readonly) string $statusMessage  
  The accompanying status messsage.
* public (readonly) string $errorMessage  
  Any error message if $status indicates an error.
* public (readonly) int $numRows  
  The number of rows in the result set.
* public (readonly) int $numCols  
  The number of fields in a single tuple of the result set.
* public (readonly) int $affectedRows  
  The number of rows affected by a statement.
* public int $fetchType = pq\Result::FETCH_ARRAY  
  The [type of return value](pq/Result#Fetch.types:) the fetch methods should return when no fetch type argument was given. Defaults to pq\Connection::$defaultFetchType.
* public int $autoConvert = pq\Result::CONV_ALL  
  What [type of conversions](pq\Result#Conversion.bits:) to perform automatically.
