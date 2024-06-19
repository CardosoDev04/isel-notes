
A view is a virtual table that acts as a "view window" into the actual table it references without storing data, and executes a predefined query when it's interacted with. (e.g. SELECT).

Views by default are not updatable.

An updatable view, is a special kind of view that allows modification as if the user is interacting with the actual underlying table. Updatable views cannot be the result of complex operations such as joins or aggregations.


A materialized view is hybrid between a view and a table, it allows for storage of results from a query o the "base table" while maintaining access to it for updates. It's used for performance improvement since we can offload the results of a query on a given table to a materialized view.

These views have a problem, which is the storage overhead since they effectively duplicate the data that's offloaded to them to their own storage.


In general, normal views should be used for presenting filtered or aggregated data, materialized views should be used to optimized queries that are done often and are complex. And updatable views should be used (cautiously) to present changing data that is the result of a simple query.