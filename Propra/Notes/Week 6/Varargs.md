# Varargs
- There are many methods in Java that take an arbitrary number of parameters. How does that work?
- Answer: Varargs
- Here's how we use them:

```Java
public void foo(String ... args) {
	if (args.length == 0) System.out.print("Empty")
	System.out.print(args[args.length()-1])
}

foo(); // leer 
foo("a"); // a 
foo("a", "b", "c"); // c
```

Pretty cool.