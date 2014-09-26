# class pq\LOB

A *large object*.

> ***NOTE:***  
  Working with *large objects* requires an active transaction.

## Constants:

* INVALID_OID  
  0, representing an invalid OID.
* <span class="constant">R</span>  
  Read-only mode.
* <span class="constant">W</span>  
  Write-only mode.
* RW  
  Read/write mode.

## Properties:

* public (readonly) pq\Transaction $transaction  
  The transaction wrapping the operations on the *large object*.
* public (readonly) int $oid  
  The OID of the *large object*.
* public (readonly) resource $stream  
  The stream connected to the *large object*.
