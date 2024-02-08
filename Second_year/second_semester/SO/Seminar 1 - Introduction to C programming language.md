
# Structure of a C program

C is an imperative procedural language. It's a set of functions with one *main* function
- Compilations and execution
```Shell
$ cc hello.c -o hello
$ ./hello
Hello World
$
```

![[Pasted image 20240201151210.png]]

# Functions

- Global variables are accessible from any function, but local variables can only be accessed from inside the function where it's declared
- C provides modularization: cleaner code and code reuse
- By default, all the parameters are passed by value. If we need to use a parameter to return a value, a pointer must be used
- & address operator, \* dereference operator

# Data types

- Integer types (signed or unsigned):
	- char: 1 byte
	- int: 4 bytes in Ritchie
	- short: 2 bytes in Ritchie
	- long: 8 bytes in Ritchie
- Floating point types:
	- float: 4 bytes in Ritchie
	- double: 8 bytes in Ritchie
- No boolean type. A integer type is used instead
	- 0 $\rightarrow$ false
	- != 0  $\rightarrow$ true
- Arrays
	- If we use the sizeof() function over an integer array with 10 slots we will obtain 40 as output (10 slots * 4 bytes for each slot)
	- To know the real size of an array a we need to do is 
	```c
	sizeof(a)/sizeof(a[0]) 
	```
- Strings
	- They doesn't exist
	- Instead, arrays of chars are used. They need to end with \\0 
	- Strings can be manipulated using the string library
	- Space for strings must be allocated before using it
	- Formating string:  Text to be displayed containing special markers where values of parameters will be filled:
		- %d for decimal int
		- %c for char
		- %f for float
		- %s for string
	```c
	printf("The %d char in %s is %c\n",3,s1,s1[3]);
```
- Enums
	- If one variable needs some specific value, an enum can be used. Internally, an integer value is assigned to each element of the array. We can also use our own values
```c
enum INT_BITS {SYSCALL_BIT=2, CLOCKINT_BIT=9, EXCEPTION_BIT=6};
```
- Structs
	- Is like a new "concept". It has a set of several variables grouped under the same name.
	- A struct cannot have methods. Is like an autistic object 
	```c
	struct date{
		int day;
		int month;
		int year;
		char *monthName;
	};
	struct date d1 = {1,1,2019,"January"};
	struct date d2;
	d2=d1; d2.day=5;
```
- Type data alternative names
	- With *typedef* we can define new types of data
```c
typedef unsigned char boolean;
boolean myBool;
typedef struct date date;
date d1, d2;
typedef long myInt;
myInt i
```
The usage of typedef gives the advantage of avoiding portability problems and cleaner code 

# Preporcessor

They're commands to do something before executing the program
- Include command
	- To include standard libraries
		\#include <stdio.h>
	- To include custom libraries/files
		\#include "processor.h"
- Constant definition
		\#define INTERRUPT_TYPES 10
- Conditional compilation
		\#ifndef PROCESSOR_H
		\#define
		...
		\#endif

# Programs with multiple files

To organize the code, programs can be divided in modules, stored in two different files:
- **Header file** (\*.h): contains function prototypes and global variables/types definition (Interface)
- **File itself** (\*.c): contains the implementation of the functions, local module variable definition
- To compile, all the c files must be compiled and then linked together. Utilities like make automate this process
