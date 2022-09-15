# Type inference
- The keyword `var` can be used to infer the type of a variable.
Example:

```Java
List<Integer> arr1 = new ArrayList<>();
var arr2 = new ArrayList<Integer>(); 
```

The two lines above are equal.

Caveat: the keyword `var` cannot be used without initializing a variable. 