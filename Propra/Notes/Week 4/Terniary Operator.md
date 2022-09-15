# Ternary Operator
Example:
```Java
int x = 0;
if (y.isEmpty()) x=42;
else x = y.length();
```

Using the ternary operator `?`, we can shorten the code above to this one-liner:

```Java
int x = y.isEmpty() ? 42 : y.length();
```

The anatomy of an expression that uses the terniary operator looks like this:

`test ? then : else;`

The `test` will be performed. If it succeeds, our expression takes the value of `then`. If it doesn't succeed, our expression takes the value of `else`.