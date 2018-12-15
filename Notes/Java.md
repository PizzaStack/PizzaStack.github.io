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

## Programming and Compiling
Most Java applications only require the **JRE** (Java Runtime Environment). But to write and compile you need the **JDK** (Java Development Kit). While the JRE provides Java's standard libraries and exceptions as well as a JVM, the JDK provides all the above as well as *javac*, the compiler. Java source code is written in text files labeled with *.java* extension. It is then compiled into bytecode in *.class* files by *javac*. Then the bytecode is executed by the JVM, which translates the Java commands into low-level instructions to the operating system.

Since Java 6, all Java programs not run inside a container (such as a Servlet Web Container) start and end with the main method. The class containing the main method can have any name, but the method itself should always be named *main*

```java
class Example {
    public static void main(String[] args) {
        System.out.println("Num args:" + args.length);
    }
}
```

- *public* is a Java access modifier keyword that means the `main` method can be accessed from any method during the program's execution.
- *static* is a Java keyword that means the method can be invoked without creating an instance of the class that contains it, making it a global method.
- *void* is a Java return type keyword that means the method doesn't return any values of any data type.
- *args* is a Java variable of type String array which means the method can take command line arguments as an array of Strings

We can compile this code into a *.class* file of the same name:
>javac Example.java

And to run the resulting `Example.class` file:
>java Example

The `java` and `javac` commands require the full directory path or class path to any source code or binary file respectively. If you have a package `com.demo` in the first line of Example, then you would nest the java file into a `com/demo/` directory and then run:
>javac com/demo/Example.java 

>java com.demo.Example

From here we can add packages and imports, expanding the application into a set of interacting objects. By default, the *javac* compiler implicitly imports several base packages from the standard library.

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
Reference types store the memory address location of more complex data types. They are most commonly used to point to the location of objects in memory, and are checked by the garbage collector regularly. If an object has no reference, it will eventually be removed from memory.

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

# Maven 
Build automation and dependency management tool. Once installed, use with the `mvn` command. Allows for a project to be IDE agnostic.

## Example commands
Create a new Maven project with the quickstart archetype. Change groupId and artifactId arguments as needed:
>mvn archetype:generate -DgroupId=com.revature -DartifactId=my-first-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

Package project into a jar
>mvn package

Remove target folder and compiled build
>mvn clean

Run JUnit tests
>mvn test

# Threads
A *thread* is a unit of program execution that runs independently from other threads. Java programs can consist of multiple threads of execution that behave as if they were running on independent CPUs.

- `java.lang.Thread` is the Thread class representing a thread, which you can extend and then override its run() method. Afterwards, you call start().
- `java.lang.Runnable` is a functional interface (meaning only one method) which you can implement and then override run(). Afterwards, you can pass the object to a Thread instance and run start().
- The `synchronized` keyword is a modifier that can be used to write blocks of code, methods, or other resources to protect it in a multithreaded environment.
- `wait()` and `notify()` or `notifyAll()` methods of `java.lang.Object` can be used to suspend or wake up threads.

# I/O Streams
The JVM can connect to sources of data that exist outside itself, from files on the hard drive to network port sockets and of course the standard input/output channels of a console.
- Byte Input Streams
    - **BufferedInputStream** Reads a buffer of bytes from an InputStream, and then returns bytes from the buffer, making small reads more efficient.

    - **ByteArrayInputStream** Reads bytes sequentially from an array.

    - **FileInputStream** Reads bytes sequentially from a file.

    - **ObjectInputStream** Reads binary representations of Java objects and primitive values from a byte stream. This class is used for the deserialization of objects.

- Character Input Streams
    - **BufferedReader** Reads a buffer of characters from a Reader, and then returns characters from the buffer, making small reads more efficient.

    - **FileReader** Reads characters sequentially from a file. An InputStreamReader subclass that reads from an automatically-created FileInputStream.

    - **InputStreamReader** Reads characters from a byte input stream. Converts bytes to characters using the encoding of the default locale, or a specified encoding.

