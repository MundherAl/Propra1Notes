# More Code Smells
## What was a smell, again?
- A code smell is a hint, that our code might contain something that is not maintainable.
- Here are a couple of smells.
---
## Large Class
- When a `class` gets too big, there's a very good chance that it violated the SRP.
---
## Primitive Obsession
- We should try to create domain objects.
- If our code contains a lot of primitive types, then we should consider implementing some domain objects.
---
## Data Clumps
- If we see a lot of data types in a code block, we should consider making smaller data groups.
- Example: we want to calculate the distance between two points.
```Java
class Calculator {
	public static getDistance(int x1, int y1, int z1, int x2, int y2, int z2) {
	// implementation
	}
}
```

That's awful! This is better:

```Java
public record Point(int x, int y, int z) {}

class Calculator {
	public static getDistance(Point p1, Point p2) {
	// implementation
	}
}
```
---
## Divergent Change
- This one starts stinking when we keep having to edit a class whenever making changes in external components.
---
## Shotgun Surgery
- Sometimes adding a new feature leads to having to make changes in many other parts of our code. That stink is shotgun surgery.
---
## Feature Envy
- When a class calls too many methods from another class, it's a sign of feature envy. This causes high coupling and low cohesion!
---
## Message Chains
- Occurs when a class (class A), in order to get some data from class D, must access class B and use it to access class C, and use class C to access class D.
- The reason to avoid this is that class A becomes reliant on the implementation of the in-between classes (classes B and C).
---
## Refused Bequest
- A Refused Bequest smell occurs when a subclass removes or hides inherited functionality.
- This is an indication that the class should not be a subclass of the parent class, since child classes should add or modify functionality.