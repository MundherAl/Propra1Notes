# Class inheritance
- Every Java class inherits from the `Object` class.
- When using inheritance, make sure you're applying an "is-a" relationship. For example, it wouldn't make sense to have a `Customer` inherit from an `Employee`. They might both be persons, but a `Customer` in most contexts is usually not an extension of an employee.
- Liskov Substitution Principle: we should always be able to substitute a `Superclass` with its `Subclass`. i.e. invariants should not be violated when using subclasses.
- What is great about inheritance?
	- Makes it easy to implement new subclasses.
	- Gives us pre-context for the behavior that the subclass is supposed to have.
	- Open/Closed principle:
		- Our code is open to add new extensions without having to alter client code so much. (**Open for extension**)
		- We don't need to change anything when extending our code. (**Closed for modification**)
---
## Inheritance and coupling
#### Interface inheritance
- By using inheritance, we increase coupling. But it's not so bad in the case of interfaces.
- By making classes that extend an interface, we create a coupling at compile-time, but we practically only inherit function names.
- ISP: Interface Segregation Principle.
	- ISP says "make your intersections as small as possible but as big as necessary".
	- When designing an interface, make sure it only contains methods that you **NEED**.

#### Class inheritance
- Contrary to interface inheritance, class inheritance increases coupling substantially.
- Class inheritance violates encapsulation; the subclass needs to know the implementation details of its superclass. (remember IHP?)
- Worst-case scenario: changes in the superclass cause subclasses to stop working, without having modified code of the subclasses. 