# bool pq\Connection::flush()

Flush pending writes on the connection.
Call after sending any command or data on a nonblocking connection.

If it returns FALSE, wait for the socket to become read or write-ready.
If it becomes write-ready, call pq\Connection::flush() again.
If it becomes read-ready, call pq\Connection::poll(), then call pq\Connection::flush() again.
Repeat until pq\Connection::flush() returns TRUE.

> ***NOTE:***  
> This method was added in v1.1.0, resp. v2.1.0.

## Params:

None.

## Returns:

* bool, whether everything has been flushed.

## Throws:

* pq\Exception\InvalidArgumentException
* pq\Exception\RuntimeException when no asynchronous operation is active, or flushing failed

## Example:

	<?php
	$c = new pq\Connection();
	$c->nonblocking = true;

	$c->execAsync("SELECT '".str_repeat("a", 6e7)."'", function($r) {
		$r->fetchCol($s);
		var_dump(strlen($s));
	});

	$flushed = $c->flush();
	do {
		while (!$flushed || $c->busy) {
			$r = $c->busy ? [$c->socket] : null;
			$w = !$flushed ?[$c->socket] : null;

			if (stream_select($r, $w, $e, null)) {
				if ($r) {
					printf("P%d", $c->poll());
				}
				if ($w) {
					printf("F%d", $flushed = $c->flush());
				}
			}
		}
		echo "\n";
	} while ($c->getResult());
	?>

### Yields:

	F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0
	... (omitted)
	F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F0F1P3P3P3P3P3P3P3P3
	... (omitted)
	P3P3P3P3P3P3P3P3P3P3P3P3P3P3
	int(60000000)
