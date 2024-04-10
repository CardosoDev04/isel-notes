
The phantoms problem happens in concurrent transaction execution on all [[Isolation Level]] except for the Serializable level.

This problem occurs when the following happens:

Let's imagine we have transactions T1 and T2.

T1 begins by reading a row on a table, perhaps by using an SQL WHERE clause to search for data based on a User's age for example.

T2, somewhere along it's execution history that's concurrent with T1, inserts a new user with the same age T1 is looking for.

When T1 performs a second search on the table, it will find data that previously wasn't there since T2 added it after the first read.

This new data is called a Phantom.
