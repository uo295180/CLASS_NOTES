# COMPUTATION MODELS AND COMPUTABLE FUNCTIONS

## Concept of Algorithm

- **Loop**: Requires performing an action repeatedly until a condition is satisfied
- **Macro**: Several simpler instructions are needed to execute it
- **If-then-else**: Two or more alternatives with different actions to perform

### Features

- **Finiteness**: The set of instructions is finite
- Existence of **loops**: The only thing that can cause the execution to be infinite
- **Function**: There is a function associated to the algorithm


## Computation Model

It's a mathematical model that allows us to formally characterize the algorithmic solvability of complex problems, and defines a set of allowable operations and their respective costs. It allows to analyze the computational resources required to solve a problem and discuss algorithmic limitations.
Their main features are *basic operations* and *combination rules*. This course covers **while programs** and **turing machines**.
Combination:
- The repeated execution of an algorithmic action is also algorithmic. Termination test must be algorithmic as well
- The sequential execution of a finite number of algorithmic actions is algorithmic

## While Programs

### The Model of While Programs

- **Domain**: Set of **natural numbers**.
- **Variable names**: Finite strings of letters and digits, always starting with an upper case letter
- **Operation symbols**: Used to denote basic operations. The tree basic ones are **succ** (successor function), **pred** (predecessor function), **0** (constant zero function)
- **Relation symbol**: "$\mathbf{\neq}$" ("not equal")
- **Programming symbols**: **:=** (assignment), **;** (semicolon), **begin**, **end**, **while**, **do**, **(**, **)**

#### Statements

- **Basic statements (assignment)**
	- X := 0
	- X := succ(Y)
	- X := pred(Y)
- **While statement**
	- **while X $\neq$ Y do $\delta$**
	- where $\delta$ represents an arbitrary statement
	- X $\neq$ Y is the test, and $\delta$ is the body
- **Compound statements**
	- **begin $\delta_1$; $\delta_2$; ... ; $\delta_n$ end**
	- Where $\delta_i$ are arbitrary statements and n $\geq$ 0

A **while program** is a compound statement we choose to identify as a program but could be used as a compound statement in some other larger program

##### Example

![[Pasted image 20231212170518.png]]


#### Macros

>[!Definition]
>- **Macro-statement**: A label for a while program so it can be used as part of other while programs

##### Examples
###### 1 - Add X to Y and store in Z

- Assign the value of X to Z
``` asm
begin
	Z := succ(X);
	Z := pred(Z);
end
```

- Add the value of Y to Z
```asm
begin
	U := 0;
	while U ≠ Y do
	begin
		Z := succ(Z);
		U := succ(U);
	end
end
```

- Now, combine
```asm
begin
	Z := succ(X);
	Z := pred(Z);
	U := 0;
	while U ≠ Y do
	begin
		Z := succ(Z);
		U := succ(U);
	end
end
```

###### 2 - Bound difference  Z := X ∸ Y

>[!Note]-
>The bound difference between two elements X ∸ Y is:
>- if X $\geq$ Y    ->    X - Y
>- if X < Y    ->    0

```asm
begin
	Z := succ(X);
	Z := pred(Z);
	U := 0;
	while U ≠ Y do
	begin
		Z := pred(Z);
		U := succ(U);
	end
end
```

###### 3 - Z := X * Y

Macros for assignment and addition are allowed
```asm
begin
	Z := 0;
	U := 0;
	while U ≠ Z do
	begin
		Z := Z + X; //Macro for addition 
		U := succ(U);
	end
end
```

Now, we can replace the addition macro by its basic statements
```asm
begin
	Z := 0;
	U := 0;
	while U ≠ Z do
	begin
//------------------------------
		V := 0;
		while V ≠ X do
		begin
			V := succ(V);
			Z := succ(Z);
		end
//------------------------------
		U := succ(U);
	end
end
```

###### 4 - Z := X div Y

The macro for bound difference is allowed

```asm
begin
	W := succ(X);
	Z := 0;
	U := 0;
	while W ≠ U do
	begin
		Z := succ(Z);
		W := W ∸ Y; //Bound difference macro
	end
	Z := pred(Z);
end
```

Replace the macro for bound difference by its basic statements

```asm
begin
	W := succ(X);
	Z := 0;
	U := 0;
	while W ≠ U do
	begin
		Z := succ(Z);
//------------------------------
		V := 0;
		while V ≠ Y do
		begin
			W := pred(W);
			V := succ(V);
		end
//------------------------------
	end
	Z := pred(Z);
end
```

###### 5 - Z := X mod Y

The module is the reminder of a division. That is, the last value we get on the bound difference operation after we obtain the zero. 
```asm
begin
	W := succ(X);
	Z := 0;
	U := 0;
	while W ≠ U do
	begin
		Z := W; //Macro for assignment
		W := W ∸ Y; //Macro for bound difference
	end
	Z := pred(Z);
end
```

Now, if we want to replace the macros by their basic statements:
```asm
begin
	W := succ(X);
	Z := 0;
	U := 0;
	while W ≠ U do
	begin
//------------------------------
		Z := succ(W);
		Z := pred(Z);
//------------------------------
			V := 0;
			while V ≠ Y do
			begin
				W := pred(W);
				V := succ(V);
			end
//------------------------------
	end
	Z := pred(Z);
end
```

#### Macro-test

