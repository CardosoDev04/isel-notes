


The Non-repeatable Read problem happens when the [[Isolation Level]] is either Read-Committed or Read-Uncommitted, on the occurrence of the following:

Let's imagine we have two transactions T1 and T2.

If T1 reads a data item X and then after that T2 goes and writes on the same data item, when T1 goes to read it again the value has changed. Making the reading of the data item  with the same end result non-repeatable.

This is prevented by setting the [[Isolation Level]] to Repeatable Read.
