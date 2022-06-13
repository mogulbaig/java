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

### String

String are thread-safe. String are mutable to improve cachine, security, synchronization and performance. It is the most widely used data structure and caching the literals and reusing them saves a lot of heap. 

Interning is the process of storing only one copy of distinct string value. Two different variables are pointing to the same string object saving memory. 

**==, comparison**

This way of string comparison only checks for referential equality of two string. 

```java
String string1 = "using comparison operator";
String string2 = "using comparison operator";
String string3 = new String("using comparison operator");

assertThat(string1 == string2).isTrue();
assertThat(string1 == string3).isFalse();
```

In the example above, the first assertion is true because the two variables point to the same *String* literal. On the other hand, the second assertion is false because *string1* is created with a literal and *string3* is created using the *new* operator – therefore they reference different objects.

**equals()**

Equals is overriden by the String class from the Object. This method compares two strings character by character ignoring their address.

```java
String string1 = "using equals method";
String string2 = "using equals method";

String string3 = "using EQUALS method";
String string4 = new String("using equals method");

assertThat(string1.equals(string2)).isTrue();
assertThat(string1.equals(string4)).isTrue();

assertThat(string1.equals(null)).isFalse();
assertThat(string1.equals(string3)).isFalse();
```

In this example, *string1, string2,* and *string4* variables are equal because they have the same case and value irrespective of their address.

For *string3* the method returns *false,* as it's case sensitive. Also, if any of the two strings is *null*, then the method returns *false.*

**equalsIgnoreCase()**

Ignores casing in characters while comparing *Strings*.

**compareTo()**

Compares two string character by character lexicographically. This method returns 0 if two *Strings* are equal or if both are *null,* a negative number if the first *String* comes before the argument, and a number greater than zero if the first *String* comes after the argument *String.*

```java
String author = "author";
String book = "book";
String duplicateBook = "book";

assertThat(author.compareTo(book))
  .isEqualTo(-1);
assertThat(book.compareTo(author))
  .isEqualTo(1);
assertThat(duplicateBook.compareTo(book))
  .isEqualTo(0);
```
