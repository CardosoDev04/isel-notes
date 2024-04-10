

The isolation level utilises [[Exclusive Lock]]'s in order to guarantee that data items read by one transaction cannot be modified until the transaction releases the lock. Making it so that another transaction cannot change the value before the first transaction reads it again, making the reading operations repeatable.

This isolation level prevents both [[Dirty Read]] and [[Non-repeatable Read]] but does not prevent [[Phantoms]].