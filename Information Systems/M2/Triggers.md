
Triggers are type of special function (see [[Functions vs Stored Procedures]]) that is automatically executed once a specific operation is performed on the table they're associated to.

These can be used to ensure data integrity, keep views updated, among other things.


Here is an example declaration of a function that returns a trigger:

 ```sql
 create function example_trigger_fun() returns trigger as $$
	begin
		insert into a(value1) values(1);
	end;
	$$ language plpgsql;
 ```

Here is an example of how this trigger can be applied to a table:

```sql
create trigger trig after insert on abc
for each row execute procedure example_trigger_fun();
```


