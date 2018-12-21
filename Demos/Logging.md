# Logging
## Java Logging API
```java
import java.util.logging.Logger;

public class Example {

	private static final Logger logger = 
        Logger.getLogger(Example.class.getName());

}
```

```java
public void foo() {
    logger.entering(getClass().getName(), "foo");
    
    try {
        logger.log(Level.INFO, "Setting x");
        System.out.println("This is x");
        int x = 5;
        logger.info("x = " + x);
        throw new Exception("An exception has occurred");
    } catch (Exception e) {
        logger.log(Level.SEVERE, "Error: {0}", e.getMessage());
    }

    logger.exiting(getClass().getName(), "foo");
}
```

```java
public static void main(String[] args) {
// LogManager.getLogManager().reset();
    try {
        FileHandler handler = new FileHandler("log.txt", true);
        handler.setFormatter(new SimpleFormatter());
        logger.addHandler(handler);
    } catch (IOException e) {
        e.printStackTrace();
    }
    logger.setUseParentHandlers(false);
    new LoggingExample().doIt();
}
```