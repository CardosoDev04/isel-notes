
Loop using cursor:

```sql
declare abc cursor for select * from table

open abc;

loop
	fetch abc into record_variable;
	exit when not found;
end loop;	
```


For loop without explicit cursor:

```sql
for record in select * from table loop
-- .... --
end loop;
```

