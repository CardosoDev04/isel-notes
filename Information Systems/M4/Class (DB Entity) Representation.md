
In the context of [[JPA]], it's possible to create domain classes that represent, and make us able to manipulate, database entities. This is done through following certain conventions.


Let's imagine for example we have an entity in our database which' table is defined in SQL as such:

```sql
create table entity(
a serial primary key,
b int not null,
c varchar(255) unique
)
```

Now, the way we represent this entity through a domain class requires us to use JPA annotations.

For example, in this case it would be something like this:

```java
@Entity
public class Entity {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private long a;
	@Column(nullable=false)
	private int b;
	@UniqueConstraint(columnNames = {"c"})
	private String c;
}
```

## @Entity annotation

We start by annotating the class with *@Entity* , this annotation tells JPA that this class represents a database entity (table) with the same name. While not mandatory, the fact that the entity in this case needs to have the same name as the table in the DB, is a JPA convention. 

It's not mandatory because we can explicitly tell JPA to map this entity to a certain table using the *@Table* annotation and specifying the table name. This second way of mapping is not so common and by convention should be avoided.

## @Id and @GeneratedValue annotations

We can see that for attribute "a", our domain class contains two annotations, an *@Id* and *@GeneratedValue*.

These annotations are important given the context of this attribute, since the attribute in our database table corresponds to the primary key and has a serial type.

The *@Id* annotation symbolizes that the attribute is an identifier for this entity (i.e. the primary key), this automatically give's it certain properties, such as the unique and distinct constraints.

The *@GeneratedValue* annotation set's this attribute as being generated by the DBMS, making it an unnecessary inclusion when instantiating an object of this class since the system will generate it for us. The strategy used inside the annotation *GenerationType.IDENTITY* since this attribute is a serial and should be an incrementing number that corresponds to an ID, for example.


## Other field annotations

There are many other annotations used to enforce constraints and other business rules.

These annotations can be used to annotate fields in the Entity classes, such as the one seen above *@UniqueConstraint* which dictates which columns should have unique values, to bridge from the SQL keyword *unique*.