

The read-uncommitted isolation level is the lowest isolation level and some SQL languages will not even allow for it to happen, even if the user tries to use it by setting the isolation level manually. One of these languages is the one we use in this course, PostgreSQL.


It allows for transactions to read data modified (written on) by other concurrent transactions without the latter being committed.

This leads to many problems and anomalies such as [[Dirty Read]], [[Non-repeatable Read]] and [[Phantoms]].