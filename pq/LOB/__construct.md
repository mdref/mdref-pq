# void pq\LOB::__construct(pq\Transaction $txn[, int $oid = pq\LOB::INVALID_OID[, int $mode = pq\LOB::RW]])

Open or create a *large object*.
See pq\Transcation::openLOB() and pq\Transaction::createLOB().

## Params:

* pq\Transaction $txn  
  The transaction which wraps the *large object* operations.
* Optional int $oid = pq\LOB::INVALID_OID  
  The OID of the existing *large object* to open.
* Optional int $mode = pq\LOB::RW  
  Access mode (read, write or read/write).

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
