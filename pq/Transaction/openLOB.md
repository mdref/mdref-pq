# pq\LOB pq\Transaction::openLOB(int $oid[, int $mode = pq\LOB::RW])

Open a *large object*.
See pq\Transaction::createLOB().

## Params:

* int $oid  
  The OID of the *large object*.
* Optional int $mode = pq\LOB::RW  
  Operational mode; read, write or both.

## Returns:

* pq\LOB, instance of the opened *large object*.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
