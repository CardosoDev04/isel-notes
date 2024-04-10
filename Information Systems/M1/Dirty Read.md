

The dirty read problem happens on the occurrence of a R/W conflict between two concurrent transactions specifically when the [[Isolation Level]] is set to Read-Uncommitted.

Let's imagine we have concurrent transactions T1, T2 :

If T1 writes on a data item X and then before this write being committed T2 reads data item X., since this is possible on the Read-Uncommitted isolation level.

What will happen is that the value T2 is reading is not the real value of X since T1 hasn't committed, meaning that if T1 is to rollback it's changes and the value of X rolls back to it's old_value or BFIM , T2 is now operating on a "fake" value.