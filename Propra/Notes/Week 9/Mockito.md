# Test doubles and Mockito
- Test doubles are "fake" implementations of production objects.
	- Example:
	![[Test Double Example]]
``` ad-note
When testing, we try to avoid side effects. In the example above, we don't want to send actual emails to test our code. A good solution is to create a mail server double. Mockito does a great job at this.
```
- #### Why do we need test doubles? So many reasons.
	- There are classes that produce nondeterministic results. Test doubles can control this.
	- Some objects are difficult to isolate, which cause parallel testing problems.
	- Some implementations are expensive, like accessing databases (relative to accessing local files.)
	- Some objects are difficult to bring into the state that we want to test. For example, if we want to test what happens if a hard drive is full, it would be better to create a double instead of actually filling your hard drive.
	- Some objects are also unreliable. For example, objects that rely on the network they're on.
	- Some tests have undesirable side effects (like sending emails).

```ad-attention
The trouble with this, is that test doubles lead to boilerplate code, code that keeps repeating itself with very minor changes.
```

And so was mocking born. Mocking is a way to create test doubles on the fly. Mockito is an excellent framework for this.

Mockito creates so-called stubs, dummies and mocks. These are test doubles.
Syntax: `Object myObject = mock(Object.class)`

---
## Stubs
- Stubs are a type of test double that don't have logic. They are meant to simulate real objects for a test scenario. 
	- Example: we want to test if clients can receive mails. We create a stub mail receiver instead of using a real email address.

Let's try testing the scenario above without using Mockito:

```Java
@Test
@DisplayName("Sends a mail on a hot day")
void test_1() {
	// Arrange
	ForecastServer fakeWeather = () -> 30;
	FakeSender fakeSender = new FakeSender();
	CustomerRepository customerRepo = () -> List.of("me@you.com");
	MarketingApp marketingApp = new MarketingApp(fakeWeather, 
	fakeSender, customerRepo);
	// Act
	MarketingApp.sendMessage("Discounts on icecream!");
	// Assert
	assertThat(mailSender.mailsSent).isNotZero();
}
```

This can be shortened to:

```Java
@Test
@DisplayName("Sends a mail on a hot day")
void test_1() {
	ForecastServer fakeWeather = () -> 30;
	MarketingApp 
}

```