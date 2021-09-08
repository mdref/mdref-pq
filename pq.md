# pecl/pq

## About:

This is a modern binding to the mature [libpq](http://www.postgresql.org/docs/current/static/libpq.html), the official PostgreSQL C-client library.

### Highlights:

* Nearly 100% support for [asynchronous usage](pq/Connection/:%20Asynchronous%20Usage).
* Extended [type support by pg_type](pq/Types/:%20Overview).
* Fetching simple [multi-dimensional array maps](pq/Result/map).
* Working [Gateway implementation](https://bitbucket.org/m6w6/pq-gateway).

## Installation:

This extension is hosted at [PECL](http://pecl.php.net) and can be installed with [PEAR](http://pear.php.net)'s pecl command:

	# pecl install pq

### PHARext

Watch out for [PECL replicates](https://replicator.pharext.org?pq)
and pharext packages attached to [releases](https://github.com/m6w6/ext-pq/releases).

### Checkout

	git clone github.com:m6w6/ext-pq
	cd ext-pq
	/path/to/phpize
	./configure --with-php-config=/path/to/php-config
	make
	sudo make install

## Dependencies:

This extension unconditionally depends on the pre-loaded presence of the following PHP extensions:

* raphf
* spl

It optionally depends on the following extensions:

* json
