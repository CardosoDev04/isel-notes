

The Read-committed isolation level, contrary to the [[Read-uncommitted]] isolation level makes it so that transactions can only read data modified (written on) by other transactions once those modifications have been committed. Even so, there are no locks acquired for reading operations.

This isolation level still has problems and provokes the occurrence of anomalies like [[Non-repeatable Read]] and [[Phantoms]], though it does prevent the [[Dirty Read]] anomaly.
