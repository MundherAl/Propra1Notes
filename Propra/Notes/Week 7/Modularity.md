# Modularity
- In Java, we primarily use classes, packages and modules as a structuring mechanism.
---
## Information hiding and encapsulation
- Whenever we are implementing a component, we should consider the following:
	- Is the component going to intersect with other modules? If yes, then set the modifier to `public`.
	- Is the component more important for the internal structure of a module? Mark it with `private`.
	- Does the component consist of multiple classes? All classes should be `private` except the ones that intersect with other modules.
---
## Testing implementation details
- `private` methods might seem problematic for testing.
- However, Maven and Gradle combine the packages inside `main` and `test`, so we can create instances of a class and test implementation details.
- We generally try to avoid this as it increases coupling.
---
## Invariants
- Invariants are properties that stay the same after a change in an object's  state.