# Organizing Tests
## Test names
- It is a common and good practice to describe every test with the annotation `@DisplayName("tests output")`
- If there is an arrange step that is similar for every test, we can use the `@BeforeEach` annotation before a function. The annotated function will run before every test.
- It is a good idea to tag tests using the `@Tag("myTag")` annotation. We can set up gradle to ignore certain tests if they are for example tagged with `@Tag("slow")` so that our program can build faster. 