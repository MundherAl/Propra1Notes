# Over-specification
- If we were to choose the top 3 problems in testing, over-specification would be number one.
```ad-question
It's pop quiz time! Which of the following assertions are more interesting to us?
```
```Java
\\ a)
assertThat(employee.getHolidays().size()).isEqualTo(3);

\\ b)
assertThat(employee.getHolidayHours()).isEqualTo(3*8);
```

- Answer: b.
- You might argue that both options test behavior that is interesting to us.
- But notice that option "a" depends on how we implement the employee class.
- Option "b" is less dependent on implementation details and can test behavior better.

When writing tests, always ask the following two questions:
- What behavior is my program supposed to have?
- How can I test this behavior with minimal knowledge of implementation details?