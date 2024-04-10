
Flow control is a mechanism used in most programming languages, and as the name suggests controls the "flow" or execution of a program based on certain conditions.

This is usually translated into if/then/else statements like the following:

```SQL
IF salario > 10000 THEN
BEGIN
    UPDATE funcionarios SET bonus = 10;
END;
END IF;
```


The example above is an example of a simple if/then statement.

What happens is that conditional flow control can also have cases where the first condition doesn't verify itself but we don't want to end the execution there and can perhaps have a second condition to check or a default case in case of a first condition not being verified.

For these cases we use the else / else if statements.

```SQL
IF salario > 10000 THEN
	UPDATE funcionarios SET bonus = 10;
ELSE IF salario > 5000 THEN
	UPDATE funcionarios SET bonus = 5;	
ELSE
	UPDATE funcionarios SET bonus = 2;
END IF;
```

The flow control ends on the END IF clause and this clause if mandatory for it to work as it delimits the block.