# Collectors
- Motivation: every time we have a use case for a `collect()`, we have to write 3 functions. A lot of work and has a lot of potential for mistakes.
- The `Collector` interface comes to the rescue!
	- It always implements five methods.
	- Details in documentation. :)
- We can use the `Collectors` class methods to ease some work:
```Java
List<Integer> list = List.of(2, 5, 2, 2, 4, 6, 8, 4, 5);
Set<Integer> set = list.stream()
	.map(e -> e + 1)
	.collect(Collectors.toSet());
```
