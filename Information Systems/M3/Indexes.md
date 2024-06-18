
Indexes are objects used in DBMS to optimize table searches.

There are different kinds of indexes such as:
- B-Tree Indexes
- Hash Indexes

These different types of indexes can be used for the same purpose but generally are used for different situations.

The B-Tree index is the most widely used one, since it works well for equality, range and lookup queries. While the Hash index is most used for look-ups in tables with high column cardinality.

Indexes in PLPGSQL can be created as such:
```sql
create or replace index idx on table(column);
```

This means that an index named "idx" has been created regarding the column "column" of table "table".

The effect of the creation of an index can be seen by analyzing the output of the [[Explain]] command.