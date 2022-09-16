# Functional interfaces
- Functional interfaces are interfaces that contain only one abstract methods.
- They are immensely useful for streams.

Examples:
- `Consumer a -> void`
	- Takes a parameter `a` and performs an action.
```Java
Consumer<Integer> printPlusOne = a -> System.out.println(a+1);
printPlusOne.accept(2); // prints 3
```

- `Function a -> b`
	- Takes a parameter `a` and returns `b`.
```Java
Function<Double, Double> timesTwo = a -> a*2;
timesTwo.apply(3); // ==> 6
```

- `BiFunction (a, b) -> c`
	- Takes two parameters `a` and `b` and returns `c`.
```Java
BiFunction<Double, Double, Integer> multiply = (a, b) -> (int)a*b;
BiFunction.apply(2,4); // ==> 8
```
```ad-note
We cast the result into an `int`. See if you can spot why.
```

- `Predicate a -> boolean`
	- Takes a parameter `a` and returns a `boolean` type.
```Java
Predicate lessThanTen = a -> a < 10;
Predicate.test(5); // true
```
```ad-info
This a considered a subset of the `Function` interface.
```

- `Supplier () -> a`
	- Takes no parameters and returns `a`.
```Java
Supplier tossCoin = () -> (int)(Math.random())+1;
tossCoin.get(); // (maybe) 1
tossCoin.get(); // (maybe) 0
```