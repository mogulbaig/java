### Variable Scope

**Instance and Class Variable**

Instance and class variables don't require us to initialize. As soon as we declare them they are given default value.

```java
@Test
public void whenValuesAreNotInitialized_thenUserNameAndIdReturnDefault() {
    User user = new User();

    assertThat(user.getName()).isNull();
    assertThat(user.getId() == 0);
}
```

**Local Variable**

Local variable must be initialized before use, as they don't have default value. The below code will give error during the compilation stage itself.

```java
public void print(){
    int i;
    System.out.println(i);
}
```

**Final**

Final variable is applied to the field that can no longer be modified.
