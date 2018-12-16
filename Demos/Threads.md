# Threads
Besides the main thread, developers can instantiate their own when:

1. A custom class extends the `Thread` class 
1. A `Thread` is passed an implemented `Runnable` instance

Override the `run()` method in both cases to define the program to be run concurrently in the new thread, then call the Thread instance's `start()` method.

## Extend `Thread`
```java
public class CustomThread extends Thread {
    @Override
    public void run() {
        // Do something
    }

    public static void main(String[] args) {
        new CustomThread().start();
    }
}
```

## Implement `Runnable`
```java
public class CustomRunnable implements Runnable {
    @Override
    public void run() {
        // Do something
    }

    public static void main(String[] args) {
        new Thread(new CustomRunnable()).start();
    }
}
```

## Anonymous `Runnable` Class
```java
new Thread(new Runnable() {
        public void run() {
            // Do something
        }
    }).start();
```

## `Runnable` Lambda
```java
new Thread(
    () -> { /* Do something */ };
    ).start();
```