The only test allowed in while statements is X $\neq$ Y
**Inductive definition: Macro-test**
- Basic: **X < Y**
- Inductive: Let $\mathbf{T_{1}}, \mathbf{T_{2}}$ be tests
	- $\mathbf{T_{1}} \wedge \mathbf{T_{2}}$
	- $\mathbf{T_{1}} \vee \mathbf{T_{2}}$
	- $\mathbf{\neg T_{i}}$   **i=1, 2**
	Are all Macro-tests as well

**Proposition**: A statement taking the form:
$$\text{while T do } \delta$$
where $\delta$ is an arbitrary statement and *T* is a test different from **X $\neq$ Y** is a **macro-statement**. Assuming that *T* does not involve any natural number, there's an arithmetical expression $E_{T}$ in terms of the variables used in *T* and the operators \*, + and ∸ such that:
$$E_{T} = \left\{ \begin{array}{rcl}
>0 & \text{\emph{if T is true}} \\ 0 & \text{\emph{otherwise}}
\end{array}\right.$$
```asm
begin
	U := E_{T};
	V := 0;
	while U ≠ V do
	begin
		\delta;
		U := E_{T};
	end
end	
```

To build an expression for **any arbitrary test *T*** we can use the inductive definition of Macro-test

- **Base case:**
	- $T = X < Y$                              $E_{T} = (Y ∸ X)$

- **Inductive case:**
	-  $T =T_{1} \wedge T_{2}$                            $E_{T} = E_{T_{1}} * E_{T_{2}}$
	-  $T =T_{1} \vee T_{2}$                            $E_{T} = E_{T_{1}} + E_{T_{2}}$
	-  $T =\neg T_{1}$                                 $E_{T} = 1 ∸E_{T_{1}}$


##### Examples
###### Build $E_{T}$ for T = ($Z \geq Y$) $\vee$ (Z > X)
$$E_{(Z\geq Y)} = E_{Z \geq Y} + E_{Z>X} = E_{\neg (Z<Y)} + E_{X<Z} = (1 ∸ E_{Z<Y}) + E_{X<Z} = \mathbf{(1∸(Y∸Z)) + (Z∸X)}$$
###### Build $E_{T}$ for T = (X = Y)
$$E_{X=Y} = E_{(X \leq Y)\wedge (X \geq Y)} = E_{X \leq Y} * E_{X \geq Y} = $$$$=E_{\neg(X>Y)}*E_{\neg(X<Y)} =(1 ∸ E_{Y<X}) * (1 ∸ E_{X<Y}) = \mathbf{(1∸(X∸Y)) * (1∸(Y∸X))}$$
#### Structured statements

A **proposition** is a **structured statement** with form:
	//////////
	**if** *T* **then**
		$\delta$;
	/////////
	**if** *T* **then**
		$\delta_{1}$;
	**else**
		$\delta_{2}$;
	/////////
	**repeat**
		$\delta$;
	**until** *T*
Where **T** is a test and $\delta$, $\delta_{1}$ and $\delta_{2}$ are statements, is a **macro-statement**

### While Computable Functions

#### Definition

- **K-variable Statement (Program):** A **statement** $\delta$ is **k-variable**, if it uses a subset of the {$X_{1}$, $X_{2}$, .... , $X_{n}$} variables.
- **State vector:** A **state of computation vector** for a k-variable While Program is a vector
$$\hat{a} = (a_{1}\text{, ... , }a_{k}) \in N^k$$
in which $a_{i}$ is the content of variable $X_{i}$. If the program **has k variables**, its **state** of computation vector will always have **k components**.

#### Computation sequence

Given a k-variable program P, a **computation sequence** by P is a sequence of the form:
$$\hat{a}_{0} A_{1} \hat{a}_{1} A_{2} \hat{a}_{2}\text{ ...}$$
with $\hat{a_{i}}$ state vectors and $A_{j}$ instructions of P. An instruction can be a basic statement or a test.
$\hat{a_{0}}$ is the **initial state vector**. If the computation sequence is finite, it is 
$$\hat{a}_{0} A_{1} \hat{a}_{1} A_{2} \hat{a}_{2}\text{ ... } \hat{a}_{(n-1)} A_{n} \hat{a}_{n}$$
where **n** is its **length** an $\hat{a}_n$ is the **final state vector**

#### Semantic Function

A computation sequence is a trace of a program. Input and initialization of the rest of the variables will be stored in the initial state vector. If the sequence is finite, the final state vector will contain the values of all the variables, including the output. 
We can define a function that associates each input to its corresponding output once the program is executed.

The **j-ary semantic function**, $\varphi_{p}^j$: $N^j \rightarrow N$  (j>0) for a **k-** variable while program **P** is defined as follows:
- Given an input vector $\hat{a} = (a_{1}\text{, ... , }a_{j})\text{, }\varphi_{p}^j(a_{1}\text{, ... , }a_{j})$ is evaluated according to the following rules:
	
	- **k $\geq$ j:** $\varphi_{P}^j(a_{1}\text{, ... , }a_{j})$ is obtained by applying **P** to the initial state vector  $\hat{a}_{0} = (a_{1}\text{, ... , }a_{j}\text{ 0, 0, ..}.^{(k-j)}\text{ ... , 0})$
	
	- **k < j:** $\varphi_{P}^j(a_{1}\text{, ... , }a_{j})$ is obtained by applying **P** to the initial state vector $\hat{a}_{0} = (a_{1}\text{, ... , }a_{k})$

- If and when **P** halts on this vector, the final value of **X1** is the value corresponding to $\varphi_{P}^j(a_{1}\text{,, ... , }a_{j})$

- Otherwise, $\varphi_{P}^j(a_{1}\text{,, ... , }a_{j}) = \perp$ (indetermined)