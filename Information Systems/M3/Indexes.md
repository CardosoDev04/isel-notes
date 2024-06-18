
Indexes are objects used in DBMS to optimize table searches.

There are different kinds of indexes such as:
- B-Tree Indexes
- Hash Indexes
- Bitmap Indexes
- Partitioned Indexing

These different types of indexes can be used for the same purpose but generally are used for different situations.

The B-Tree index is the most widely used one, since it works well for equality, range and lookup queries when given a small/medium sized data set. 

The Hash index is most used for direct look-ups in tables with high column cardinality.

The Bitmap index is most used for queries with where clauses having multiple conditions in large data sets.

Partitioning is the act of the system dividing a large data set into partitions and assigning indexes to each partition, this is done in order to optimize database lookup.

Indexes in PLPGSQL can be created as such:
```sql
create or replace index idx on table(column);
```

This means that an index named "idx" has been created regarding the column "column" of table "table".

The effect of the creation of an index can be seen by analyzing the output of the [[Explain]] command.