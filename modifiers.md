## Access Modifiers

Access modifiers are used to encapsulate the state of the objects.

Default access modifiers are package private, as all members are only visible within the same packages. Protected access modifiers are also package-private but also allows members to be visible to its subclasses.

* Public

* Private

* Protected

* Default

## Non-Access Modifiers

* Final

* Static

* Volatile

* Abstract

* Transient

* Synchronized

## Static

Static keyword means that a particular member belongs to the type itself rather than the instance of that type. That is there is only one instance of the static member shared across all instances of the class. 

### Fields

When a field is declared as static, exactly a single copy of that field is created and shared among all instance of that class. Static fields are stored in the heap.

Static fields can only be declared at a class level, and can be accessed without object creation.

```java
public class Car {
    private String name;
    private String engine;

    public static int numberOfCars;

    public Car(String name, String engine) {
        this.name = name;
        this.engine = engine;
        numberOfCars++;
    }

    // getters and setters
}
```

### Methods

Static methods belong to the class instead of the instance. We can call them without creating the object. 

* Used to create utility or helper classes

Static methods are resolved in compile time. Since method overriding is runtime process static methods cannot be overridden.

* Abstract methods cannot be static. Static methods can't use this or super

* Instance methods can directly access other instance methods and variables

* Instance methods can directly access static methods and variables

* Static methods can access all static variables and methods

* Static methods can't access non-static variables and methods directly. They need to some object reference to do so. 

### Class

## Final

Final keyword is used to limit the scope for variables, classes, and methods.

### Class

Classes market with final keyword cannot be extended. One of the major immutable classes that have final marked are String class.

Any attempt to extend a final class will result in compilation error.

```java
public final class Cat {

    private int weight;

    // standard getter and setter
}
```

Final keyword in class doesn't mean that objects are immutable. We just can't extend it.

### Methods

Methods marked as finals cannot be overriden.

```java
public class Dog {
    public final void sound() {
        // ...
    }
}
```

- Mark a method as final if we don't want to the caller to cause suprising results

- Difference between marking all the methods final and marking the class final is that in the former we can extend the class and in the latter we cannot

### Fields and Variables

Variables marked as final cannot be reassigned. Primitive variables cannot be assigned again. Reference variables cannot be reassigned but are still mutable.

```java
final Cat cat = new Cat();
```

```
cat.setWeight(5);

assertEquals(5, cat.getWeight());
```

Final fields can be constant or write once fields. And class constant fields should be capitalized. In case the fields are not meant to be serialized then the fields must be specified as final.

```java
static final int MAX_WIDTH = 999;
```

All final fields must be initialized before the constructor completes. **You can assign a value to a final variable only one time.**

- For static final fields, these need to be initialized upon declaration or inside static initializers (as static initalizers are created before constructors).

- For instance fields, they can be initialized - upon declaration, inside initializer block, inside the constructor.

Constructor can be invoked only **one** time per object creation by using the `new` keyword. You cannot invoke constructor multiple times, because constructor are not designed to do so.

```
class Test {
    private final List foo;

    public Test() {
        foo = new ArrayList();
        foo.add("foo"); // Modification-1
    }

    public void setFoo(List foo) {
       //this.foo = foo; Results in compile time error.
    }
}
```

`foo` is an **instance** variable. When we create `Test` class object then the instance variable `foo`, will be copied inside the object of `Test` class. If we assign `foo` inside the constructor, then the compiler knows that the constructor will be invoked only once, so there is no problem assigning it inside the constructor.

If we assign `foo` inside a method, the compiler knows that a method can be called multiple times, which means the value will have to be changed multiple times, which is not allowed for a `final` variable. So the compiler decides constructor is good choice!

### Argument

Final argument cannot be changed inside the method

```java
public void methodWithFinalArguments(final int x) {
    x=1;
}
```

The final local variable x cannot be assigned. It must be blank and not using a compound assignment.

### Static - Final

These fields need to be initialized upon declaration or inside static initializers.

```java
private static final List foo = new ArrayList();
```

`foo` is now a **static** variable. When we create an instance of `Test` class, `foo` will not be copied to the object because `foo` is static. Now `foo` is not an independent property of each object. This is a property of `Test` class. But `foo` can be seen by multiple objects and if every object which is created by using the `new` keyword which will ultimately invoke the `Test` constructor which changes the value at the time of multiple object creation (Remember `static foo` is not copied in every object, but is shared between multiple objects)

## Synchronized

Race condition occurs when two or more thread attempt to update mutable shared data. We can avoid this by synchrinized thread access to the shared data allowing only one thread to execute at any given time. 

Synchronized keyword can be used across - 

* instance methods

* static methods

* code blocks

Synchronized internally uses a monitor lock to provide synchronization. The monitors are bound to an object, and all synchronized blocks of the same object can have only one thread executing them at the same time. 

**Synchronized instance methods**

```java
public synchronized void synchronisedCalculate() {
    setSum(getSum() + 1);
}
```

Instance methods are *synchronized* over the instance of the class owning the method, which means only one thread per instance of the class can execute this method.

**Synchronized static methods**

```java
public static synchronized void syncStaticCalculate() {
     staticSum = staticSum + 1;
 }
```

These methods are synchronized on the class objects. Since only one *Class* object exists per JVM per class, only one thread can execute inside a *static* *synchronized* method per class, irrespective of the number of instances it has.

**Synchronized blocks within the methods**

```java
public void performSynchronisedTask() {
    synchronized (this) {
        setCount(getCount()+1);
    }
}
```

This is the monitor object. The code inside the block gets synchronized on the monitor object. Simply put, only one thread per monitor object can execute inside that block of code. If the method was *static*, we would pass the class name in place of the object reference, and the class would be a monitor for synchronization of the block:

## Volatile
