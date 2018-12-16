# [Return to Index](https://pizzastack.github.io)
# Design Patterns: Dependency Injection
Some classes require another class, a dependency. While the dependency can be defined in the dependant class's own constructor, this introduces several problems such as tightly coupling the two classes and introducing difficulties during unit testing. To solve this, we can inject the dependency as an argument into the dependant class's constructor or setter.

```java
public class Order {
    private Customer customer;

    // Constructor Injection
    public Order(Customer customer) {
        this.customer = customer;
    }

    // Setter Injection
    public setCustomer(Customer customer) {
        this.customer = customer;
    }
}
```

## Testing Benefits
By injecting dependencies, we can more easily test this class without having to also test the dependency which can be independantly tested, if necessary. The injection pattern means that a mocked dependency can be injected in the original dependency's place.

```java
public class MockCustomer extends Customer {
    // Stub methods overriding the super class methods
}
```

```java
public class OrderTest {
    @Test
    public void testMock() {
        Order order = new Order(new MockCustomer);
    }
}
```