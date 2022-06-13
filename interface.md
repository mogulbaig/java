Interfaces is used to implement polymorphism and multiple inheritance. They help add additional functionality to unrelated classes. For instance Comparable, Comparator, and Cloneable are interfaces that can be implemented by unrelated classes. 

### Default Methods

Conceptually the main purpose of default methods in interfaces is backward compatibility. 

### Multiple Inheritance

Java primarily supports single inheritance. Using interfaces we can implement multiple interfaces. 

```java
public interface Transform {
    void transform();
}

public interface Fly {
    void fly();
}

public class Car implements Fly, Transform {

    @Override
    public void fly() {
        System.out.println("I can Fly!!");
    }

    @Override
    public void transform() {
        System.out.println("I can Transform!!");
    }
}
```

In order to enable multiple inheritance through interfaces we have to remember a few rules. 

* Interface extending another interface

* Abstract class implementing interfaces

### Polymorphism

Ability for an object to take different forms during runtime. It is achieved through overriding behavior of a specific object.

```java
public interface Shape {
    String name();
}
```

```
public class Circle implements Shape {

    @Override
    public String name() {
        return "Circle";
    }
}
```

```java
public class Square implements Shape {

    @Override
    public String name() {
        return "Square";
    }
}
```

```java
List<Shape> shapes = new ArrayList<>();
Shape circleShape = new Circle();
Shape squareShape = new Square();

shapes.add(circleShape);
shapes.add(squareShape);

for (Shape shape : shapes) {
    System.out.println(shape.name());
}
```
