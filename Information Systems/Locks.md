

In a DBMS, pertaining to the matter of concurrency, locks are objects/variables associated with each data item used to synchronize access to said items.
Each lock has information about the status of the data item it locks, in respect to the possible operations that can be performed on said item by other transactions trying to access it concurrently.

They have two methods associated with them:

- lock():
  ->  This method, when called internally, locks the access to it's lock's associated data item so that only the transaction which called the method can access it.
  
- unlock():
  -> This method, when called internally, unlocks access to it's lock's data item so that other transactions can access it, either that be reading or writing it.


There are two kinds of locks we talked about in SI:
- [[Binary Lock]] 
- [[Multi-mode Lock]]


The use of these doesn't directly guarantee [[Serializability]] and so there are other protocols involving the locking mechanisms discussed that ensure that a schedule is serializable such as the [[2PL Protocol]].

Other concurrency control protocols include the [[Timestamp Protocol]].
