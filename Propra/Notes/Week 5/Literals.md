# Literals
- Literals are data values that can be used in a program without having to call a constructor. For example:
	- `5` `"Foo"` `true` `3.14` are all literals.
- We might face the problem of having to use an integer that is bigger than the maximum value. For this, we need to use `long` literals:
```Java
long n = 2147483648; // does not work.
long n = (long) 2147483648; 
// also does not work because the literal is still an integer and therefore the value is invalid.
long n = 2147483648L; // works because we provide a long as a literal and not an integer.
```
- We can use other number bases:
``` Java
int a = 30; // Decimal
int b = 0x1e; // Hexadecimal
int c = 036; // Octadecimal
int d = 0b11110 // Binary
```
- We can use underscores in numbers to increase readability:
``` Java
int n = 10_000_000 // is the same as 10000000
```
- Textblocks:
``` Java
String text = """
This is
a very lengthy
paragraph
"""
```
This is useful when having to deal with HTML.