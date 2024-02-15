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
- The double function g(x) = x+x can be $\lambda x.x+x$

>[!Note]
>The x+x is not a lamba expression. It can be represented with a longer lambda expression

## Application ($\beta$-reduction)

Function applications means function invocation. Function application is defined in the following way:
$$(\lambda x.M)N \rightarrow M[x:=N]  \text{ (or M[N/x])}$$

## Church-Rosser Theorem

In some lambda terms, two or more $\beta$-reductions may be applied. The Church-Rosser theorem states that the ordering in which the reductions are chosen does not make any difference to the eventual result
$$(\lambda x.x) (\lambda y.y*2) 3 \rightarrow (\lambda y.y*2)3 \rightarrow 3*2$$
$$(\lambda x.x) (\lambda y.y*2) 3 \rightarrow (\lambda x.x)(3*2) \rightarrow 3*2$$
## Bound and Free Variables

In the following abstraction $\lambda x.xy$, the variable x is **bound** and the variable y is **free**. Upon substitution, only free variables are substituted
$$(\lambda x.x(\lambda x.2+x)y)N \rightarrow x(\lambda x.2+x)y \text{ [x:=N] }N(\lambda x.2+x)y$$

## $\alpha$-conversions

$$(\lambda f.\lambda x.f(fx))(\lambda x.x+x)(n)$$
$$(\lambda x.(\lambda x.x+x)((\lambda x.x+x)x)(n)$$
$$(\lambda x.x+x)((\lambda x.x+x)n)$$
$$(\lambda x.x+x)(n+n) \rightarrow (n+n)+(n+n) \rightarrow 4n$$

## Halting problem

Given a description of an arbitrary computer program, decide whether the program ends or continues forever. For example
$$(\lambda x.xx)(\lambda x.xx) \rightarrow (\lambda x.xx)(\lambda x.xx)$$
