Abstract class enables data encapsulation and polymorphism. It doesn't allow multiple inheritance. 

Java provides a mechanism to achieve abstraction, polumorphism, and inheritance. This can be achieved using abstract and interface keyword.

Properties of abstraction using abstract keyword -

- It is defined using the abstract keyword preceding the class keyword

- Abstract class can be subclassed but cannot be instantiated

- If a class has one abstract nature, then the entire class should be abstracted. This also means an abstract class can have concrete or abstract methods

- Subclass that extend the abstract class must implement all the abstract methods or be an abstract class itself.

```java
public abstract class BoardGame {

    //... field declarations, constructors

    public abstract void play();

    //... concrete methods
}
```

```java
public class Checkers extends BoardGame {

    public void play() {
        //... implementation
    }
}
```

When to use abstract classes -

- Abstraction can be used to encapsulate multiple functionality into one place and can be reused across other places

- Abstraction allows for lazy implementation, where the blueprint is defined and the implementation is done more concretely someplace else

- Concrete classes have common functionality that can be used with protected access modifiers

Properties of abstraction using interface keyword -

- An interface is a blue print for a class. Interface cannot be instantiated using the new keyword but concrete class can implement these methods. Eg Map, List, Set

```java
interface Mogul {
    void name();
}
```

- Abstract class can have both implemented and unimplemented methods. Eg. AbstractList, AbstractSet
