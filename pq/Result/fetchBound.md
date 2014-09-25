# array pq\Result::fetchBound()

Iteratively fetch a row into bound variables.
See pq\Result::bind().

## Params:

None.

## Returns:

* array, the fetched row as numerically indexed array.
* NULL, when iteration ends.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\BadMethodCallException
* pq\Exception\RuntimeException
