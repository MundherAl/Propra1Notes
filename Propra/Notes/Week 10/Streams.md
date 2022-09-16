# Streams
## Quick summary
- By now you have hopefully understood higher order functions.
- They are however mostly used in the context of `Stream`s and not `Collection`s.
- A common heuristic when first learning about streams is thinking they are a type of data structure. They are not.
- Streams are to be looked at as a "processing pipeline".
	1. Streams first get fed with data.
	2. This data is processed by so-called intermediate operations.
	3. At the end of the pipeline process, is so-called terminal operation. This operation generates the final result.

---
## Creating a stream
- We often create a `Stream` from a data structure, for example a `Collection`.
```Java
List<Integer> integers = list.Of(1,2,3,4,5);
Stream<Integer> integerStream = integers.stream();
```

- We can also create streams without a data structure as a starting point using the methods:
	- `generate()`
	- `iterate()`
- Let's see how we can use these methods:

###### `generate()`
```Java
Stream<Double> randomStream = Stream.generate(Math::random); // generates a stream of random doubles.
```

###### `iterate()`
```Java
UnaryOperator<Integer> successor = e -> e + 1;
Stream<Integer> generatedSequece = Stream.iterate(0, successor) // initial value 0. generates a stream 0, 1, 2, 3, ..
```

```ad-note
Notice how both streams are infinite. Is a sort of hint that streams are not a data structure. They are something more.. fleeting.
```

- We can also create streams from primitive types that are more efficient for their corresponding types.
```Java
IntStream from0to999 = IntStream.range(0,1000);
IntStream from0to1000 = IntStream.rangeClosed(0,1000);
```

- There are, however, some methods that are available from `Stream`s but not for `IntStreams`. But the smart guys at Stream Incorporated figured this out already.
	- We can use the method `boxed()` to make a `Stream` out of an `IntStream`.
	- We can also use the method `mapToInt()` to make an `IntStream` out of a `Stream`.

```ad-info
There are many helpful methods that `IntStream`s have that are not often not useful for normal `Stream`s, like `sum()` or `average()`.
```
---
## Intermediate operations
- If we imagine our stream to be a conveyor belt, then intermediate operations are the workstations at which items get operated on.
```ad-note
Every intermediate operation returns a `Stream`.
```
- Some useful intermediate operations:
	- `limit(long n)` ends the stream after `n` elements.
	- `skip(long n)` skips the next `n` elements.
	- `takeWhile(Predicate p)` ends the stream as soon as the predicate `p` returns `false`.
	- `dropWhile(Predicate p)` keeps dropping elements until `p` returns `false`.
	- `peek(Consumer c)` performs a consumer `c` on every element and keeps them unchanged. This is usually used for logging or debugging.
	- `distinct()` removes all duplicates from the stream.
	- `sorted()` sorts all the elements in the stream in their natural order. We can also pass a `Comparator` to define an order.
```ad-attention
In order for `sorted()` to work properly, it needs to "look ahead" at all the elements of a stream. This causes problems when using `sorted` with infinite streams. Always make sure your stream is finite.
```
---
## Terminal Operations
- At the end of every stream, there is exactly one terminal operation that delivers a result.
```Java
IntStream intStream = IntStream.range(0,5);

intStream.forEach(System.out::println); // 0, 1, 2, 3, 4
intStream.forEach(System.out::println); // Exception
```

- `toArray()` and `toList()` are also useful terminal operations:
```Java
Stream<Integer> stream = IntStream.range(0,5)
	.map(e -> e * 2)
	.boxed();
	
List<Integer> integers = stream.toList(); // [0,2,4,6,8]
```

- Other often used terminal operations:
	- `min(Comparator c)` and `max(Comparator c)` give the minimum or maximum according to a comparator `c`.
	- `count()` returns the number of elements in the stream.
	- `anyMatch(Predicate p)`, `allMatch(Predicate p)` and `noneMatch(Predicate p)` checks if all, any or none of the elements in a stream match the predicate `p`.
	- `findFirst()` returns the first element of the stream.
