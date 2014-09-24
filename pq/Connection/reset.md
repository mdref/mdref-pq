# void pq\Connection::reset()

Attempt to reset a possibly broken connection to a working state.

## Params:

None.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException


## Example:

    <?php
    
    if ($connection->status != pq\Connection::OK) {
        $connection->reset();
    }
    
    ?>
