# Code Smells
- Code is supposed to be written in a comprehendable way. Other programmers should not struggle with understanding your code and code should minimize coupling.
---
## 1. Mysterious Name
- It's important to pick sensible names for variables and functions. Example:
	- `int d` is not good.
	- `int numberOfDays` is better!
	- `int numberOfDaysSinceLastLogin` is very specific but far too long.
	- `int daysSinceLogin` is much better!
- Names should not lie! Example:
	- `static void matrixInverter()` should invert a matrix and not do anything else.
- Names should have minimal context! We can leave out words like `Processor` or `setOf` because they don't contribute to understanding.
- Konventions:
	- Interfaces often end with "able" like `iterable`.
	- Constants are written in upper-case like `PI`.
---
## Comments
- Commenting code may seem like a good practice and it often is. But it can sometimes be a code smell.
- Better than writing comments is writing easy and readable code that doesn't require explaining.
---
## Methods
- Long methods are a smell. The longer the code is, the more tasks it tends to do. We want to isolate the tasks in as many methods as possible to reduce duplicates and increase usability.
- Methods should minimize the number of paramters they get when possible. For example: Getting the distance between two points in a 3D space requires 6 parameters that are numerical. We can instead create a Point object and use two points as parameters for our method. This reduces the number of parameters from 6 to 2 and increases readability.
- Booleans are usually a smell too. Avoid using if-else statements and try to fulfill the conditions using other methods. Or split the method that intends on using booleans into two methods.
- SLAP: Single Layer of Abstraction Principle. A method should be as abstract as possible. For example: A method `printReceipt()` should only print receipts and not create receipts then print them.
---
## DRY
- Don't repeat yourself. Avoid duplicates in your code.
