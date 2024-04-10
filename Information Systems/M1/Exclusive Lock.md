

The exclusive lock or write-lock denoted by Lock-x(X), with X being the data item it locks, is a state of a [[Multi-mode Lock]].

Let's imagine we have a data item X and two transactions, T1 and T2.

If T1 is performing a write operation on X, there shouldn't be any read or write operations being performed by T2 for the duration of the operation performed by T1. This is because both W/W and R/W operations between two concurrent transactions are, in fact, conflicting.

This is where the Exclusive Lock comes into play.

When acquired by T1, for example, for the duration of it's locking of X (until it's released) only T1 can perform both read and write operations in X. This lock is acquired when a write operation is performed by T1 and makes it so that T2 can only access it when T1 is done writing on it.
