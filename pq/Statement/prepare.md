# void pq\Statement::prepare()

Re-prepare a statement that has been deallocated. This is a no-op on already open statements.

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
        $statement->prepare();

        ?>

