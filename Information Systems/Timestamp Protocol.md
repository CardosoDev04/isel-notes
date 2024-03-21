
The Timestamp Ordering Protocol makes use of timestamps (TS) to order the execution of transactions and prevents [[Deadlock]].



### But what is a timestamp?

A timestamp is a unique identifier in the DBMS that identifies the start of a certain transaction. Think of it like the transaction is being identified by the time it starts executing.

Timestamps are denoted by TS(T), with T being the transaction, and are usually integer numbers 1,2,3... and so on.



## Timestamp Ordering Algorithm

To understand the timestamp ordering algorithm we must first divide the operations in a transaction and the transactions themselves into different timestamps categories:

- Transaction timestamp - TS(T)
- Data item read timestamp - read_TS(X)
- Data item write timestamp - write_TS(X)


### Basic timestamp ordering

Let's imagine we have transaction T and a data item X.

Initially we have:

TS(T) = 1       read_TS(X) = 0 && write_TS(X) = 0


Whenever T tries to perform a write_item(X) operation the following is checked:
- If read_TS(X) > TS(T) or write_TS(X) > TS(T) , T will abort and rollback
- If the mentioned conditions are not met, T will execute the write_item(X) and write_TS(X) will be set to TS(T)'s current value

Whenever T tries to perform a read_item(X):
- If write_TS(X) > TS(T) then abort and rollback
- Otherwise, if write_TS(X) <= TS(T), execute the read_item(X) and set the read_TS(X) to the larger number between it's current value or TS(T).






## Thomas's Write Rule

This is a modification of the Basic TO algorithm that rejects fewer operations by modifying the check conditions for write_item(X) as follows:

- If read_TS(X) > TS(T), then it aborts and roll's back
- If write_TS(X) > TS(T), then it does not perform the write operation but continues processing.
If neither conditions are met, it performs the write operation and sets write_TS(X) to TS(T).
