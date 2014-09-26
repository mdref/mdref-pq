# void pq\Transaction::exportLOB(int $oid, string $path)

Export a *large object* to a local file.
See pq\Transaction::importLOB().

## Params:

* int $oid  
  The OID of the *large object*.
* string $path  
  The path of a local file to export to.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
