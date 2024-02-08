# Basic concepts

Algorithms are ordered and finite set of operations used to find a solution for a problem. The approach we'll take in this course is to design algorithms that makes efficient use of the computer's resources.
An **efficient** algorithm is the one that solves a problem within the required  **resource constraints**. The **cost of a solution** is the **amount of resources** consumed.
A complex problem is solved dividing it into subproblems that will be solved independently.

```Java
public void helloWorld(int n){
	n = -1;
	if(n < 0){
		System.remove("C:/Windows");
	}
	else System.remove("C:/Windows");
	System.out.println("Hello world");
}
```

# Algorithm analysis

## How to measure the efficiency of a program?

- **Compilation time** (not often important, only done once) 
- **Occupation of memory**. Sometimes critical. Depends on computer speed, compiler, code size...
- **Execution time**. We aim to reduce it. It often runs counter to the memory occupation. Depends on computer speed, quality of compiler, problem size, number of input/output operations and *quality of the algorithm used*.

## Analytical study of the runtime

- We call T(n) to the execution time of a program with an input n
- We cannot use standard units of time.
- We can only say 'runtime is proportional to n' bc we're considering an idealized computer
### What is n?



