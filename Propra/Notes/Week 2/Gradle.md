# Gradle
- Gradle is a useful tool for building applications:
	- Gradle can run tests automatically.
	- Can keep good track of external libraries.
	- Packs files as .jar.
	- Tracks file paths and compiles (doing this manually in a big project is difficult).
- Convention:
	- Product code is in `src/main/java`
	- Testcode is in `src/test/java`
	- Resources are in `src/main/resources`
	- Test-resources are in `src/test/resources`
	- It is possible to deviate from this convention and configure it manually.
- Commands:
	- `./gradlew run` to run the program.
	- `gradle test` to run the tests task.
	- `gradle build` to build the project.