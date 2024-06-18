
## Functions

PLPGSQL functions are methods used to execute business logic / check values / get a return, they are created using the following syntax:

```sql
	create or replace function abc(params)
	returns (data_type) as $$
	declare
		(variables)
	begin
	-- Code --
	end;
	$$ language plpgsql;
```

Functions always have a return value of type (data_type).

Functions can be called inside of SQL transactions and their return assigned to a variable as such:

```sql
begin

declare variable (data_type)

select abc(params) into variable;

commit;
```

As we can see from the example above, functions are called using the "select" instruction followed by the function and it's arguments/parameters.


## Stored Procedures

Stored procedures, while similar to functions, serve a different purpose. They are, as the name implies, procedures that are stored in a simple name and can be called to be executed.

Let's take for example this simple, no-return stored procedure:

```sql
create or replace procedure abc(params)
as $$
begin

insert into table(val1,val2,val3) values (1,2,3)

end;
$$
```

This procedure makes an insert of 3 values into a table and doesn't return any value. This is the main difference between ***Stored Procedures*** and ***Functions***, while functions need to have a return value, procedures don't.

To call a procedure we use the following syntax:

```sql
begin

call abc(params);

commit;
```
