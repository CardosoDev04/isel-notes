

The 2PL Protocol or Two Phase Locking Protocol is a locking protocol that involves two phases of lock manipulation, as the name suggests.

A transaction is said to follow this protocol if all locking operations such as state changing of a [[Multi-mode Lock]] are done before the first unlock operation.


## Phase 1 - Growing

The Growing phase starts once the first lock is acquired by the transaction.

In this phase, a transaction can acquire it's locks such as the afro mentioned read-lock or write-lock and it must do so in this phase for all locks it will acquire.

If the conversion of locks is allowed, the upgrading of a lock should be done in this phase.

In phase one, there's no releasing of locks and if there is then the transaction is not following the 2PL protocol.


## Phase 2  - Shrinking

The Shrinking phase starts once a lock acquired in phase one is released (or when the first unlock operation is performed on a lock acquired in phase one).

In this phase, no locks can be acquired but existing locks can be released.

If the conversion of locks is allowed, the downgrading of a lock should be done in this phase.



# Drawing of a 2PL


![[Pasted image 20240321113131.png]]

Figure 1. - Basic [[2PL Diagram]]



# Types of 2PL Protocols


There are actually 4 variations of the 2PL protocol, with these being:
- Basic
- Conservative
- Strict
- Rigorous

The variation we've been discussing is the Basic 2PL Protocol. Let's discuss the other ones and see the differences between them.

### Conservative 2PL

This variation demands that the transactions declares all the locks it will be using for the different data items before the transaction begins. 

This is done by predeclaring a read-set and write-set, since the transaction declares a set of items it will read and a set of items it will write to.
If any of the items the transaction wishes to lock cannot be locked at the time it declares it's read/write sets, for example if the data item that needs to be locked is already locked by another transaction, the first transaction in turn will simply not lock any of the items and wait until all items can be locked.

This variation of the 2PL is [[Deadlock]] free yet impractical to use due to the need of predeclaring all locks and write/read sets.


### Strict 2PL

This is the most popular 2PL variation and it guarantees strict schedules.

This variation makes it so that the transaction that follows it doesn't release any of it's write-locks until it has been committed or aborted, hence no other transaction can read or write any of the data items that have been write-locked by it until it has finished it's execution and committed the results or aborted in the process.

This variation of the 2PL is not [[Deadlock]] free.

### Rigorous

The rigorous 2PL is essentially the same as the Strict 2PL but it also does not release any of it's read-locks until after it's committed or aborted.