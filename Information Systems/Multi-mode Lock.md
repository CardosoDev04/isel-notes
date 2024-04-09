
Let's say we have a data item X, which is being accessed by two transactions T1,T2. 

If in this access both T1 and T2 are trying to perform a read operation on X, and since read operations by concurrent transactions are non conflicting, they should be able to both read X at concurrently.
This isn't possible with the use of a [[Binary Lock]], for example, since when this lock is acquired no operations by another transaction are possible even non conflicting ones.

Now let's imagine that T1 is trying to perform a write operation on X and T2 is trying to perform a read operation on the same item. This would result in a Read-Write conflict and requires locking to deal with this concurrency. But now, as R/W are conflicting operations on the same data item,
this would require that T1 locks the data item in such a way that T2 cannot read it while it's being written to.

This is where Multi-mode Locking comes into play.

## States

Multi-mode locks are lock objects that possess three locking operations and three states:

- unlock() -> State 0 or unlocked
- read_lock()  -> State 1 or read-locked
- write_lock() -> State 2 or write-locked

## Implementation

Example implementation of a Multi-mode Lock class:

```Kotlin
class MultiModeLock(var state: Int){
init { this.state = 0 }

fun read_lock(){ this.state = 1 }
fun write_lock() { this.state = 2 }
fun unlock() { this.state = 0 }

}
```

Read-locks are also called [[Shared Lock]] and Write-locks are also called [[Exclusive Lock]].

## Conversion of states

Some times, it's desirable to convert the locking state from it's initial acquired state, in order to either restrict or relax the access conditions of the data item it locks.

For example, if T1 has issued a read-lock or [[Shared Lock]] it's possible for it to then **upgrade** the lock by issuing a write-lock or [[Exclusive Lock]] then, later down the transactional process road, **downgrade** it again to a read-lock.

This conversion has rules though, if at the time T1 wishes to upgrade it's read-lock to a write-lock, T2 or any other transaction don't possess a read-lock as well, then T1 can upgrade it's lock. Otherwise, it must wait until the other transactions release their locks.

On another note, T1 can always downgrade it's write-lock to a read-lock since no other wite-locks can be active if T1 has a write-lock on the data item.