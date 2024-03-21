

Deadlock is a phenomenon that occurs in concurrent data access and occurs when each transaction T in a set of transactions (two or more) is waiting to access some item that has been locked by a transaction T' of the set.

The problem is, if T' is also waiting to access a data item locked by T' and does not proceed before it does, both of them will be waiting forever since none of them will release the lock on the data item each of them want's to access.


## Deadlock Prevention

A way to prevent deadlocking is to use a deadlock free protocol like the Conservative [[2PL Protocol]] which requires all locking to occur before the transactions begin so that if one of the items cannot be obtained, none of them are locked.

A second protocol, which also limits concurrency, involves ordering all the items in the database and making sure that a transaction that needs several items will lock them according to that order. This requires that the programmer (or the system) is aware of the chosen order of the items, which is also not practical in the database context.

A practical example of these protocols that prevent deadlocking is the [[Timestamp Protocol]]. 