

The Binary Lock (lock) is the most restrictive kind of lock since, as the name ensues, provides only two states of access to the data item it locks:

- Locked (No access)
- Unlocked (Full access)

## States

These states can be interpreted as 0 and 1, with 0 being unlocked and 1 being locked.


## Implementation

Example implementation of a Binary Lock class in Kotlin:

```Kotlin

class BinaryLock(var state: Int) {
	init{ state = 0 }
	fun lock() { this.state = 1 }
	fun unlock() { this.state = 0 }
}
```

Binary locks are the simplest locks available in DBMS but also the more restrictive as mentioned earlier since that , locks of this nature can only be in those two states, either completely locked of completely unlocked.

On the contrary, there are other types of locks which allow for a less restrictive access of data items such as [[Shared Lock]] or [[Exclusive Lock]]