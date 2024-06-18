
The explain command is a command used before an SQL query/operation to gather information about the execution of it.


If we add the keyword *explain* to an SQL statement such as:

```sql
explain select * from a;
```

The output will include:
- The execution plan
- The planning time
- The estimated cost
- The estimated execution time

The execution plan will contain, in the above case, the type of scan that will be performed upon execution of the query (Seq Scan, Indexed Scan, Hash Index Scan, Nested Loop... etc...), which varies for example on the presence (or lack thereof) of [[Indexes]] on the columns being scanned. It will also contain any filtering (if needed) that will be used to filter out unnecessary rows, in a query with a where clause, for example.

This command by itself doesn't execute the query, hence the times present in the output are mere estimations.

## Analyze

Analyze is another keyword that we're able to add to the Explain command (after it) in order to gather more information about the query.

Here's how it can be used in PostgreSQL:
```sql
explain analyze select * from a;
```

Contrary to the standalone *explain*, by using explain analyze the query is actually executed and as such, the output will contain the actual execution and planning time along with all rows that were scanned, filtered, skipped...etc...

The total cost in time of the operation can be calculated by adding both the planning and execution time, as this gives us the time from the statement call up until the result is shown.