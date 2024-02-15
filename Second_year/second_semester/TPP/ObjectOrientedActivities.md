# Prev Lab 1

## Comments

- They can be written in **XML**. Visual Studio can generate XML files. 
- **NDoc** is able to take the XML file and generate other types of  files like HTML or LaTeX

```C#
namespace TPP.ObjectOrientation.Basic {
	/// <summary>
	/// First C# class
	/// </summary>
		class Hello {
		/// <summary>
		/// Main entry point
		/// </summary>
		public static void Main() {
		// * Shows “Hello World" in the console
		System.Console.WriteLine("Hello World");
		}
		}
}
```

## Assemblies 

- It's a merge collection of application resources (*.exe, .dll, .ini...*). They're not packed into a single file
- Reusable implementation unit
- The **Assembly Linker** (*AL.exe*) tool facilitate the creation of assemblies. Each project represents an assembly.
- An assembly has a collection of at least one **module** (*.exe, .dll* managed file)

## Namespaces

- Is a categorization mechanism for grouping types related to a particular functionality. It does not provide any *information hiding* feature. They're not physical and they can be also *nested*
- To directly use **types** in a namespace, the **using** keyword is used at the beginning of a C# file

## Class Access Control

- A C# class can be either **public** or **internal** 
- An **internal** can only be accessed from within their *assembly*. Then those classes used for implementation purposes that're not part of the assembly facade must be **internal**.

## Modularity in OO Languages

Comparing C# **namespaces** with Java **packages**. Focused on three main elements:
- Logical grouping
- Physical grouping
- Information hiding

### C# vs. Java

- C# **namespaces** provide
	- **Logical** grouping of types (avoids name collision)
	- **.Net** assemblies used for **physical** code reutilization
	- No information hiding level is provided for namespace control access

- **Java packages** provide
	- **Logical** and **physical** (.class, .jar and .zip files in a directory described in the classpath) grouping of types
	- Information hiding levels to control access to members and types from outside the package

![[Pasted image 20240123223531.png]]

### Modularity in C# 

A namespace is defined between brackets ( namespace whatever{  -  } ). Instead of specifying the full name of a namespace, the **using** is used (**using** System;). This type access control is a great mechanism to achieve **loose coupling**.

![[Pasted image 20240123224611.png]]

### Member access control

There're the information hiding levels for the members of a class (not the class itself, but all the atributes or methods that this class contains). This levels are:
- **public**: Accessible from everywhere
- **private**: Only accessible from within that class (Default access control)
- **protected**: Accessible from within that class or any derived class
- **internal**: Only accessible from within that assembly
- **protected internal**: Accessible from within that assemble or any derived class in another assembly

![[Pasted image 20240123225156.png]]

### Entry point

In C# only one entry point can be defined for each program. This will be a **static** class method called **Main** and:
- The return type could be **void** or **int**
- It could be declared with any information hiding level
- It must have either no parameters or a single **String[ ]**  parameter. This parameter will hold the arguments passed in the command line


## Grammar
### Built-in Types

| Type | Bytes | Description |
| ---- | ---- | ---- |
| *byte* | 1 | Unsigned bytes (from 0 to 255) |
| *char* | 2 | Unicode characters |
| *bool* | 1 | *true* or *false* |
| *sbyte* | 1 | Signed bytes (from -128 to 127) |
| *short* | 2 | 2 bytes signed values (from -32,768 to 32,767) |
| *ushort* | 2 | 2 bytes of unsigned values (from 0 to 65,535) |
| *int* | 4 | 4 bytes integer values (from -2,147,483,648 to 2,147,483,647) |
| *uint* | 4 | 4 bytes unsigned values (from 0 to 4,294,967,295) |
| *float* | 4 | Single precision real numbers (from +/-1.5 * 10-45 to +/-3.4 *<br>1038 with 7-digit mantissa) |
| *double* | 8 | Double precision real numbers (from +/-5.0 * 10-324 to +/-1.8<br>* 10308 with 15-16-digit mantissa) |
| *decimal* | 16 | Fixed 28-digit precision used for financial calculations |
| *long* | 8 | Signed  integers with double precision |
| *ulong* | 8 | Unsigned integers with double precision  |
- Implicit conversions (promotion) when no information is lost
- Explicit conversions by means of **casts** (Same syntax as in Java and C++)

