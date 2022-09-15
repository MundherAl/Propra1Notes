# Domain Driven Design
- Software projects fail. Most fail due to communicational issues.
- Technical expertise is not enough. Software developers need to communicate within and understand the domain they are designing a software for.
- This is a central idea in DDD (Domain Driven Design).
- So: we need domain experts and developers to first speak the same language. Then we can start drafting models.
	- Developers should integrate domain language in their code. For example, if domain experts use the word "premium" to describe a price-up, then name the corresponding method `addPremium()`.
	- It is a very good idea to devise a domain glossary to keep communications explicit and clear.
	- Consider contexts. A `Customer` in marketing is considered a person that will make a future purchase. A `Customer` in payment systems is a person that has already made a purchase. Consider having two separate `Customer` classes and separating `MarketingServer` and `PaymentServer` in different packages.
	- **Domain Objects**: consider creating objects and naming them after their domain names instead of using primitive types. Example: instead of saving a credit card number in a `String creditCard`, create a class `CreditCard`. This makes a lot of things easier like checking whether the object you are passing to a function is a credit card. You would otherwise have to create a method, that takes a string, that verifies that your string is indeed a credit card, and returns a boolean, that you need to use in an `if` statement... You get it.
---
## Entities, values and aggregates
- In DDD, we distinguish between two types of domain objects: **entity objects** and **value objects**.
- **Entities** are objects that have a "life cycle". We create them, they exist, and we transform them or remove them. They have the concept of an identity.
	- For example, an `Account` can be an entity at a bank. We create it, it belongs to someone, the amount of money it has changes, we can remove it when a customer chooses to close their account.
- **Value objects** don't require an identity.
	- Example: if we have an online woodworking shop, we only care if our tabletop is made of maple. We don't care about its "identity", ergo which exact maple tree it came from.
- Depending on context, the same domain object could be either.
	- Example: a car needs to be an entity for the production team (serialno., specifications, etc..). For data processing, a car could just be a value object (serialno., specifications and so forth are not valuable for data processing).
---
## Entities in Java
- Entities need to have an identity, so in some way unique. To distinguish between entity objects, a common solution is to use unique sequences of numbers or UUIDs (Univerally Unique Identifiers). 
- The latter is easy: Java has a `UUID` class that generate a (with huge guarantee) unique ID using the method `UUID.randomUUID()`.
	- **Note** that `UUID`s have higher memory costs than a `long` would.
- If we opt for the former, we ought to make sure that the sequences truly are unique and no duplicates can occur. We also need to make to sure override the `equals()` and `hashcode()` methods that come with every object.
---
## Value Objects in Java
- When creating a value object, we need to override the `equals()` and `hashcode()` methods as well.
- Often we use `record`s. Attributes of records are always final, `equals()` and `hashcode()` methods are automatically generated.
- Try to adhere to LCHC. Records can distract us from that. Take the following example:

```Java
public record Computer(String gpu, String cpu, String os, String osArchitecture, String manufacturer, String model);
```

This is very low cohesion. Better is the following:

```Java
public record Hardware(String gpu, String cpu);
public record Software(String os, String architecture);
public record Make(String manufacturer, String model);

public record Computer(Hardware hw, Software sw, Make make)
```

This adds a lot more cohesion and makes for cleaner code than having to use classes.

- Records differ from classes through their getters: Classes have getters `getAttribute()` while records have just `attribute()`.
---
## Aggregates
- An **aggregate** consists of both value and entity objects that are related to each other in a context.
- We have the following rules for aggregates:
	1. Entities that belong to an aggregate have the same lifecycle as the aggregate.
	2. Every aggregate has a root-entity (aggregate-root).
	3. When referencing an aggregate outside of its classes, we only allow references to the aggregate-root.
	4. The aggregate-root is the entry-point that defines its intersection with the universe.
	5. Aggregates have so-called "eventual consistency". This means that the consistent state can have temporal delays.
		- Example: when modeling a bank transfer, money is usually booked immediately from one account but may take a while until it is booked into the beneficiary's account.

Example of an aggregate (graphical):
![[Aggregate Example]]

#### Interacting with aggregates
- See example above. We can reference a `ManufacturerID` but what if we want a manufacturer to be able to reference a `TumbleDryer`? Who should be able to reference whom?
- The answer is **none of the above**.
- We instead use a so called **Domain-Service**. A domain-service could look like this:

```Java
public void addTumbleDryer(TumbleDryer td, Manufacturer manu) {
	td.addManufacturer(mfkt.getID());
	manu.addTumbleDryer(td.getID());
}
```
