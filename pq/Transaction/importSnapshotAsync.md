# void pq\Transaction::importSnapshotAsync(string $snapshot_id)

[Asynchronously](pq/Connection/: Asynchronous Usage) import a snapshot from another transaction to synchronize with.
See pq\Transaction::importSnapshot().

> ***NOTE:***  
  The transaction must have an isolation level of at least pq\Transaction::REPEATABLE_READ.

## Params:

* string $snapshot_id  
  The snapshot identifier obtained by exporting a snapshot from a transaction.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