### Constants and Console

 - The reserved word **const** in a variable means that the value stored in that variable cannot be modified.
 - Strings literals are written between " " and characters between ' '
 - **System.Console** offers access to the console and **Write** and **WriteLine** writes text with format
 
### Enumerations

They're a finite set of constant values that represent **a new type** with his own hiding level. Integers can be assigned too to each value

```C#
enum Colors{
	blue, green=3, red, yellow
}
class Enumeration{
	static void Main(String[] args){
		Colors color;
		color = Colors.blue;
		Console.WriteLine(color); // blue
		color = (Colors) 3;
		Console.WriteLine(color); // green
	}
}
```

### Operators

| Type | Symbols |
| ---- | ---- |
| Arithmetic | +,   -,   *,   /,   % |
| Booleans | &&,   \|\|,   ! |
| Comparison | ==,    !=,   >=,   <=,   <,   > |
| Bitwise | &,   \|,   ^,   ~,   >>,   << |
| Assignment | =,   +=,   -=,   *=,   /=,   %=,   &=,   \|=,   ^=,   <<=,   >>= |
| Increment and Decrement | ++,   --       (prefix and postfix) |
| Conditional ternary operator | ?: |
The **+** operator with strings means concatenation. [More operators](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/)

### If, While and DoWhile

- If:
	***if** (expression) statement1
	**else** statement2*
	- Expression must be **bool**
	- Statements are single instructions or a collection of instructions between { brackets }
	
-  While
	***while** (expression) statement*
	- Expression must be **bool**
	- Statement can be a block

- Do-while
	***do** statement **while** expression*
	- Expression must be **bool**
	- Statement can be a block

### For

```C#
for([initialization]; [expression]; [iterations]){
	statement;
}
```

- ***initializations*** are coma-separated declarations or statements
- ***expression*** must be **bool** 
- ***iterations*** are a collection of comma-separated statements
- ***statement*** can be a block
- In wile, do-while and for loops, **break** and **continue** can be used

### Switch

```C#
switch(expression){
	case literal:
		[statement*
		jump-statement]
	[default: statement*]
}
```

- Expression could be any integer, character or string type
- The type of ***literal*** must be equal (or promote) to the type of ***expression***
- ***jump-statement*** could be either
	- **break**
	- **goto case *literal***
- Once a jump statement is used, it is mandatory in every case

```C#
switch (args[0]) {
	case "Democrat":
		Console.WriteLine("You voted Democratic.\n");
		break;
	case "Liberal Republican":  // * Continues
	case "Republican":
		Console.WriteLine("You voted Republican.\n");
		break;
	case "New Left":
		Console.WriteLine("NewLeft is now Progressive");
		goto case "Progressive";
	case "Progressive":
		Console.WriteLine("You voted Progressive.\n");
		break;
	case "Libertarian":
		Console.WriteLine("Libertarians are voting Republican");
		goto case "Republican";
	default:
		Console.WriteLine("You have voted for an invalid party.\n");
		break;
}
```


## Constructors and Destructors

### Constructors

- A **constructor** defines the initialization of an instance of an object. It's implicitly called just **after** its construction
- It's a method that haves the same name as the class name and with no return type declared
- **By default** the compiler provides a default constructor without any parameters
- The default initialization if this constructor is called is **0** for numerical values and enums, **false** for Boolean values, **'\0'** for characters and **null** for references
### Destructor

- A **destructor** defines the cleaning up of the additional resources used by the object. It's implicitly called **before** its destruction
- It's a method with the same name as the class but starting with ~, with no return type declared and without any access control level specified

```C#
class MyClass{
	public MyClass(parameters){
		// Constructor
		assignmet o additional resources
	}
	~MyClass(){
		// Destructor 
		release of additional resources
	}
}
```

C# ensures the execution of the destructor before its destruction, but it's not deterministic (we don't know exactly when). The garbage collector executes the object destructor before it's been collected

## Objects

They're accessed by reference. Within an instance method the **this** reference points to the implicit object. They're created with the **new** operator. **Messages** can be passed to an object using the **dot (.)**, like *object.message()*.

## Partial classes

Some classes have a lot of members, that can be grouped into different categories. It's interesting to **separate them** into different files. 
In order to do this, C# offers the **partial classes**:
- They can be **implemented in different files**
- The **partial** keyword should be written before the class keyword

