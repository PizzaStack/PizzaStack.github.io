# [Return to Index](/README.md)
# Programming and Compiling
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