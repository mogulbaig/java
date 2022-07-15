String are created immutable, thread-safe to improve cachine and performance. String uses a process called interning, where we store only one distinct copy of the value and reusing them to save heap (two different variables point to the same string object).

### String Buffer and String Builder

- String are immutable, and objects of StringBuffer and StringBuilder are mutable.
- StringBuffer and StringBuilder are similar, but StringBuilder is faster and preferred over StringBuffer for single-threaded program. If thread safety is needed, then StringBuffer is used.

### **==, comparison**

This way of string comparison only checks for referential equality of two string.

```java
String string1 = "using comparison operator";
String string2 = "using comparison operator";
String string3 = new String("using comparison operator");

assertThat(string1 == string2).isTrue();
assertThat(string1 == string3).isFalse();
```

In the example above, the first assertion is true because the two variables point to the same *String* literal. On the other hand, the second assertion is false because *string1* is created with a literal and *string3* is created using the *new* operator – therefore they reference different objects.

### **equals()**

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

In this example, *string1, string2,* and *string4* variables are equal because they have the same case and value irrespective of their address.

For *string3* the method returns *false,* as it's case sensitive. Also, if any of the two strings is *null*, then the method returns *false.*

### **equalsIgnoreCase()**

Ignores casing in characters while comparing *Strings*.

### **compareTo()**

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
