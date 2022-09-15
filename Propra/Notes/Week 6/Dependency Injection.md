# Dependency Injection
## Dependency Injection
Look at the following code:

``` Java 
class Car {
	private Wheel wh = new NepaliRubberWheel();
	private Battery bt = new ExcideBattery();
}
```

What is the problem with the code above?
- It is handling logic from other modules by calling their constructors.
- This means that the dependency is given at compile-time and not at run-time. If we want to change a wheel or a battery, we can't.
- For example: if we want to use another type of battery, we will have to change the logic inside the car as well.

Let's use dependency injection.

```Java
class Car {
	private Wheel wh;
	private Battery bt;

	public Car(Wheel wh, Battery bt) {
		this.wh = wh;
		this.bt = bt;
	}
}
```

- We are therefore not relying on the class `Car` to create its own objects and use them. 
- Rather, we create the objects that `Car` depend on and inject them. 
- If we now want to swap out a `Wheel`, then we simply call the `Car()` constructor with the new type of `Wheel`. No internal code changes in `class Car`!
- This also makes testing easier, because we can now use mock `Wheel` or `Battery` objects. 

**In simple words:** dependency injection is *giving* an object its instance variables instead of delegating the task *to* the object itself.