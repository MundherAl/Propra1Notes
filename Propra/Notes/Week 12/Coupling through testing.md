# Coupling through testing
- We know that tests should be specific and test program behavior.
- Problem: badly written tests could be an obstacle that causes a lot of frustration.
- One change in the implementation for a class could break 20 other tests.
	- Example: we run 10 tests that are coupled to a class `SickLeave(Employee e, LocalTime from, LocalTime till)`. 
	- If we decided to re-parametrize to `SickLeave(Employee e, Duration d)`, we will probably have to rewrite up to 10 tests.
``` ad-note
To fall into that trap less often, remember the DRY principle.
```
## Factory methods
- A useful trick for the scenario above are factory methods. We would include a static factory method like:
```Java
class SickLeave {
	public static SickLeave sickLeave(Employee e, LocalTime from, LocalTime till) {
	return new SickLeave(Employee e, new Duration(from, till));
	}
}
```
This leads to a lot less refactoring!

---
## Builder pattern
- The builder pattern is yet another design pattern.
- Its main purpose is to separate the construction of an object from its representation.
- It solves problems like:
	- How can a class create different representations of an object?
	- How can we make creating a complex object simpler?
- Including solutions to the above problems causes a class to be inflexible. Enter builders.
- Builders solve such problems by delegating object creation to a `Builder` class. This allows different representations of the complex object that we are creating. 
---
## ObjectMother
- When writing tests, we often have to specify a certain configuration of an object that we want to test.
	- For example: a test to see what happened if you give an employee 3 days of sick leave, when they have a salary amounting to x, etc…
- This could lead to repetitive code. For every test, we will have to specify a configuration.
- Enter ObjectMother. These are just pre-configured objects that we set up for testing.
- This has many advantages:
	- You can easily tell what is being tested.
	- Communicating with other developers becomes easier when everyone is familiar with ObjectMothers.
- There is, however, a caveat. ObjectMothers couple tests with the specified attributes they have. In a way, they test less the traditional way we'd set up our tests. This is usually not too bad, because our tests should test behaviors with as little context as possible.