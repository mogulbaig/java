Collection maintains complex data types. 

### LinkedList

It is a doubly linked list implementation of the List and Deque interfaces. LinkedList permits null values.

* It is not synchronized

* If a list is modified while iteration will result in ConcurrentModificationException

### Comparable and Comparator

Allows for comparing custom object types that aren't directly comparable. 

```java
public class Player implements Comparable<Player> {

    // same as before

    @Override
    public int compareTo(Player otherPlayer) {
        return Integer.compare(getRanking(), otherPlayer.getRanking());
    }

}
```

Sorting order is decided by the return value of compareTo() method. The method returns a number indicating whether the object being compared is less, equal, or greater than the object being passed. 

Comparable interface is a good choice to use for defining default ordering of that object. Comparator requires us to create separate independent comparator class for comparison logic.

## Hashset

Stores unique elements and permits null and doesn't maintain insertion order and not thread-safe. Internally a hashmap gets initialized when hashset is created. 

When an object is inserted into a HashSet, we first check the object's hashcode value to determined if its already available in the set. Each hashcode value corresponds to a certain bucket location which contain various elements. 

Objects within the same buckets will be compared using equals() method. 

### Hashmap

For maps to work properly we need to provide an implementation of equals() and hashcode(). These methods need to be overriden only for classes that want to be used a map keys not for classes that will be used as values. 

Hashmap calculates the position of based on the hashcode. The keys are stored in buckets and the number of buckers is called capacity. The hashcode method is used to determin the bucket of the key where the value needs to be inserted. 

An important aspect of the key is that it should be immutable. 

```java
public class MutableKey {
    private String name;

    // standard constructor, getter and setter

    @Override
    public boolean equals(Object o) {
        if (this == o) {
            return true;
        }
        if (o == null || getClass() != o.getClass()) {
            return false;
        }
        MutableKey that = (MutableKey) o;
        return Objects.equals(name, that.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name);
    }
}
```

```java
MutableKey key = new MutableKey("initial");

Map<MutableKey, String> items = new HashMap<>();
items.put(key, "success");

key.setName("changed");

assertNull(items.get(key));
```

We're no longer able to get the corresponding value once the key has changed, instead, *null* is returned. This is because *HashMap* is searching in the wrong bucket

**Collisions**

Similar keys need to have the same hashcode thus belonging to the same bucket. The complexity to find the key inside the bucket is O(N) as List is used as bucket.

**Initializer**

Using static initializer

```java
public static Map<String, String> articleMapOne;
static {
    articleMapOne = new HashMap<>();
    articleMapOne.put("ar01", "Intro to Map");
    articleMapOne.put("ar02", "Some article");
}
```