## Static

Class members should be declared as **static**, and they're accessed through a class reference. In C#, we cannot access a class member using object references.
C# offers **static** constructors, executed whenever a class is loaded into memory and used as an initialization mechanism

## Utility Classes

They're classes with all methods **static** and a private constructor. C# offers **static** classes. In this classes instance fields, properties, methods and constructors are not allowed. 

## Properties

C# offers **properties** as a flexible mechanism to access the abstract state of objects, having the benefit of **encapsulation**. The object state is hidden and its implementation can be changed without changing its use. This leads to reach **maintainability**.

Properties can **read** and/or **write** the object state and they can be:
- Declared with all the information hiding levels
- Be static
- Be abstract
- Be overridden

Properties facilitate the **object construction**. For example, is a **Person** implements a constructor without parameters and provides the modifiable **FirstName**, **Surname**, **Age**, and **IDNumber** properties, its instances can be constructed with any combination of any number of the previous 4 properties, in any order and avoid extensive constructor overload.

```C#
class Person{
	string FirstName {get; set;}
	string Surname {get; set;}
	int Age {get; set;}
	string IDNumber {get; set;}
	static void Main(){
		Person mary = new Person {
			FirstName = "Mary",
			Surname = "Smith",
			Age = 43,
			IDNumber = "31651692-D"
		};
		Person jhon = new Person {
			Surname = "Doe", Age = 10, FirstName = "Jhon" };
	}
}
```

## Strings
**string** is an alias of **System.String**, and therefore:
- string (and String) is a class
- Its instances are objects
- Variables of this type are references
The **+** operator means concatenation when applied to strings. Strings are also immutable, so the usage of **StringBuilder** is needed whenever we require to mutate a string

# Prev Lab 2

## Arrays

They're a mechanism to collect values of the same type. They're objects, so a reference is needed. Therefore, a reference of an array of *T* is declared as *T[] reference;*.
They're created using the **new** operator and determining a fixed array size.
```C#
int[] intValuesArray = new int[10];
bool[] boolValuesArray = new bool[2];
Angle[] angleValuesArray = new Angle[91];
```

After the construction of the array, the values that will be stored inside (without having added yet, just by default) are the following ones:
- **0** for numerical values and enumerations
- **false** for Boolean values
- **'\0'** for characters
- **null** for references

C# allows initializing arrays upon creation, by separating the stored values by a comma
```C#
char[] digits = {'0', '1', '2', '3', '4', '5', '6', '7', '8', '9'};
int[] integers = {2, 3, 234, -234, 43};
bool[] booleans = {true, false};
Angle[] angles = {new Angle(0), new Angle(90), new Angle(180)};

// or also

Angle[] angles2 = new Angle[] (new Angle(0), new Angle(90), new Angle(180));
```

.Net arrays provides the read-only **Length** property. It contains the size of the array. It should be used while looping through the array. It also provides the for-each loop, called the **Length loop**:
```C#
for(int i = 0; i < angles.Length; i++){
	Console.WriteLine(angles[i]);
}
foreach(Angle angle in angles){
	Console.WriteLine(angle);
}
```
It does not allow modifying the array

## Multidimensional Arrays

Two ways:
- **"Lineal" arrays**: Elements are saved in one contiguous memory block
	- More efficient, less versatile
	- **Length** is the product of all sizes
	- The length for each dimension is obtained with **GetLength**
```C#
string[,] vector = new string[3,4];
for(int i = 0; i < vector.GetLength(0); i++)
	for(int j = 0; j < vector.GetLength(1); j++)
		vector[i,j]="("+(i+1)+","+(j+1)+")";
```
- **Arrays of Arrays**: Allows irregular arrays
```C#
int[][] triangular = new int[10][];
for(int i=0; i<triangular.Length;i++)
	triangular[i] = new int[triangular.Length-i];
```

## Structs

They're an efficient way to represent lightweight objects. They can implement constructors, properties, methods, fields, operators and class (static) members
They don't support inheritance but they implicitly derive from **ValueType**.
They can implement interfaces but they cannot implement destructors. The default information hiding level for their methods is public.
They're stored in the stack. Created to transfer data and avoid garbage collector overload.

## Parameter Passing

