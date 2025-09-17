## Introduction
- Singleton pattern restricts the instantiation of a class and ensures that only one instance of the class exists in the Java Virtual Machine.
- The singleton class must provide a global access point to get the instance of the class.
- Singleton pattern is used for [logging](https://www.digitalocean.com/community/tutorials/logger-in-java-logging-example), drivers objects, caching, and [thread pool](https://www.digitalocean.com/community/tutorials/threadpoolexecutor-java-thread-pool-example-executorservice).
- Singleton design pattern is also used in other design patterns like [Abstract Factory](https://www.digitalocean.com/community/tutorials/abstract-factory-design-pattern-in-java), [Builder](https://www.digitalocean.com/community/tutorials/builder-design-pattern-in-java), [Prototype](https://www.digitalocean.com/community/tutorials/prototype-design-pattern-in-java), [Facade](https://www.digitalocean.com/community/tutorials/facade-design-pattern-in-java), etc.
- Singleton design pattern is used in core Java classes also (for example, `java.lang.Runtime`, `java.awt.Desktop`).

## Implementation considerations
To implement a singleton pattern, we have different approaches, but all of them have the following common concepts.
- Private constructor to restrict instantiation of the class from other classes.
- Private static variable of the same class that is the only instance of the class.
- Public static method that returns the instance of the class, this is the global access point for the outer world to get the instance of the singleton class.

## Implementation approaches

### Eager initialization
In eager initialization, the instance of the singleton class is created at the time of class loading.  
**Drawback:** to eager initialization is that the method is created even though the client application might not be using it.
```java
public class EagerInitializedSingleton {

    private static final EagerInitializedSingleton instance = new EagerInitializedSingleton();

    // private constructor to avoid client applications using the constructor
    private EagerInitializedSingleton(){}

    public static EagerInitializedSingleton getInstance() {
        return instance;
    }
}
```

If your singleton class is not using a lot of resources, this is the approach to use. 
But in most of the scenarios, singleton classes are created for resources such as File System, Database connections, etc.

### Static block initialization
Static block initialization implementation is similar to eager initialization, except that instance of the class is created in the static block that provides the option for exception handling.
```java
public class StaticBlockSingleton {

    private static StaticBlockSingleton instance;

    private StaticBlockSingleton(){}

    // static block initialization for exception handling
    static {
        try {
            instance = new StaticBlockSingleton();
        } catch (Exception e) {
            throw new RuntimeException("Exception occurred in creating singleton instance");
        }
    }

    public static StaticBlockSingleton getInstance() {
        return instance;
    }
}
```
Both eager initialization and static block initialization create the instance even before it’s being used and that is not the best practice to use.

### Lazy Initialization
Lazy initialization method to implement the singleton pattern creates the instance in the global access method.
```java
public class LazyInitializedSingleton {

    private static LazyInitializedSingleton instance;

    private LazyInitializedSingleton(){}

    public static LazyInitializedSingleton getInstance() {
        if (instance == null) {
            instance = new LazyInitializedSingleton();
        }
        return instance;
    }
}
```

This implementation is not thread safe. if multiple threads skip the if check at the same time, we can get multiple instances of this class.

### Thread Safe Singleton
A simple way to create a thread-safe singleton class is to make the global access method [synchronized](https://www.digitalocean.com/community/tutorials/thread-safety-in-java "Java Synchronization and Thread Safety Tutorial with Examples") so that only one thread can execute this method at a time.
```java
public class ThreadSafeSingleton {

    private static ThreadSafeSingleton instance;

    private ThreadSafeSingleton(){}

    public static synchronized ThreadSafeSingleton getInstance() {
        if (instance == null) {
            instance = new ThreadSafeSingleton();
        }
        return instance;
    }

}
```

It reduces the performance because multiple threads can be waiting on getInstance but only one thread can execute it at a time, hence blocking other thread from proceeding. To avoid this extra overhead every time, _double-checked locking_ principle is used

```java
	public static ThreadSafeSingleton getInstance() {
        if (instance == null) {
		    synchronized(ThreadSafeSingleton.class){
			    if(instance == null){
		            instance = new ThreadSafeSingleton();
			    }
		    }
        }
        return instance;
    }

```

### Bill Pugh Singleton Implementation
Create the singleton class using an inner static helper class.
```java
public class BillPughSingleton {

    private BillPughSingleton(){}

    private static class SingletonHelper {
        private static final BillPughSingleton INSTANCE = new BillPughSingleton();
    }

    public static BillPughSingleton getInstance() {
        return SingletonHelper.INSTANCE;
    }
}
```
\
### Enum Singleton Implementation

- `enum` is inherently singleton in Java because Java ensures that any enum value is instantiated only once.
- This approach is thread-safe and also prevents issues related to serialization, ensuring a single instance throughout the application.
```java
public enum Singleton {
    INSTANCE;

    // Add your methods and fields here
    public void someMethod() {
        // Method implementation
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        Singleton singleton = Singleton.INSTANCE;
        singleton.someMethod();
    }
}

```
