
ACID is an acronym in DBMS pertaining to transactions which means:

A - Atomicity, meaning a transaction is seen as an individual undividable unit, either all operations on the transaction succeed or none do.

C - Consistency, meaning all transactions must move the database from one [[Consistent State]] to another. Enforcing all DB restrictions imposed by defined rules.

I - Isolation, meaning all concurrent transactions do not interfere with each other. The execution of a transaction should not modify the outcome of another concurrent transaction.

D - Durability, meaning that if a transaction commits, all changes made by it are persistent even in case of a system fault, crash or error.

These properties when violated create what are called [[Anomalies]].