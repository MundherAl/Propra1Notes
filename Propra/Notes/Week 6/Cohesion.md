# Cohesion
- Cohesion refers to the degree in which elements inside a module belong together.
- Sort of like the strength of relationship between data and methods inside a class.
- We try to follow the principle of LCHC (Low Coupling High Cohesion). We know why we want low coupling but why do we desire high cohesion?
---
## Advantages of high cohesion
- Module complexity is lowered because it has fewer operations.
- Increases maintainability. Local changes in one module affects less modules.
- Increased usability. Developers will more easily find the component of a module that they need because they grouped together sensibly.
---
## How do I increase cohesion?
- By increasing what methods inside a class have in common. (e.g. constants)
- By keeping a module small with related methods.
- Grouping related methods together.
---
## SRP (Single Responsibility Principle)
- A project becomes more cohesive when classes have less reponsibilities. The SRP tells us, that every class should have one responsibility.
- Great example: [Woche 6 – Programmierpraktikum 1 (propra.de)](http://propra.de/fc3a78ad127672f/#_koh%C3%A4sion)
