NodeJS Logging
==

The biggest players are

http://www.timqian.com/star-history/#trentm/node-bunyan&winstonjs/winston

I've yet to use bunyan but with winston I've personally encountered these issues.

* https://github.com/winstonjs/winston/issues/418 - handleExceptions on a file transport should not kill the console print out
* https://github.com/winstonjs/winston/issues/397 - File transport maxsize and maxFiles cause inconsistent state on restart
* https://github.com/winstonjs/winston/issues/280 - Error objects are discarded during logging
* https://github.com/winstonjs/winston/issues/871 - Error objects inside object or array are discarded during logging

I would recommend not to use winston for logging in nodejs.
