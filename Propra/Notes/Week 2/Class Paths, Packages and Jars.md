## Class Paths
- We often separate java files in different directories.
	- In order for the main code to run, it compiles other classes that it may require.
	- If the classes are not in the same directory as the main class, then we need to manually tell java where the classes are located using `javac -cp <dir> <source file>` where dir is the directory in which the classes are located.
	- When running the source code, we also need to specifiy the location of the classes directory.
	- When changing the class path, java will try to look for the main code in the class directory. This needs to be remedied. We can use a `:` (in linux) to add another class path.

---
## Packages
- Motivation: we need a good way to structure our projects.
- Therefore we declare the directory of the file we are working on using `package name.of.package`.
- Package structure is supposed to stay the same, independant of the computer its on.
- Package declaration must be the same as the file path.
---
## Visibility modifiers
- For methods and attributes:
	- `public` can be used by world.
	- `private` can only be used within a class.
	- `protected` can only be used within a package and subclasses or subpackages.
	- if not specified, then it is package-private.
- For classes:
	- `public` can be used by world.
	- `private` can only be used within a class.
	- If not specified, then it is package-private.
---
## Jar files
- Motivation: How to send a big structure of java files?
- Answer: zipping them using `jar`
- Example:

``` linux
home ~ ls
Manifest.txt hello
```
Manifest.txt is a file that indicates which file is the Main code.

Create a jar file using `jar cfm run.jar Manifest.txt hello/*.class`

Now we can run our program using `java -jar run.jar`

If we don't zip the Manifest file in the jar file, then we need to specifiy the class path. Example:
`jar cf run.jar hello/*.class`
`java -cp run.jar hello.Hello`
works exactly the same as with the manifest.