In JPA, the management and manipulation of entities is done through a class called the *EntityManager*.

This class is instantiated through the use of a factory class named *EntityManagerFactory* which allows us to create instances of the *EntityManager* class in order to manipulate data.

Here is an example of the instantiation of an *EntityManager* object through the *EntityManagerFactory*:

```java
private EntityManagerFactory emf = Persistence.createEntityManagerFactory("persistence_name");

private EntityManager em = emf.createEntityManager();
```

Through the entity manager we can access the database through operations like:
- Persisting
- Finding
- Merging
- Removing

These operations make up the CRUD operations available in DBMS (creating, reading, updating, deleting).

Let's take a look at how we can store an entry in a table through JPA's *EntityManager*:

```java
public static void persistEntity(Entity e, EntityManager em) {

em.getTransaction().begin();
em.persist(e);
em.getTransaction().commit();

}
```

In this example, we take in two parameters. The first is the entity we wish to persist and the second is the entity manager we are using to persist it.

We use *em.getTransaction.begin()* in order to begin an SQL transaction, afterwards we use *em.persist(e)* to persist the entity parameter in the DB (store it). Finally, we use *em.getTransaction.commit()* to commit the current transaction, making our changes final.

If we require, and if the Entity class has an auto-generated ID property, like the ones mentioned in [[Class (DB Entity) Representation]], we can access it after persisting the entity to the DB through *e.getId()*.


(Note: The code below does not handle exceptions)

We can also do a search, by id for example, using this entity manager:
```java
public static Entity findEntityById(long id) {
	return em.find(Entity.class, id);
}
```

Update an entity given it's ID and new value for attribute:
```java
@Entity
class Entity {
@Id
private long id;
private String name;
}


public static void updateEntity(long id, String newName){
	Entity updated = new Entity(id,newName);
	
	em.getTransaction().begin();
	em.merge(updated);
	em.getTransaction.commit();
}
```

Delete an entity given it's id:
```java
public static void deleteEntity(long id) {
	Entity toDelete = em.find(Entity.class,id);
	
	em.getTransaction().begin();
	em.remove(toDelete);
	em.getTransaction().commit();
}
```

