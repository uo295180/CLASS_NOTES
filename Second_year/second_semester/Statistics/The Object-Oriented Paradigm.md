Defines programs as interactions among objects that has data and services. 
**Abstraction** denotes the essential characteristics of an object that distinguish it form all other kind of objects.

## Encapsulation

Process of compartmentalizing the elements of an abstraction. Information hiding allows to separate the data accesible to the rest of the application from the intern data. For that purpose, different levels for **controlling access** to members are provided. 
Several benefits are provided by this approach, for example changing the implementation of a class without having to modify its interface. 

## Properties

They seem to be as a public atribute but internally they're implements as a getter and a setter. Then can **read** or **write** the object state. Properties can be:
- Declared with all the information hiding levels
- *Static*
- *Abstract*
- *Overridden*

```C#
public class Circumference {
	private int x;
	public int X {
		get{return x;} // Read Only
	}
	public uint Radius {get; set;} // Read and write
	public int Y {get, private set;} // Read only
	public void Move(int relx, int rely){
		x += relx;
		Y += rely;
	}
}
```

# Modularity

Consists of partitioning a program into individual components. 

## Coupling and Cohesion

- **Coupling**: Degree of interconnectedness of modules (How much a module depends on another one)
- **Cohesion**: Degree of connectivity among the elements of a single module
We aim to reduce coupling and increase cohesion to increase maintainability and reutilization

## Method Overloading

Using two or more methods with the same name but with different parameters.
**out** indicates that the method should return. Objects are passed as **ref**.

## Operator Overloading

It allows operators to have different meanings depending on their parameter types.

# Inheritance vs Polimorphism

#### Difference between inheritance and polymorphism

Inheritance allows us to refactor code. Using generalization allows us to move code upwards, so we can maintain only one copy of the code. 
Polimorphism also allows us to specialize some code for a reduce amount of objects that share similar characteristics but requires some special features.

## Inheritance

It's a code **reutilization technique**. Aims for the union of fields and services that're common for different objects.

## Polimorphism

It's a **generalization** mechanism. Allows a general abstraction to represent more specific abstractions. Derived references promote to base references. With polimorphism, an specific object can promote automatically to the father class without any cast.

## Dynamic Binding

It happens at runtime. It's a specialization mechanism (similar to downcast in java). It's not provided by default in C\#. 
To enable it, we need to mark an object as virtual and then the derived method needs to be overridden. If we create a method with the same name and no overriding is required, we need to mark it as **new**.

## Abstract Classes 

When we need to provide some message but it cannot be implemented (Works as in java).
We need to override the abstract method, so we ensure that all the classes that inherits that class has that specific method.

## Multiple Inheritance

This feature allows directly inheriting from more than one superclass. The derived classes inherits all the members of all the superclasses
$$\text{members(instance(F))} = \text{members(F)} \cup \text{members(C)} \cup \text{members(D)} \cup \text{members(A)}  $$
This can produce two conflicts:
- **Name conflict**: When two superclasses have different members with same identifier. The access to this member in the derived class is ambiguous
- **Repeated inheritance**: When a class derives more than once from the same superclass. Then, it inherits repeated members.

# Interfaces

It's not commonly used as a code reutilization mechanism, but as a multiple generalization technique. 
Sometimes, we need a type to be a subtype of two or more super-types. An interface is the set of messages a class provides to their clients. In C\# this concept is offered as a type as in Java. They also provide **multiple subtyping**

[Mandatory Activity](https://www.artima.com/articles/composition-versus-inheritance)


