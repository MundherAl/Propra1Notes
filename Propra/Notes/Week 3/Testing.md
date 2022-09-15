# Testing
## Testing Spectrum
- Tests are used to validate. There are different scenarios for validating.
	- Formal proofs: Testing is not very useful here.
	- Trial and error scenarios: Testing is not so useful here either.
	- Tests are great for validating for scenarios between proofs and trials on the spectrum.
## Why test?
- Automated tests are great investments. They improve the maintainability of software.
- Tests prevent regression. Changes in code often leads to old errors and tests prevent that.
- Tests are a good documentation of what a code does.
- Tests give a good sense of security when changing code.
- Tests can show the presence of bugs but not their absence!
---
## Testing principles
1. Tests need to be simpler than the source code.
2. Tests should be as linear as possible.
3. Tests shouldn't contain complicated logic.
4. Tests need to test one functionality at a time.
5. Tests should test program behavior and not implementation details.
---
## AAA
There are 3 steps to creating a test:
- Arrange:create context (initialize objects).
- Act: run the code.
- Assert: validate results.
---
## FIRST Principle
- Fast: Tests need to be short and quick to run.
- Isolated: Tests should not be dependant on each other and should be runnable arbitrarily.
- Repeatable: Tests need to be reliable and deliver the same results on any other computer.
- Self-evaluating: Tests should validate themselves and we shouldn't need to look at the results and validate them ourselves.
- Timing: Tests should be performed as soon as possible.