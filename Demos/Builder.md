# [Return to Index](https://pizzastack.github.io)
# Design Patterns: Builder
This constructor may change as new requirements are introduced, or users may accidentally switch their arguments and introduce bad data. A Builder can help solve this.

```java
// Pizza.java
public class Pizza {
	private int size;
	private String crust;
	private Sauce sauce;

	public Pizza(int size, String crust, Sauce sauce) {
		this.size = size;
		this.crust = crust;
		this.sauce = sauce;
	}
}
```

This builder provides special setter methods for each field, but returns itself allowing users to chain together method calls before finally calling the build method to construct the above class type.
```java
// PizzaBuilder.java
public class PizzaBuilder {
	
	private int size = 12;
	private String crust = "Regular";
	private Sauce sauce = Sauce.MARINARA;
	
	public PizzaBuilder withSize(int size) {
		this.size = size;
		return this;
	}
	
	public PizzaBuilder withCrust(String crust) {
		this.crust = crust;
		return this;
	}
	
	public PizzaBuilder withSauce(Sauce sauce) {
		this.sauce = sauce;
		return this;
	}
	
	public Pizza buildPizza() {
		return new Pizza(size, crust, sauce);
	}

}
```

The builder can be used as follows:
```java
Pizza pizza = new PizzaBuilder()
                    .withSauce(Sauce.ALFREDO)
                    .withSize(10)
                    .withCrust("Thin")
                    .buildPizza();
```

## Generic parameters & Lambdas
Builders can be further simplified with a generic method that accepts and returns generic parameters.
```java
public class GenericPizzaBuilder {
	public int size = 12;
	public String crust = "Regular";
	public Sauce sauce = Sauce.MARINARA;
	
	public GenericPizzaBuilder with(Consumer<GenericPizzaBuilder> builderFunction) {
		builderFunction.accept(this);
		return this;
	}
	
	public Pizza buildPizza() {
		return new Pizza(size, crust, sauce);
	}

}
```

This builder can be used as follows:
```java
Pizza magicPizza = new GenericPizzaBuilder()
				.with(var -> {
					var.size = 12;
					var.sauce = Sauce.ALFREDO;
					var.crust = "Thin";
				}).buildPizza();
```