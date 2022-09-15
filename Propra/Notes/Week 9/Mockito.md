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

- Stubs give the advantage of control. By creating stubs, we can control effects from outer components and always get deterministic results.
- Stubs minimize costs in many scenarios.
- Stubs can save a lot of programming effort and keep code at a minimum. Check out this example:

```Java
interface CustomerRepository {
	String getNextCustomer();
	boolean iterationCompleted();
	void addCustomer();
	void resetIteration();
}
```

Creating a test double for this would mean that we have to create a class that implements all these methods. Mockito can shorten this process:

```Java
@Test
void simple_test() {
	CustomerRepository repo = mock(CustomerRepository.class):
	when(repo.getNextCustomer()).thenReturn("John Doe");
	when(repo.iterationCompleted()).thenReturn(false).thenReturn(true); // first call returns false, all others after true
	// assertions here
}
```

Neat. We don't have to create a class `FakeRepository` and implement all the interface functions and THEN test.

---
## Dummies
- Dummies are a type of test double that are used to pass as parameters.
- Example: Mail server needs a `Location` to initialize.

```Java
	@Test
	void test() {
		Email email = new Email("abc@gmail.com");
		MailServer server = new MailServer(email, mock(Location.class)) // Don't need a Location object!
	}
```
---
## Mocks
- Mocks are basically stubs but smarter. Mocks contribute to the assert step in testing, while stubs don't.
- Example: Let's use our repository from above to test a `MarketingApp` that uses a `MailSender`.

```Java
@Test
@DisplayName("Sends two emails")
void test() {
	// arrange
	CustomerRepository repo = mock(CustomerRepository.class):
	when(repo.getNextCustomer()).thenReturn("me@you.com", "you@me.com");
	when(repo.iterationCompleted()).thenReturn(false).thenReturn(true);
	MailSender mailSender = mock(Mail.class);
	MarketingApp marketingApp = new MarketingApp(repo, mailSender)
	// act
	marketingApp.doMarketing();
	// assert
	verify(mailSender).sendMail("me@you.com");
	verify(mailSender).sendMail("you@me.com");
	verifyNoMoreInteractions(mailSender); // makes sure that the mailSender doesn't have more interactions than the two above.
}
```

- In the assertion step, the `verify()` method asserts that the `sendMail()` method was called in `doMarketing()` twice with the given parameters.

```ad-note
If the order matters, then we can use an `InOrder` and call the verify method through it to make sure assertions happen in the correct order.
```
Verification can get pretty interesting:

```Java
verify(mailSender, times(2)).sendMail(anyString());
verify(mailSender, never()).sendMail("lmao@lmao.com");
verify(mailSender, atLeastOnce()).sendMail(anyString());
```

The wonderful part is that the code is very readable. I bet you can guess what the code does without me having to explain it to you.