- Byte Output Streams
    - **BufferedOutputStream** Buffers byte output for efficiency; writes to an OutputStream only when the buffer fills up.

    - **FileOutputStream** Writes bytes sequentially to a file.

    - **ObjectOutputStream** Writes binary representations of Java objects and primitive values to an OutputStream. Used for the serialization of objects.

- Character Output Streams
    - **BufferedWriter** Buffers output for efficiency; writes characters to a Writer only when the buffer fills up.

    - **FileWriter** Writes characters sequentially to a file. A subclass of OutputStreamWriter that automatically creates a FileOutputStream.

    - **OutputStreamWriter** Writes characters to a byte output stream. Converts characters to bytes using the encoding of the default locale, or a specified encoding.

    - **PrintWriter** Writes textual representations of Java objects and primitive values to a Writer.

# Collections API
Java provides the **Collection** interface which provides a framework for several diffrent containers which will be disscussed below. All interfaces except **Map** share **Collection** as their superinterface.  
  
- **List** is an ordered collection of elements. A user has the ability to place an element anywhere in the list. The elements are accessable by their index. Unlike **Set**, **List** typically allows for duplicate elements such that element1.equals(element2). In addition to duplicates, **List** allow for multiple null elements to be stored.  
  
- **Set** is a collection of non duplicate elements meaning there will never exist a situation where element1.equals(element2). In addition to this, it is implied that there can only exist one null element due to the no duplicates rule.  

- **Queue** is a collection of elements who in essence cannot be iterated, instead the **Queue** follows the **FIFO** (First In First Out) rule. When an element is added to the **Queue** it is placed at the back and when an element is pulled it is pulled from the from the front (index :0).  
  
- **Deque** extends **Queue** but augments the ability to insert and remove elements at either end. The name is short for "Double Ended Queue" and is pronounced "Deck".  
  
- **Map** is an interface which stores data with a key. A map cannot contain duplicate keys; each key can map to at most one value. **Map** can be visualized like a dictionary where only one word is paired with one definition.  

## Example Implementations
  
**ArrayList** extends **AbstractList** and implements **List** (among others). **ArrayList** provides a dynamic array implementation. **ArrayList** has a dynimic capacity which is resized when the user fills the container. At all times the **ArrayList** capacity will be either larger or the same size as the number of elements it contians.  
  
**HashSet** extends **AbstractSet** and implements **Set** (among others). **HashSet** implements the **Set** interface which organizes elemts based on a hash map. Due to the hash map, there is no guananteed order of iteration.  
  
**TreeSet** extends **AbstractSet** and implements **NavigableSet**. Elements in the set are ordered using natural ordering (sorted and ascending order). **TreeSet** does not preserve the insertion order of elements but elements are sorted by keys. Alternatively, a Comparator can be passed in the constructor to achieve other orderings. Elements in a **TreeSet** must be homogenous and comparable with the default sorting or else a runtime *ClassCastException* will occur. **TreeSet** is essentially an implementation of a self-balancing binary search tree.  
  
**LinkedList** extends **AbstractSequentialList** and implements **List** and **Deque** (among others). **LinkedList** is implemented using a doubly-linked list (meaning it is iterable both forward and backwards).  
  
**HashMap** is an implementation of the **Map** interface. This container allows for both null keys and elements. Unlike the **Map** keys are generated using a hashing algorithm.  
  
**Hashtable** maps keys to values. Any non-null object can be used as a key or as a value. To successfully store and retrieve objects from a hashtable, the objects used as keys must implement the hashCode method and the equals method. The HashMap class is roughly equivalent to Hashtable, except that it is non synchronized and permits nulls. (HashMap allows null values as key and value whereas Hashtable doesn't allow nulls).  
  
![alt text](https://cdncontribute.geeksforgeeks.org/wp-content/uploads/java-collection.jpg "Collections Tree")

