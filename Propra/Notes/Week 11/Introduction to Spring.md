# Spring
## What is it?
- Spring is a framework for developing enterprise applications.
- Spring uses parts of Java Enterprise Edition.
- Spring has been around since 2002(?). Enough time for it to mature and become more robust.
- Very widely used in the industry.
- Spring is also open source!
---
## Getting started
- To initialize a project: [Spring Initializr](https://start.spring.io/)
	- Or use the built-in initializer in IntelliJ Ultimate.

#### Configuring Spring application properties
- There is an `application.properties` file in the project.
- You can add properties to it like:
	- `logging.level.root=error` to make the application log errors only.
	- `spring.main.banner=off` to turn off the Spring banner upon running the application.
---
## Motivation
![[Complex Dependency Injection]]
- Above is a graph that visualizes dependencies between classes A, B, C, ...
- If we want to initialize an object of class `A` using dependency injection, we will need about this much code:
```Java
B b = new B();
E e = new E();
F f = new F();
D d = new D(e,f); // we need E and F to construct D
G g = new G();
C c = new C(c); // we need G to contruct C
A a = new A(b,c,d)
```
- That's a lot of code. Spring can make this task easier by taking care of dependency injection.
---
## Terminology
- Some Spring terminology before we start:
	- There are **containers** that manage Spring **beans**.
	- We can request an instance of a **bean** from a **container**.
	- The container takes on the task of creating a bean as well as managing its lifecycle.