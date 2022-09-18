# Test Duplication
Make sure your test is sensible. Look at the following:

```Java
public static double percentage(double percent, double value) {
	return percent * value / 100;
	}

@Test
void test() {
	double testedValue = percentage(10,100);
	assertThat(testValue).isEqualTo(10*000/100);
}
```

That is sort of like asking, "does percent times value return percent times value?"
That is a duplication that we want to avoid.