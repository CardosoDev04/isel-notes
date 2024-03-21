

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

Figure 1. - [[2PL Diagram]]

