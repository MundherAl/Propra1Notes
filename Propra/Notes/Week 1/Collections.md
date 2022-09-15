## Java Class Libraries
- Focus on **Collections Framework**.

### Collection
- Is the basic interface of most generic data structures in Java
	- e.g. A `HashSet` implements `Set` which implements `Collection`
	- Methods: `add, addAll, remove, removeAll, removeIf, contains, containsAll, size, isEmpty, toArray, stream`
	- `retainAll()` returns the intersection of two collectibles.

### List
- Motivation: Collections that require an order but not necessarily sortation.
- Extends collection with methods: `get, set`.
- Lists that are initialized using the method `List.of()` are immutable.
	- The following implement the `List` interface:
		- `ArrayList`
		- `LinkedList`  mostly used as implementation for stacks or queues.

### Queue
- FIFO-Queue (first-in-first-out)
- Methods:
	- `offer()` adds an item in the queue.
	- `poll` returns and removes the next item in the queue.
	- `peek` returns the next item in the queue without removing it.

### Deque (stack)
- Uses LIFO
- Methods:
	- `push()` adds an item on top of the stack.
	- `pop()` returns top of stack and removes it from stack.
	- `peek()` returns top of stack without removing it from the stack.

### Set
- Is the implementation of the mathematical idea of a set.
- Often used is `HashSet`
- Is not necessarily sorted if `SortedSet` is not implemented.
-  `TreeSet` implements `SortedSet`, so TreeSets are sorted according to a comparator.
- `Comparator` is a functional interface. Meaning it contains only one function.