# class pq\Transaction

A database transaction.

> ***NOTE:***  
  Transactional properties like pq\Transaction::$isolation, pq\Transaction::$readonly and pq\Transaction::$deferrable can be changed after the transaction begun and the first query has been executed. Doing this will lead to appropriate `SET TRANSACTION` queries.

## Constants:

* READ_COMMITTED  
  Transaction isolation level where only rows committed before the transaction began can be seen.
* REPEATABLE_READ  
  Transaction isolation level where only rows committed before the first query was executed in this transaction.
* SERIALIZABLE  
  Transaction isolation level that guarantees serializable repeatability which might lead to serialization_failure on high concurrency.

## Properties:

* public (readonly) pq\Connection $connection  
  The connection the transaction was started on.
* public int $isolation = pq\Transaction::READ_COMMITTED  
  The transaction isolation level.
* public bool $readonly = FALSE  
  Whether this transaction performs read only queries.
* public bool $deferrable = FALSE  
  Whether the transaction is deferrable. See pq\Connection::startTransaction().

