# Mocking, revisited
- We've seen how mocks and stubs can be very useful tools for testing.
- But if we're not careful, they might cause **very high** degrees of coupling!
---
One could say, we have three types of tests. There are tests that:
1. directly verify a returned value from a method of a component.
2. check what happens to the state of a component.
3. test the interaction between tested components and external components.
---
## 3 types of tests
- For the first two types of tests, we can use stubs to verify our expected behavior.
- The third type of test requires the usage of mocks. This can go wrong!
	- [Mocking gone wrong - YouTube](https://www.youtube.com/watch?v=4EPHz1dn-KY)
