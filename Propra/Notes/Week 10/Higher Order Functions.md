# Higher Order Functions
- We've seen Higher Order Functions (HOF) before. They aren't **that** special.
- Just like normal functions, they take parameters and do something with them.
- The only difference is, that they take functions as parameters. Hence, the "higher order" in the name.
- We already know the `forEach()` method. But we didn't know it was a HOF!
```Java
List<Integer> numbers = list.Of(1,2,3);
numbers.forEach(n -> System.out.println(2*n)); // prints every number in the list multiplied by 2
```

- We can also have a functional interface as a return type for our HOF:
```Java
public static <T> Supplier<T> constantly(T value) {
    return () -> value;
}

public static void main(String[] args) {
    Supplier<String> dot = constantly(".");
    System.out.println(dot.get());
}
```

- Some cool things we can do with HOFs:
```Java
public static <T> UnaryOperator<T> applyTwice(UnaryOperator<T> f) {
	return p -> f.apply(f.apply(p));
}

UnaryOperator<Integer> multiplyByTwo = e -> 2*e;
System.out.println(applyTwice(multiplyByTwo).apply(2)); // applies the method multiplyByTwo twice on the parameter 2. result is 8.
```