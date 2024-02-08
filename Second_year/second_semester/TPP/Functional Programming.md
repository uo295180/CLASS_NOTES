# Functional Paradigm

**Declarative** paradigm that abstracts programs as mathematical **functions** computing **immutable data**.
- Data is never modified
- Instead of modifying data, a function is called returning the new data without modifying the original one
A **program** is defined as a set of functions invoking one another
Opposite to imperative programming, functions can **never** have **side effects**. The value of a function only depends on the value of its parameters

# Lambda Calculus

Is a formal system based on **function definition** (abstraction) and its **application** (invocation). It makes extensive use of recursion. 
It's considered as the **smallest universal programming language**

## Lambda Expressions

A lambda **abstraction** $\lambda$x.M (M, N, ...) where x is a variable, (x, y, z, ...) a parameter and M is a lambda expression (function body)
An application M N where both M and N are lambda expressions

Examples:
- The function f(x) = x can be $\lambda x.x$
