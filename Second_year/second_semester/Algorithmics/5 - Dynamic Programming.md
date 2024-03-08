
# Basic concepts

Divide and Conquer is based on divide the original problem to solve a original problem.
It has some drawbacks:
- When the number of subproblems is very high and the complexity is not polynomial
- When generating a number of subproblems that are repeated and therefore are solved several times in the same execution

Improvements of dynamic programming:
 - We can solve each problem and store the solution
 - The idea is to **avoid calculating the same subproblem twice**.

Fibonacci solution for dynamic programming:
```Java
public static int fibonacci_dp(int n){
	int[] f = new int[n+1];
	
	f[0] = 0; f[1] = 1;
	for (int i=2; i<n+1; i++)
		f[i]= f[i-1]+f[i-2];
	return f[n];
}
```

| Divide and Conquer              | Dynamic Programming           |
| ------------------------------- | ----------------------------- |
| Descending technique            | Ascending technique           |
| We start with the whole problem | We start with the subproblems |

# Examples of use

## Combinations

A **combination** is a way of selecting several things out of a larger group, where order does not matter
In smaller cases it is possible to count the number of combinations

$${n\choose{k}} = {n -1 \choose k -1} + {n -1 \choose k} \text{  if 0 < k < n, } {n \choose 0} = {n \choose n} = 1$$
