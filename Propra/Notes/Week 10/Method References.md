# Method References
- Lambdas are very useful, but don't always make your code easy to read.
- Take the case of the method `sort()` that takes a `Collection` and `Comparator` as parameters.
- Look at the following example. You don't have to go through the logic but pay attention to readability.

```Java
public static void main(String[] args) {
    List<Integer> integers = new ArrayList<>();
    integers.addAll(List.of(345, 533, 374, 11, 932, 357));

    Collections.sort(integers, (a, b) -> {
        for (int i = 2; i <= Math.max(Math.sqrt(a), Math.sqrt(b)); i++) { 
            if (a % i == 0 && b % i == 0) { 
                return 0;
            }
            if (a % i == 0) {  
                return -1;
            }
            if (b % i == 0) {  
                return 1;
            }
        }
        return a.compareTo(b); 
    });
    for (Integer i : integers) {
        System.out.println(i);
    }
}
```

Very difficult to read. Let's make it more readable by delegating the logic to another class, `PrimeComparator`. (Remember **SRP**!)

```Java
public static void main(String[] args) {
    List<Integer> integers = new ArrayList<>();
    integers.addAll(List.of(345, 533, 374, 11, 932, 357));

    Collections.sort(integers, (a,b) -> PrimeComparator.compareByPrimeFactor(a,b));
    
    integers.forEach(a -> System.out.println(a));
}
```

We've also shortened the `for`-loop. But we notice a pattern. We always pass a comparator with some parameters, and we call functions on those parameters. There's a to skip this: method references.

```Java
public static void main(String[] args) {
    List<Integer> integers = new ArrayList<>();
    integers.addAll(List.of(345, 533, 374, 11, 932, 357));

    Collections.sort(integers, PrimeComparator::compareByPrimeFactor);
    
    integers.forEach(System.out::println);
}
```

- Neat! Method references are notated with `::`.
- But what if we have the case where one of the parameters is the Instance of the method reference? E.g. `(a, b) -> a.something(b)`?
	- Answer: we can still use the same notation. In this case, calling a method reference will use the first parameter as the instance object and the second parameter will be passed into the referenced method.
		- Example: `Collections.sort(people, Person::compareByAge);`. `Person`s in `people` will be compared by age and sorted.
- We can also reference constructors:
```Java
BiFunction<String, LocalDate, Person> personFactory = Person::new;
Person person = personFactory.apply("Kerry Marisa Washington", LocalDate.of(1977, 1, 31));
```
