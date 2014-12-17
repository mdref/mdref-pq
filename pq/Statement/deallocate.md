# void pq\Statement::deallocate()

Free the server resources used by the prepared statement, so it can no longer be executed.
This is done implicitly when the object is destroyed.

## Params:

None.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException

## Example:

        <?php

        $connection = new pq\Connection;
        $types = new pq\Types($connection);
        $statement = $connection->prepare("st1",
                "SELECT \$1, \$2", [pq\Types::XML, pq\Types::JSON]);

        // some code which executes the statement

        $statement->deallocate();

        ?>