Three possible parameter passing mechanisms
- **By value** (default)
	Formal parameter is a copy of the argument. When passing objects, what is copied is the reference.
- **By reference** (in and out)
	Formal parameter is an alias for the argument. A value is passed (in) and it can be modified within the method, implying a change of the actual value (out). The **ref** keyword should be written before the formal and the actual parameters
- **By reference** (out)
	Formal parameter is an alias for the argument. No value is passed, as the purpose is to modify its value within the method. The **out** keyword should be written before the formal and the actual parameters

## Named and Optional Arguments

**Optional arguments** allows omitting arguments for some parameters

# Prev Lab 3

## Abstract classes and Methods

When we need a class to provide a method but this method cannot be implemented, we declare it as **abstract**. In C\#, the **abstract** keyword is provided, and the method is not implemented. This abstract method should be overridden and it cannot be declared as **virtual**. The class containing this abstract methods should be declared as **abstract class**.

## Interfaces

Sometimes we need a type to be a subtype of two or more supertypes, but C\# does not provide multiple inheritance, so we aim to achieve multiple polymorphism. An interface can be defined as the class containing the set of messages provided to the user. In C\# this concept is offered as a type.
Interfaces provide **multiple subtyping**. Therefore, a class or interface may derive from one or more interfaces

```C#
[public|internal|] interface name [: base-interfaces]{
	message-declaratios
}
```

By convention, interface identifiers starts by I. Also, interfaces cannot have class (**static**) members

### IDisposable

It's an interface in the System namespace with just one ***Dispose*** method. It's responsible of releasing the additional resources managed by the object. Every *.Net* class that manages additional resources should implement this interface.
Commonly, a class that defines a destructor also implements IDisposable, where dispose is called by the destructor.

```C#
class File : IDisposable{

	private string fileName;
	private bool isOpen;
		
	public File(string fileName){
		this.fileName = fileName;
		this.isOpen = true;
		Console.WriteLine("Opening the {0} file", fileName);
	}

	public void Dispose(){
		if(this.isOpen){
			this.isOpen = false;
			Console.WriteLine("Closing the {0} file.", fileName);
		}
	}
	~File(){ this.Dispose(); }
}
```

As the programmer may forget invoking Dispose, C\# provides the **using** keyword (kind of a **try-catch with resources** in Java). Therefore, the call to Dispose is ensured.

```C#
using(File file = new File("input.txt")){
	string line = file.ReadLine();
	// Throws an exception (division by zero)
	file.WriteLine(line + line.Length/"".Length);
} // The file is closed (Dispose is invoked)
```

### Explicit interface implementation

Considering the following scenario:
```C#
interface I1 { void m(); }
interface I2 { void m(); }
class C : I1, I2 {...}
```

And the programmer wants to provide different implementation to I1.m and I2.m. That's possible in C\# due to the **explicit** interface implementation syntax

```C#
class C : I1, I2 {
	public void I1.m() {/* I1.m implementation*/}
	public void I2.m() {/* I2.m implementation*/}
}
```

