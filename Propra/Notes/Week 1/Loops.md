# Loops
## Recursion
- Usually a bad idea for Java due to memory usage

# Enhanced For-Loop
- Works for every class that uses the `Iterable` interface.
- Quick example:

```java
List<Person> studierende = getStudierende(); 
for(Person p : studierende) { 
System.out.println(p.getAlter()); 
}
```

## Lambdas
- Syntax: `(a,b,c) -> { // java code }`

## For-Each Method
- `forEach()` gets a `Consumer` interface to apply a Lambda on an object that implements the `Iterable` interface.