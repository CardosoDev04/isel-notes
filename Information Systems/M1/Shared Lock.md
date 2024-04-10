

The shared lock or read-lock denoted by Lock-s(X) with X being the data item it locks, is a state of a [[Multi-mode Lock]].

Let's imagine we have a data item X and two transactions, T1 and T2.

If the Shared Lock is acquired for data item X by T1, this means that T2 will be able to perform read operations on X without the lock being released by T1. This is because R/R operations between two concurrent transactions are non conflicting so it makes sense that T2 can read data item X if T1 is only reading it as well.

Now, this lock doesn't allow for T2 to write on X while the lock is present meaning only R/R operations are possible. This is because R/W operations between two concurrent transactions are conflicting and it wouldn't make sense to allow T2 to write as this would make the locking mechanism useless.

In summary, when a transaction T1 acquires a Shared Lock on a data item X, it allows other concurrent transactions to perform read-only operations on X for the duration of the lock.
