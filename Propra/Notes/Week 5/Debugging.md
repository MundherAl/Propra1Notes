# Debugging
- Bugs will always happen in programming. Debuggers are a great tool provided with IDEs. They help locate bugs in your programs.
---
## Debugging in IntelliJ
- Set a breakpoint: when using the debugger, your program will run until the breakpoint is reached pause so you can examine the state of the program.
- Look at the debug tool: it lets you look at the callstack and the values of initialized variables.
- Two types of stepping:
	1. Step-into: enters the method that the line is about to execute so you can see what's happening inside it.
	2. Step-over: executes the line without stepping into the method. This is useful when you know that the method is not causing a bug or also for finding out whether the output of the method is causing a problem.
- Debuggers also allow you to set values of scope variables while the debugger is running. This is great for testing different scenarios without having to rewrite code.
---
## How to find bugs
There are 4 types of bugs:
- Syntax and compiler bugs.
- Logical bugs.
- Resource bugs.
- Integration bugs.

### 1. Syntax and compiler bugs
This is the kindest type of bug. When it happens, you'll always know it happened and you will also know where it happened. Read the error message to deal with the bug!

### 2. Logical bugs
When writing code, we often get results that don't match our expectations. This is likely an error in code that we've written ourselves, though in some rare cases it can be an error from a library that we are using. It's almost always safe to assume that the bug is located in domestic code and not in libraries or lower-levels like the JVM or Operating System.

#### How to deal with such bugs?
Reproducibility. It is important to reproduce bugs. If you cannot reproduce the bug, then you cannot prove that it has been repaired.
1. Take note of what **context** the error appears in. 
2. Ask the question "what **should** my program produce?"
3. Examine the **results**.
4. Examine the **assumptions** of the context.
5. Always read the **error message**!

### Problems we face
1. Bugs that are difficult to reproduce.
2. Bugs that happen indeterministically.
3. Heisenbugs, bugs that disappear when you use the debugger.
---
## Bug Diagnosis
The anatomy of a bug:
1. Code runs.
2. Code reaches a defective point.
3. Defective point causes an infection in the code.
4. The infection propagates through the code.
5. We observe unexpected results.
---
## Debugging steps
1. Reproduce the bug.
2. Diagnose the bug.
3. Repair the bug.
4. Reflect so this does not happen in the future.
---
## Scientific Method for Debugging
1. Observe.
2. Formulate a question.
3. Hypothesize.
4. Make a prediction.
5. Observe the experiment and adjust your hypothesis.