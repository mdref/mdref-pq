# void pq\Transaction::unlinkLOB(int $oid)

Unlink a *large object*.
See pq\Transaction::createLOB().

## Params:

* int $oid  
  The OID of the *large object*.

## Returns:

* pq\LOB, instance of the opened *large object*.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
