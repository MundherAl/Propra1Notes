# Dependency Inversion
We have used dependency inversion in the [[Dependency Injection]] example without having talked about it. Take a look at the code:

``` Java
class Car {
	private final ExcideBattery battery;

	public Car() {
		this.battery = new ExcideBattery();
	}
}
```

We can already spot the problem if we're familiar with dependency injection. Let's optimize:

``` Java
class Car {
	private final ExcideBattery battery;

	public Car(ExcideBattery battery) {
		this.battery = battery;
	}
}
```

This is already better. But what if we want to use a different type of battery? We will have to change quite a bit in the code. Let's instead create an interface `Battery`.

```Java
interface Battery {
	// methods
}
```

Everytime we want to add a new type of battery, it should implement the `Battery` interface. Why? Because it allows the following:

```Java
class Car {
	private final Battery battery;

	public Car(Battery battery) {
		this.battery = battery;
	}
}
```

How much better is this? On medium or big sized projects, this is infinitely better. We can now equip cars with any battery just by passing them into the constructor `Car()`, instead of having to change internal structure.

This also promotes **interfacing**, a very good programming practice. If we need to implement a new type of battery, we will use the `Battery` interface and it'll be immediately usable in any `Car` object.