# [Return to Index](https://pizzastack.github.io)
# Java
Java is an object-oriented programming language and a platform developed by Sun Microsystems (eaten by Oracle). Using the principle of **WORA** (Write Once, Run Anywhere), a Java application can be compiled and executed on any platform supported by Java. Flexible, popular, and well-supported, Java has helps developers write scalable client-server web applications, desktop and mobile applications, and frameworks and libraries.

## Features
- **Platform independence**: The compiler converts source code to bytecode, then the JVM executes that bytecode. While each operating system has their own JVM implementation, so every JVM can execute bytecode regardless of origin of said code.

- **Clear, verbose syntax** Java has C-like syntax like C++ and C#, many syntax elements of the language are readable and widely used in programming. The Java API (Application Programming Interface) is also written using verbose, descriptive naming conventions making it simple to parse large code bases.

- **Multi-paradigm** While Java is object-oriented, it supports multiple paradigms such as imperative, generic, concurrent, and functional.

- **Garbage collection** The JVM performs automatic memory deallocation of unused objects at runtime. Programs are written without the need for complex memory management.

- **Multithreading** Java supports multithreading at both language and the standard library levels. It allows concurrent and parallel execution of several parts of a Java program.

- **Object-Oriented Programming** Although Java accommodates several paradigms, OOP is the foundation for most applications. In OOP, a program is organized into objects encapsulating related fields (representing its *state*) and methods (usually to control that state or perform related functions). When defining objects, Java reserves the keyword *class* (not to be confused with the *.class* file extension) which serves as their blueprint. An object in Java represents an instance in memory of a class, and also every class implicitly inherits from the *Object* superclass which provides useful convenience methods such as *equals()* and *toString()*. Java popularized several 'Pillars' of OOP design theory. While the numbers vary between OOP languages, Java focuses on four:

    - *Abstraction* - By simplifying objects to a set of useful features, we hide irrelevant details, reduce complexity, and increase efficiency. Abstraction is important at all levels of software and computer engineering, but essential to designing useful objects. Complicated real-world objects are reduced to simple representations.

    - *Encapsulation* - Objects should group together related variables and functions and be in complete control over them. So the state of an object should only change, if ever, through the object itself. Also known as data hiding, because the object has sole responsibility for its fields, and no outside object or function should interfere.

    - *Inheritance* - Code reuse is an important principle of programming (DRY - Don't Repeat Yourself), and new classes can reuse code from existing ones. This establishes a superclass-subclass (or parent-child) relationship where the derived classes inherit (and sometimes change) fields and methods from its parent.

    - *Polymorphism* - With inheritance, an object of a derived class can be referenced as instances of its parent class. This provides flexibility when invoking inherited methods with varying implementations in derived classes.

## Variables
A value is stored and identified in memory by a variable. Variables have a name that makes it possible to access the value, and a type that defines what sort of value it stores.
```java
int variableName = 64;
String txtVar = "Hello World";
```

## Primitive data types
Java handles two kinds of datatypes: primitives and references. Primitives are variables that store simple values. There are eight in Java.
- Integer types: **byte**, **short**, **int**, and **long** (42)  
- Floating-point types: **float**, and **double** (3.1415)  
- Logical types: **boolean** (true)  
- Character type: **char** ('x')

## Reference types
Reference types store the memory address location of more complex data types in the heap. Reference types include:
- Classes
- Interfaces
- Enums
- Arrays

## Naming variables
- Case sensitivity
- Can only use letters, numbers, and *$* or *_* characters
- Cannot begin with a number
- Cannot be a reserved Java keyword

## Scopes of a variable
A variable's reference will only exist within the context of its declared scope, which is based on the location of its declaration.

- **Static** or class scoped variables are visible to all instances of a related class.
- **Instance** or object scoped variables are visible to only that object instance.
- **Local** or method scoped variables are visible only within a method.
- **Block** or loop scoped variables are visible only within a block statement.

Be aware of *shadowing*: when two variables in different scopes share names.

## Methods
Methods accept a list of arguments known as *parameters* and return some value. They are used to implement repeatable, consistent actions on variable input, much like math functions.
```java
public int myMethod(int a, int b);
public int myMethod(int a);
```

## Constructors
Classes not only define object fields and methods, but how it should be instantiated through special methods called constructors. Constructors must have no return type and share the same name as its class. Java will automatically give you a *noargs* constructor. However, if you define any constructor, you will lose the automatically given constructor.

While a constructor may be *private*, used for singletons, it may not be *final*, *static*, or *abstract*.

## Access modifiers
- **private** - accessible only within the context of that class
- **default** - accessible within the context of a package, has no associated keyword so is set when no modifier is used
- **protected** - accessible to the package, but also to derived child classes outside of the package
- **public** - accessible anywhere

Classes should only be public or default. There are no cascading access levels, and unspecified fields will be default. Subclasses can only change inherited fields to be less restrictive.