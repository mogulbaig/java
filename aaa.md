JDK is Java software development environment that offers tools and libraries necessary for developing Java based application. 

JVM, and JRE are core components of JDK. JDK has private JVM and few other resources for developing JVM application

* JRE

* Archiver

* Compiler

* Interpreter (loader)

**How does JVM work**

JVM calls the main function. Java applications are called WORA (write once read anywhere) a programmer can develop Java code on one system and expect to run on any other environment. 

When we compile a .java file, a .class file gets created by the Java compiler. These class files go through various stages - 

![jvm](https://media.geeksforgeeks.org/wp-content/uploads/jvm-3.jpg)

**Just in Time Compiler**

# Data Type

Java is strictly pass by value.

In pass by value, the caller and callee method operate on two difference variables which are copies of each other. Any changes on the one won't modify the other. While calling the method, the parameters are passed will be clone of the original parameters. Any modification done won't have any effect on the original parameters.

In pass by reference, the caller and callee method will operate on the same object. Any changes on the parameter will result in changes of the original value.

Primitives variables store the actual value, non-primitive variables store reference

### Immutable

An object whose state remains constant after it has been created entirely. Once an object has been assigned to a variable, we can neither update the reference nor mutate the internal state.

## Data Types

There are two broad data types - primitive and reference. Primitive data types are the basic data types. In Java, the primitive data types are interger, floating-point, character, and boolean. Reference data types are object that contains references to values or other objects.

**Declaring the primitive data types**

```java
int a;
int b;
```

The variables will receive default values based on their declared types. For integers, the default values would be 0, and 0.0.

### Array

An array is a reference type that can store collections of specific type. 

The array *arr* is declared as final, but the elements of an array are changed without any problem. [Arrays are objects](https://www.geeksforgeeks.org/g-fact-65/) and [object variables are always references](https://www.geeksforgeeks.org/g-fact-46/) in Java. So, when we declare an object variable as final, it means that the variable cannot be changed to refer to anything else.
