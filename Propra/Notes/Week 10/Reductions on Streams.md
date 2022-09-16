# `reduce()`
- We're familiar with the `reduce` function.
- In `Stream`s, the `reduce` function is a terminal operation:
```Java
Integer reduced = Stream.of(3,4)
	.map(e -> e * e)
	.reduce(0, (a,e) -> a + e);
```

- What does the code above calculate?
	1. We first have a stream of (3, 4)
	2. Then we map it to (9, 16)
	3. Then we reduce it using the given lambda expression with initial value `0`. (0 + 9)
	4. Then we reduce it again with the previous accumulated sum. (9+16)
	5. All elements have been processed $\rightarrow$ stream terminates and returns 25.
---
# `collect()`
- We usually use `collect()` instead of `reduce()`.
- The method `collect()` uses a mutable accumulator, and this makes processing streams much faster.
- The generic `collect()` method has three parameters:
	- A `Supplier` for the initial value.
	- A `BiConsumer(A,E)` as a function that mutates the accumulator object.
	- A second `BiConsumer(A,A)` to combine the content of the first accumulator with the second.
Example:
```Java
List<Integer> list = List.of(2, 5, 2, 2, 4, 6, 8, 4, 5);
HashSet<Integer> set = list.stream()
    .map(e -> e + 1)
    .collect(() -> new HashSet<Integer>(), 
             (a, e) -> a.add(e), 
             (a1, a2) -> a1.addAll(a2)); // [3,5,6,7,9]
```