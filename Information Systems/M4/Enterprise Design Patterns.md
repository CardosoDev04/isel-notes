
Enterprise Design Patterns are methodologies that were formalized during the "boom" in software development enterprises.

These patterns refer to certain techniques and code structure that when applied to a project result in a well-structured and concise solution to a problem.

In the context of this course, we've gone over some of the most common design patterns regarding information systems and it's interaction with applications in general.


## The Model

The model as discussed in [[JPA]] contains the adaptation of the database model to domain objects and classes.

This module usually contains the definition of classes that represent Database tables and include the enforcement of business rules and integrity restrictions.

It essentially contains a "model" of the data that's used in the application.


## The Data Mappers

The data mappers are interfaces when implemented contain functions that are used to create, update and delete data in the DB. These are implemented in the repositories in order to allow for data manipulation.

## The Repositories

The repositories are interfaces that when implemented contain methods to handle all the logic pertaining to creating, deleting, modifying and reading data from the database. Some methods in these interfaces can include findByKey() for example or the implementation of the DataMapper method, create().

It's through instances of these interfaces that we can call in our main application methods to make modifications to the database.

For example, in an application that allows for admins to create users given their name and email, the code could include something like:

```java
private IPersonRepository personRepo = gtx.getPersonRepo();

personRepo.create("name","email");
```


These interfaces are implemented in the context of a [[JPA]] application.


## Unit of Work

Unit of Work isn't a class per se, but rather the grouping certain operations in units that perform tasks.

For example, in the context of [[Entity Management]] a Unit of Work could be a block that represents a transaction and the methods called within it, as it really is just one block of code that performs a task, a *unit* that performs *work*.

## The Context Factory

The context factory, or in as we've used it, the application context, is a class that implements / makes use of all the previous patterns we've discussed earlier.

This class is then instantiated in the main application and allows for the instantiation of repositories and other generic methods that allow the end user to manipulate the database.

Each application has it's context, and each context has different implementations.

It's called a context factory since this refers to a class that generates implementations and instances.







