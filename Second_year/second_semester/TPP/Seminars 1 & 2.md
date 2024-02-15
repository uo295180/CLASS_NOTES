# Seminar 1 - Polimorphism and Dynamic Binding
## Dynamic Error Handling

Something dynamic is something that happens at runtime. A compiler is not able to detect every possible error in a program. Therefore, many programming languages provide a mechanism to handle runtime errors.

### Exception Handling Objectives

The mechanism to control runtime errors should be
- **Reusable**
- **Robust**
- **Extensible**

### Exceptions

They're objects holding essential information about an exceptional situation occurred at runtime. Exception handling is based on separating (Detecting the error and throwing the exception and handling the exception). In C\# all exceptions are *unchecked*. Exceptions thrown by a method are not specified.

### Assertions

Conditions that must be true in the correct execution of a program. They must not be used to handle runtime errors. We can use assertions to check those conditions that should never happen at runtime. In C\#, they're provided by the **Debug** class in the **System.Diagnostics** namespace. 
C\# provides conditional compilation. If the DEBUG macro is undefined, the assertion code is not compiled.

### Generics

It allows writing abstraction patterns valid for multiple types. It provides better *robustness* and better *runtime performance*.

#### Generic Methods

```C#
class Generics {
	public static T ConvertReference<T>(Object reference){
		if(!(reference is T))
			return default(T);
		return (T) reference;
	}
	
}
```


#### Generic Classes

```C#
class GenericClass<T>{
	private T field;
	public GenericClass(T field){
		this.field = field;
	}
	public T get(){
		return field;
	}
}
```

#### Bounded Generics

Only those messages in **Object** can be passed. By default, generic types are Objects. 
**Bounded** (constraint) **generics** allows making generic parameters more specific.
For example, the **Sort** generic method sorts an array of elements that implements the **IComparable\<T>** interface
```C#
static T[] Sort<T>(this T[] vector) where T:IComparable<T> {...}

////

static IComparable<T>[] Sort<T>(this IComparable<T>[] vector){...}
```

# Seminar 2 - Generics

## Generics in C\# (compare with Java)

.Net makes extensive use of generics. We'll use smth like:
- IEnumerable\<T>
- IList\<T> and List\<T>
- IDictionary\<TKey, TValue> and Dictionary\<TKey, TValue>

Java virtual machine does not support generics. The compiler translates generic types to Object. 

## Type Inference

**Type inference** refers to the automatic deduction of the type of an expression. The less information provided, the most powerful type inference is. 
The following code infers the type of *f* to be *int f (int a, int b)*:
```C#
let f a b = a + b + 100;
```

C\# provides type inference in the following three main scenarios:
- Generic methods
- Implicitly typed local variables (**var**) (var is used bc the compiler needs to infer the type)
- Lambda functions (next unit)

### Type Inference in Generic Methods

```C#
static void Swap<T>(ref T lhs, ref T rhs){
	T temp; temp = lhs;
	lhs = rhs; rhs = temp;
}
static void Main(){
	int a = 1, b = 2;
	Swap(ref a, ref);
	double c = 3.3, d=4.4;
	Swap(ref c, ref d);
	Swap(ref a, ref d);
}
```

### Implicitly Typed Local Variable

We can avoid specifying the type of local variables upon declaration. **var** should be used instead of the variable type