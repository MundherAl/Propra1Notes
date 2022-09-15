# Maintainability
- Maintainability is a so-called quality goal.
- Usually has nothing to do with functionality but the longterm life and performance of a software.
- About 67% of software costs go to maintainability. This illustrates the importance of maintainable software!
---
## What is maintainability?
- Bug and error removal.
- Implementation of new functions
- Changes in context.

#### Why is it important?
- Repetitive code can be difficult to maintain. If a repeated function needs to be modified, then we will have to modify all other repetitive functions as well. This increases costs.
- Often is the case that small changes can cause big effects. We need to make sure that the structure of software doesn't allow such changes to have a big influence. (Coupling)
---
## Abstraction
- Abstraction helps focus on software behavior rather than implementation details.
- Degrees of abstraction are very practical for software design. If a colleague develops a sorting algorithm for a collaberation, then you can use this algorithm without having to know the implementation details.
---
## Decomposition
- Decomposing software is making it modular.
- This modularity has big advantages for maintainability and collaberations. For example, a team can focus on one module of a project while other work is being done in parallel.
- IHP: Information Hiding Principle. The Idea is to focus on the intersection between modules and not their implementation details. This increases maintainability substaintially.
- In Java, we utilize the visibility modifiers `private` and `protected` to preserve this modularity and `public` to intersect between modules.
- Great example: [Woche 6 – Programmierpraktikum 1 (DE)](http://propra.de/fc3a78ad127672f/#_ein_beispiel_auf_feingranularer_ebene) 
---
## Coupling
- Whenever we commit changes in code, it can potentially affect other parts of a program of they are coupled.
- This means that we should consider where our changes can have effects.
- We call this **Coupling**.
- Coupling happens at the intersection points between two modules.
- The more a module requires internal details and assumptions of another module, the stronger the coupling between them is.
- Therefore we want to minimize this as much as possible, ergo make the intersection as small as possible.
- IHP helps us keep the coupling at a minimum.
- We can use modifiers like `final` to reduce coupling. This comes with a caveat, e.g. Arrays can be `final` but their content is still changable.
- Getters and Setters are helpful but not always!! They may sometimes increase the coupling between client-level and back-end modules.
- Constructors can also have their own issues especially when arrays are passed into them. (arrays are passed by reference!)
- Lesson: don't give the calling class the responsibility to keep consistency. Keep that hidden to decrease coupling.
---
## Law of Demeter
- The Law of Demeter seeks to reduce coupling. Here's how:
	- A method `m()` in class `K` must only have access to:
		- Methods in `K`.
		- Methods of instance variables of `K`.
		- Methods of objects, that `m` gets as parameters.
		- Methods of objects that are initialized in `m`.
		- Careful: if a passed parameter is used to construct an object, we are not allowed to use the methods of the constructed object!
---
## Tell, don't ask
- To keep coupling at a minimum, we try to delegate logic to other modules and we "tell" them to do the logic for us.
- What we want to avoid is asking modules for data and performing the logic ourselves.