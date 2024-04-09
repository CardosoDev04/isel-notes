

A schedule is said to be cascadeless if all transactions in it which read only data items written by already committed transactions. 

On the contrary, a schedule is said to be cascading if transactions are able to read data items written by other transactions without the latter being committed ***BUT*** all transactions that read data items written by other transactions can only commit after the writing transaction commits or rolls back. This means that if T2 (writing transaction) rolls back it will make T1(reading transaction) roll back as well, making it a cascade rollback.



An example of a cascadeless and recoverable schedule:

S1 with T1,T2

S1 : <w2(x) c2 r1(x) c1>

Here, T1 only reads data item X written by T2 when the latter has committed it's changes.

An example of a cascading and recoverable schedule:

S2 with T1,T2

S2 : <w2(x) r1(x) c2 c1>

