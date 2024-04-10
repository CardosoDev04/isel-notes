
A schedule is recoverable if in case of a transaction failure the system can be brought back to a consistent state. This follows the C and D property in [[ACID]] as in Consistency and Durability because all changes made in a recoverable schedule persist consistently in the database since there's no rollback of committed data.

Types of Recoverable schedules include [[Cascading and Cascadeless Schedule]] and [[Strict Schedule]].