[Mandatory activity](https://www.artima.com/articles/composition-versus-inheritance)

## Exceptions

**Exceptions** are objects holding essential information about an exceptional situation occurred at runtime. In C\#, they must be **System.Exception**. Structs cannot be thrown. 
Application specific exceptions should derive from **System.ApplicationException** and they do not represent fatal application errors.
The **System.SystemException** class is used to differentiate between exceptions defined by the system versus exceptions defined by applications.

### Throwing Exceptions (C\#)

They're raised with the **throw** keyword, followed by an **Exception** instance. C# methods does not specify the exceptions they may throw. Therefore, in C# it's not mandatory to handle any exception.

### Handling Exceptions

They're handled with **try** and **catch** blocks:
- **try** block: Code may throw an exception
- **catch** block: Exception handling code. There could be many **catch** blocks for one **try** block
- **finally** block is always executed
	- When no exception is thrown
	- When the exception thrown is handled in a **catch** block
	- When the exception thrown is not handled

### Handling Any Exception

C# provides **parameterless catch** blocks (like C++), so that any exception is handled. It also provides **parameterless throw** to re-throw caught exceptions.
```C#
public static void m(string s){
	switch(s) {
		case "1": throw new Exception(s);
		case "2": throw new ApplicationException(s);
		case "3": throw new SystemException(s);
	}
}

public static void Main(string[] args){
	try { m(args[0]); }
	catch {
		Console.Error.WriteLine("We handle and re-throw it");
		throw;
	}
}
```

### Unhandled Exceptions

In .Net, an unhandled exception shows in the standard error output:
- The type of exception thrown
- It **Message** property
- Its **StackTrace** property

## Cleaning up resources in C\#

The following C# program
```C#
private void Process(TextWriter file){
	// Method that process a file
	file.Write("hello"); // no flush
	// .... an exception can be thrown
	throw new Exception();
}
private void Resources(string fileName){
	TextWriter file = new StreamWriter(filename);
	// * The file is processed
	Process(file);
	file.Close();
}
private void run() {
	try {
		Resources("wrongManagement.txt");
	} catch (Exception){
		Console.Error.WriteLine("Exception handled.");
	}
}
```

This code does not clean up the resources allocated (the file is not closed). The exception can be handled in the following way:

```C#
private void NonMaintainable(String fileName){
	TextWriter file = new StreamWriter(fileName);
	// * The file is processed
	try{
		Process(file);
	}
	catch(Exception e) {
		file.Close();
		throw e;
	}
	file.Close(); // * Repeated code
}
```

But the file must be closed in every single **catch**. This solution is not very maintainable. 
For this reason, the **finally** was added:

```C#
private void Maintainable(String fileName) {
	TextWriter file = new StreamWriter(fileName);
	// * The file is processed
	try{
		Process(file);
	} 
	finally{
		// * Resources are cleaned up only here
		file.Close();
	}
}
```

Although C# provides destructors that might be used to clean up resources in come occasions (sometimes we need a deterministic cleaning up, so destructors are not a suitable mechanism in these cases)

## Assertions in C\#

They're conditions that must be true in the correct execution of a program
- In case they're false, it's due to a **programming error**
- They're only used in the **development cycle**
- They should be **transparently removed in the release version**
**Conditional compilation** is a widespread technique used to provide assertions

```C#
#if DEBUG
	Console.WriteLine("Debug mode");
#else
	Console.WriteLine("Release mode");
#endif
```

## Assertions in .Net

They're provided by the **Debug** class in the **System.Diagnostics** namespace

```C#
Assert(bool, [string message, [string detailedMessage]])
```

It uses conditional compilation, so if the **DEBUG** macro is not defined, the assert code is not compiled

## Preconditions in .Net

Preconditions can be grouped into one of the following types:
- The **argument values** are not appropriate
- The method invoked cannot be executed in the current **state of the object** (this)
For this cases, C\# provides the following exceptions in the **System** namespace
- **ArgumentException** for the argument preconditions
- **InvalidOperationException** for the object state preconditions

## Programming by contract: Pre/Postconditions and invariants

```C#
public void AddUser(string userName, string plainPassword, UserData data) {
	// INAVARIANT: Always at the beginning of a method (except constructors). Is object consistent?
	Invariant();
	int previousUserCount = GetUserCount();
	
	// PRECONDITIONS are not always wrong parameters: object can be in an invalid state. InvalidOperationException is used
	if(UserFileIsLocked()) 
		throw new InvalidOperationException("The file is temporally inaccessible");
		
	// If arguments have incorrect value, ArgumentException is used
	if(!validUserName(userName))
		throw new ArgumentException("User name is invalid: please use a non-existing, non-null user name");
		
	if (plainPassword.Length < 10)
		throw new ArgumentException("The password size must be at least 10");
		
	if (!PasswordWithEnoughComplexity(plainPassword))
		throw new ArgumentException("Password must have at least one upper and lowercase char, number and symbol");
		
	if (data == null)
		throw new ArgumentException(("Extra user data cannot be null");
	
	//TIP: We can create our own exceptions (inheriting from the Exception class) for this, but normally 
	//ArgumentException and InvalidOpeationException are enough for most cases
	
	//Do the work: add user name and data, encrypting the password
	_AddUser(userName, plainPassword, data);
	
	//POSTCONDITION of this method (invariants are object-scoped, postconditions are method-scoped)
	Debug.Assert(GetUserCount() == previousUserCount + 1);
	
	//INVARIANT check: Also, always end of a method (leave object consistent)
	Invariant();
}

private void Invariant(){
	//User file cannot get corrupt during the whole execution
	Debug.Assert(CheckUserFileIntegrity());
}
```


# Prev Lab 4

## Generics (Genericity)

**Generics** allows writing abstraction pattern valid for multiple types. The two main benefits are:
- Better robustness
- Better runtime performance

Since C# 2.0 permits the generic implementation of:
- Classes
- Structs
- Methods
- Interfaces
- Delegates

## default(T)

Generic types in C# include built-in types. Sometimes it's necessary to assign or return the default value of a generic T type. If we have *T variable;* , the assignment *variable=null;* would not be valid as T can be a built-in type (int, char, ...)
C# provides the **default** keyword for this reason. It returns **null** if T is an object or **0**, **'\\0'** or **false** if it's a built-in type

### Generic Methods

```C#
class Generics {
	public static T ConvertReference<T> (Object reference){
		if(!(reference is T))
			return default(T); // default value for T type
		return (T) reference;
	}
	public static void Main() {
		Object myString = "hello", myInteger = 3;
		// Correct conversions
		Console.WriteLine(ConvertReference<String>(myString));
		Console.WriteLine(ConvertReference<int>(myInteger));
		// Wrong conversions
		Console.WriteLine(ConvertReference<int>(myString));
		Console.WriteLine(ConvertReference<String>(myInteger));
	}
}
```

### Generic Classes

```C#
class GenericClass<T> {
	private T field;
	public GenericClass(T field){
		set(field);
	}
	public T get(){
		return field;
	}
	public void set(T field){
		this.field = field;
	}
}

class Run {
	public static void Main(){
		GenericClass<int> myInteger = new GenericClass<int>(3);
		Console.WriteLine(myInteger.get());
		GenericClass<string> myString = new GenericClass<string>("hello");
		Console.WriteLine(myyString.get());
	}
}
```

### Bounded Generics

By default, generic variables are **Object** instances. **Bounded generics** allow making generic parameters more specific and hence less general. 
For example, the **Sort** generic method below sorts any array of elements that implement ***IComparable\<T>*** interface.

## IEnumerable\<T>

**IEnumerable\<T>** exposes a collection of T elements, supporting a single iteration over them. It has not necessarily to be a container
Derives from the polymorphic **IEnumerable**, that can be iterated with a **foreach**. Arrays derive from **Array** which implements **IEnumerable\<T>**

```C#
int[] intArray = new int[] {10, 99, 50};
Array a = intArray;
IEnumerable enumerable = intArray;
IEnumerable<int> enumerablei = intArray;
```

**IEnumerable\<T>** and **IEnumerable** only declare one **GetEnumerator** message. It's a *factory method* responsible for building an iterator
- **IEnumerable** is a bridge to hide the iterator implementation
- The iterator is commonly implemented as a nested class within the collection
![[Pasted image 20240215174316.png]]

## Nullable Types

Sometimes is required to represent that a built-in variable has no value (null). C# represents these types with the **?** postfix: **int?, char?, bool? ...**
These types derive from the **Nullable\<T>** struct. The two most important members are
- **HasValue:bool** (read-only) To know whether the value is **null** or not
- **Value:T** (read and write) Returns the value if it is not **null;** , otherwise, **default(T)** is returned
C# has also added the **??** operator

## Collections

Sometimes we need **abstractions that store collection** of objects. They're called **containers** and they're specific implementations of collections. C# provides:
- Array objects (vectors)
- Many classes in the .Net framework that provide different collection implementations

.Net provides two kind of collections:
- **Polymorphic**: Collect **Object** instances by means of polymorphism. **System.Collections** namespace
- **Generic**: Collects objects by means of generics. **System.Collections.Generic** namespace

When it's possible, it's better to use generic ones because:
- They provide better runtime performance
- Less runtime errors occur
- More readable code with less casts

## System.Collections.Generics

Most important classes are:
- **List\<T>**: Variable length Vector
- **Dictionary\<Key, Value>**: Provides a mapping from a set of keys to a set of values, implemented as a hash table
- **HashSet\<T>**: a collection that contains no duplicate elements
- **LinkedList\<T>**: Doubly linked list
- **Queue\<T>**: FIFO collection
- **Stack\<T>**: LIFO collection
- **SortedDictionary\<T>**: A dictionary sorted on the key

[MSDN documentation](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic)