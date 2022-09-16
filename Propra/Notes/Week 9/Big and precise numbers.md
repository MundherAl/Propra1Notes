# Big and precise numbers
## Big numbers
- We know that Integers have a maximum value that we usually don't reach.
- But what if we have a scenario that requires a value beyond the maximum integer?
- `BigInteger` is here to the rescue.
```Java
BigInteger x = BigInteger.TWO;
BigInteger y = BigInteger.valueOf(Integer.MAX_VALUE);

x = x.multiply(y)

System.out.println(x) // ==> 4294967294 (two times the max value!)
```
---
## Precise numbers
- We're familiar with the problems that occur with `double` and `float` types:

```Java
double d1 = 0.3; 
double d2 = 0.1; 
System.out.println(d1-d2); // => 0.19999999999999998
```

- `BigDecimal` has some resources to deal with this problem:

```Java
BigDecimal d1 = new BigDecimal("1");
BigDecimal d2 = new BigDecimal("3");
System.out.println(d1.divide(d2, new MathContext(1))); // 0.3
System.out.println(d1.divide(d2, new MathContext(4))); // 0.3333

BigDecimal d3 = new BigDecimal("8");
System.out.println(d1.divide(d3, new MathContext(3))); // 0.125
System.out.println(d1.divide(d3, new MathContext(2))); // 0.13
```