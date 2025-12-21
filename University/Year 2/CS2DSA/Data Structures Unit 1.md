## #CS2DSA_Concepts

#Big-O-Notation:

-a way of recording the time spent to do an action.

O(1)
	constant time, consistently fast no matter what size of input
O(n) 
	linear time, time increases with the size of input
O(n<sup>2</sup>) 
	every item in a data-set interacts with every other item, e.g., 10 students handshaking amongst each other = 100 handshakes. Note that this is about pairs interacting not just items interacting with eachother.
O(log n) 
	faster than O(n) but slower than O(1). Like perusing a dictionary, this algorithm speed goes to the middle of a data set then jumps back or forth to find the inquired data. This halves and halves the operation over and over. So inversely, n increases the operations by a small amount .

Accessing data via a data-set, like an array, would be an example of O(1). Making a new array in order to add new data, or deleting data (besides data at the very end) which shifts the whole array, would be O(n).

#LinkedLists are lists where the individual data items are separated as nodes. Example below from W3S.
```java
// Import the LinkedList class
import java.util.LinkedList;

public class Main {
  public static void main(String[] args) {
    LinkedList<String> cars = new LinkedList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    System.out.println(cars);
  }
}
```
Linked lists can have their items easily removed or added compared to arrays, however perusing the data set is slower overall.
==Accessing items== is O(n) because there's no indexing.
==Inserting items== is O(1) if you reference what nodes you're inserting between, otherwise it's O(n).
Similarly, ==deleting items== has the same caveats. Specifically if you don't use pointers you have to go through the list to delete an item, which is O(n). #Pointers are memory addresses.

#Stacks are #LIFO groups of data, like Pringles. Each element is stored in an ordered manner and to access or alter elements you have to go through each item, there's no indexing. ==Accessing items== in the stack is an O(n) operation.
==Inserting== is O(1) since you just place it on top, and ==deleting== is O(1) too.

#Queues are #FIFO groups of data. It's alike a conveyer belt, elements can only be removed from the front and added at the back.
==Accessing== items is O(n) as you have to search through the set.
==Inserting/Deleting== is O(1) as you add and delete from the front and back. 

#Heaps or Priority-Queues are sets where a root data value is always needed, the latter data values are children of the higher data value.
Heaps come in two variations:

![[Min Heap.png | 200]] ![[Max Heap.png | 220]]

==Accessing== is not a typical operation for heaps, but it would be O(1) for the root/first data value and O(n) for following children values.
==Inserting== is O(log n) because of how inserting works. You add the value into the heap, then the value has to bubble up to its right position based on its size.
==Deleting== acts the same, O(log n), as when you delete a root value the smallest or biggest value must shift to the root position.

#Hashmaps store data through key-value pairs. Keys are associated with data within the storage via a Hash-function. A Hash-function could be the length of a String, such as John being in position 4. This makes ==accessing== data from a Hash-map typically O(1), however if there is too much data in one Hash e.g., two names, John and Andy, being in position 4, values will have to be adjusted into a Linked-List and the accessing speed can slow down to O(n).
==Inserting== is a similar scenario, where inserting data is typically O(1) but if there's too many values associated with a single position then it slows to O(n).
==Deleting== is O(1) as you can just delete by key, but again with a Linked-List situation it would become O(n).
Note that Hashmaps are called Dictionaries in Python.

#Binary-Search-Trees store data in nodes that follow an order. Left children have to contain smaller values than the parent, and right children contain higher values than the parent.
==Accessing== and ==Deleting== become an O(log n) operation.
==Inserting== becomes an O(log n) operation, as you can just look through each value and halve your time. If the tree is unbalanced alike a Linked-List, all three operations become O(n).

#Sets include unique values and don't use any specific order.
==Inserting/Deleting== shares its benefits and drawbacks with HashMaps, at best being O(1) and at worst being O(n).
Set Operations and using Sets to remove duplicates from Linked-Lists are common operations. **Definitely need to research.**

## #CS2DSA_UML

UML Diagrams consist of the classes, attributes (fields) and operations (methods) of a class. They include the relationships between classes and the constraints (features) of connections between objects.
![[{EB546BF4-1E45-487B-9EB2-FCAB63ACF59C}.png | 300]]
This UML diagram depicts an abstract class with private fields and public methods, each showing their parameter type and structure.
![[{75AE6DB5-93B9-465A-82DF-47E2799B9522}.png | 600]]
This UML diagram shows multiple classes, some of which denoting how much of an object they can input or output. e.g., 1 person can have 0 or 1 pet and 1 person can have 1 car, the Car and Pet classes inherit the Ownable class which holds their logic to interact with the Person class.
Inheritance involves superclasses and subclasses, which allows for logic reuse and streamlining activities.
This UML diagram is a more streamlined rendition which allows for more Ownables of each type being allocated to a single Person.
![[{01BBEE7C-D9B0-42B7-A65E-396D12E90425}.png | 600]]
Typical components of a UML class diagram:
- class (abstract/concrete)
- interface
- relation:
  -association "owns a" or "borrows" etc
  ![[{322AF244-0107-438F-8822-9102386C9FC2}.png | 500]]
  -aggregation "has a" or "has"
  ![[{C5F50ECA-5F32-4D38-9FA5-463CAB8F8F86}.png | 500]]
  -composition "is part of a" or "makes up"
  ![[{799F71D4-0F63-4A89-9A6D-EBEF4F6E8435}.png | 500]]
  -dependency "uses"
  ![[{5C48227D-8094-4FE1-B08E-AE3A947C6679}.png | 500]]
  -generalisation "is a" or extends
  ![[{CDA17F12-435F-40B6-A2F4-77E5247D6FDB}.png | 500]]
  -realisation or implements (interface has method names, implementing class uses that method name with its own code)
  ![[{36F93393-22F1-4900-8893-A4EED23818ED}.png | 500]]

  ![[{70DF2244-ACD2-4E38-AA7C-686FEEBDCBEA}.png | 600]]

## #CS2DSA_OOP
### A catch-up on first year CS's OOP module/Object Orientation as a whole.
(Page 5 onwards of the PDF)

Something huge is our definition of an "object". An object in java, unlike the typical vague noun, is not a tangible thing. An object can be a bank account's value or a list of items in a shopping cart. 
==**Objects represent values!**==
#Objects can contain "primitive" data types, numbers, floats, doubles (can store more data than float). They can also represent multiple pieces of data, e.g., a bank account balance (integer), account code (integer or string) and the account name (string).

*An object is an instance of a class.*
==The class would hold the values and logic for the balance, code and name. An object would be the occurrence of those values.
Another example, we have a class "Dog" which holds data for the name and dialogue of a dog object. Then we call a dog object, dog1, which has the name Lucy and "Woof!". That dog1 is an instance of the Dog class.==
```java
Dog dog1 = new Dog("Lucy", "Woof!");
```
Concrete classes can be templates for objects. Abstract classes can be templates for other classes' objects e.g., A car can have general vehicle elements, but has its own features. A truck can be another "subclass" that inherits the abstract "superclass."

Quick side-track, #Inheritance is a subclass that "is a" type of the superclass, while implementation is a subclass that "can do" what the superclass says it can. E.g., A Dog subclass could inherit the "legs" "height" "speak" methods from a mammal superclass, but it has to provide the body of logic within the method e.g., the Dog class can implement "speak" with its own specific way of speaking while a Person class could implement "speak" in another way. 
You can't instantiate something that has no body of logic.

Note that this is type of relation visible in UML Class Diagrams. A Car will have its own original methods for registration and getRegistration, but will also extend and therefore inherit the getOwnerTel and changeOwner methods from the Ownable class. (Example of abstract class inheritance, abstract isn't just different ways of using a method but also each instance of a method being different i.e., different cars having different Owners and Telephone Numbers).

![[{E9AADDD0-247F-4539-9FC4-8E2B3FBF9921}.png | 500]]

#Abstraction is an important term, Abstraction is when the precise details of an object is out of focus. A watch is an abstraction, we as consumers don't know how a watch works but we know its output (time). Abstraction confines details to the littlest amount that we need.
A java interface is an example of a class being abstracted.

## Creating objects

#Variables in Java can either hold a primitive value or a reference to an object, e.g.,
```java
int x; /* creates a variable x to hold a primitive integer */
Integer y; /* creates a variable y to hold a reference to
an object of the Integer class */
Integer y = new Integer(74); /* creates a new Integer object with value 74 and
sets the object reference variable y
to point to the new object */
```
Note that the "74" is the parameter for the object being fulfilled.

#Class-Libraries are sets of classes either included in a language or provided by a third party. Groups of related classes can be called API (Application Package Interface). E.g., the Java Database API is a set of classes that supports database applications such as a Microsoft Access, Java Collections Framework is a set of classes and interfaces for making collection types like LinkedList, ArrayList, HashMap, etc.
Stuff like String and System are in the java.lang package (core classes for Java programming).

You can even make packages within your program, e.g.,
```java
package dsaj;

import java.util.Stack;

public class PureStack {
	// implementation detail omitted
}
```
#Behaviours are the actions an object can take whereas #States are a field of a class (e.g., On, Off, could be a variable).
Variables can be objects (like the aforementioned reference Object variable) so a field can be many things.

#Classes define objects, like design blueprints for a house or patterns for a seamstress' new dress. A class declares the data that each object would store, like a cookie cutter defines what shape a cookie would hold. These declarations are the members of the class.
Visibility modifiers like public, private and protected allow other classes to mingle with the members of a class. Most fields and helper methods should be private as a general rule of thumb. Any members that have no visibility modifiers are treated as "package access" aka can be accessible by any class in the same package.

#Instance-Data is when a variable is declared in a class but not inside any method, i.e., right at the top of the class. This data can be referenced in any method of that class, because the location of a variable determines its scope/reach.

When creating and managing objects, we have two perspectives to consider:
- Designing/developing an object and considering the details of how it works
- Designing/developing other objects that can interact with that object, during which we only take interest in the services (outputs) of those objects.
Objects should be "self-governing" meaning that only the object itself can modify the variables it contains, e.g., an object from a Dog class can only control what it outputs as "speech". No other object should be able to modify the variables of the "Dog" object. This attribute is called #Encapsulation.
Each object in a program only interact amongst each other through their methods, their attributes and inner details are hidden from other objects.
==The methods of a class define the interface between objects of that class and the overarching program.==
Code that uses an object, i.e., a client, should not access the variables of the object.
==Use methods, not direct data!==

#Visibility-Modifiers control access to the members (variables and methods) of a class.
Some examples include:
- final, which makes constant/unmodifiable variables
- public, which makes variables usable from anywhere outside of the class
- private, which makes variables only usable from within the class
- protected, which makes variables only usable by a class and any classes that inherit it.
![[{5632EAB2-53A6-45A8-A63D-D39CB50AE525}.png| 500]]

Instance data is declared at the class level, whereas #Local-Data is declared at the method level. Local data can only be used within that method. 
This can include the parameter names in a method header and variables within the method. Local data ceases when its method is not in use.

#Constructors are alike methods that are called when a object is instantiated. Constructors are how we determine the initial state of an object,
Constructors unlike methods hold the same name as their parent class and do not return values (aka a void method).
If a class has no given constructor it has a default one.

#Method-Overloading is when multiple methods share the same name but still function as they have different parameters. A method's name and its number, type and order of its parameters are what make up its "signature".
If each method's signature is unique then the computer will know what method is being referenced.
```java
System.out.println(String s) // This method is a good example of overloading. Each reference has a different parameter so it still works.
...println(int i)
...println(double d)
...println(char c)
...println(boolean b)
```
Method overloading is used for class constructors and providing a client-class different ways to initialise the fields of its parent-class.
![[{D2AC6C6C-0C2A-4886-88C3-DB4AEA666012}.png | 500]]

An object can refer to itself using the keyword "this".
```java
public class SavingAccount {
	private float balance;
	private int accountNumber;
	private String name;
	
	public SavingAccount(int accountNumber, String owner) {
		this.balance = 0;
		this.accountNumber = accountNumber;
		this.name = owner;
		}
	}
```
If an object reference variable doesn't point to an object, it is null. e.g.,
```java
Integer y // no object pointed to, becomes null
y = new Integer(74) // points to an object, has a value
```
Two or more variables can also point to the same object.
![[{41556997-D5FA-452D-978E-4D181E3AF78E}.png | 500]]
Both x and y here reference SavingAccount, so if you change the balance value then both x and y's balance values are altered.

If an object is not referenced at all, it is referred to as "garbage". Java automatically "collects" this garbage, in that the Java runtime environment collects these unreferenced objects and returns their memory allocation to the system for future use. In other languages you would have to explicitly return that memory space.

### Passing Objects as Parameters
Formal parameters is what we call the parameters in the header of a method, whereas actual parameters is what we call those listed in a method call.
```java
// formal parameters
public class SavingAccount(int accountNumber, String owner)
// actual parameters
SavingAccount jamesSaving = new SavingAccount(24009, James)
```
In Java, all parameters are #passed-by-value meaning that when the method is called, the value of the actual parameter is copied into the formal parameter.
However, if an object is used as a parameter then the address of the object is passed and the formal parameter is an alias for the actual parameter.
```java
public class newAccount {
// instance data omitted
	public class newAccount {
	// body of logic omitted
	}
	
	public class isAccountValid(Person person) {
		return person.getName()
		return person.getAddress()
		return person.getPhone()
		}
}
// In this example, isAccountValid uses Person as a parameter to access the data addressed through Person e.g., name, home address, phone number
```
If you modify the object being referenced, i.e., its state, you modify the state of the object referenced by the actual parameter.
However if you modify the formal parameter, such as assigning it to a different object (i.e., y = new Person) then the actual parameters being used are not impacted.

There is another kind of variable, called a #static-variable, which is declared with the keyword static e.g., private static int count = 0;
Static variables are shared amongst all instances of a class, so there is only one version of that variable for all objects of a class. This means that all the objects instantiated through this class share this one variable, regardless of their own additional services. This can be used to keep track of how many objects have been instantiated from a single class.

Static variables are shared among all instances of a class, as well as #Static-methods. As the static variable is declared, a static method will have static in its declaration. Static variables and methods are both referred to as class variables and class methods.
A great practical example of a static method in a class is java.lang.Math:
```java
System.out.println("Square root of 27:" + Math.sqrt(27));
System.out.println("The larger number is:" + Math.max(5, 8));
// Notice how we call the Math class but don't need an object to make use of the methods sqrt or max?
```
java.lang.Math is an API, so we can even call the methods from it without referencing an instance of the class Math, so long as we have the API imported of course.

The keyword static can also be used as a class modifier. A class typically involves fields and methods, can be a class from an object of a class or a class itself (while not being in any instance of that class), a class can also have a class as one of its members. This is called an "inner class".
For the purpose of encapsulation, an inner class can be defined as static. E.g., here we have a static inner class called BinaryTreeNode. The fields in BinaryTreeNode are public so we don't have to get or set them, but we still have a good level of encapsulation.
```java
package dsaj;

import java.util.Iterator;
/**
  * Class BinaryTree models some operations of a binary tree.
  *
  * @author A Barnes
  *
  * @param <T>
  */
public class BinaryTree<T> implements Iterable<T>{

	protected BinaryTreeNode<T> root; // <T> is like a placeholder that keeps this memory address intact for the later created object being referenced.
		// Note that the <T> placeholder is a use of Java Generics.
	// constructs an empty tree
	public BinaryTree() {
	root = null;
	}

	/**
	  * Constructs a tree with just a root node
	  * @param element
	  */
	public BinaryTree(T element) {
	root = new BinaryTreeNode<T>(element);
	}
	
	/**
	  * Reset the tree to empty state
	  */
	public void clear() {
	root = null;
	}
	
	// OTHER METHOD DETAIL OMITTED
	
	/**
	  * Inner class for modelling a node on a binary tree.
	  * @author A Barnes
	  *
	  * @param <E>
	  */
	protected static class BinaryTreeNode<E> {
		public E element;
		public BinaryTreeNode<E> left;
		public BinaryTreeNode<E> right;
		/**
		  * Constructor for creating a leaf node
		  * @param element
		  */
		public BinaryTreeNode(E element) {
		this.element = element;
		left = null;
		right = null; // no children
		}
		
		/**
		  * Returns true if this binary tree node is a leaf node,
		  * i.e. a tree node with no children.
		  * @return Returns true if this is a leaf node;
		  * returns false otherwise.
		  */
		public boolean isLeaf() {
			return (left == null && right == null);
		}
	}// end of inner class
}
```

#Wrapper-Classes are classes used to put primitive data types into an object oriented context, e.g., collections of objects.
Java has some pre-built wrapper classes for the following:
- int = Integer
- short (16bit int) = Short
- long (32bit int) = Long
- float = Float
- double = Double
- char = Character
- boolean = Boolean
These wrapper classes can provide useful methods, like Integer.parseInt which takes a string and returns its numeric value (i.e., a String that contains only numbers, like "123").
We can also make our own wrapper classes, e.g., PureStack, a wrapper class that uses a java.util.Stack object to remodel the contents/operations of a pure "stack".
```java
package dsaj;
import java.util.Stack;
/** Class PureStack is a wrapper class which uses a java.util.Stack object
  * to model the contents and the operations of a pure stack.
  * @author S H S Wong
  */
public class PureStack<I> {

private Stack<I> contents;

/**
  * Constructor: creates a new java.util.Stack object to model
  * the contents and the operations of a pure stack.
  */
public PureStack() {
contents = new Stack<I>();
}

/**
  * Adds one element to the top of the stack.
  * @param the element to be added to the stack
  */
public void push(I item) {
contents.push(item);
}

/**
  * Removes and returns the top element from the stack.
  * @return the element at the top of the stack
  */
public I pop() {
return contents.pop();
}

/**
  * Returns the top element of the stack without removing it.
  * @return the element at the top of the stack
  */
public I peek() {
return contents.peek();
}

/** 
  * Returns the number of elements in the stack.
  * @return the number of elements in the stack
  */
public int size() {
return contents.size();
}

/**
  * Returns true if the stack contains no elements and false otherwise.
  * @return true if the stack contains no elements
  */
public boolean isEmpty() {
return contents.isEmpty();
}
}
```

#Interfaces help simplify common details between different classes. Such as different types of mammals, or different types of bank accounts.
![[{65037121-F3DA-4273-B00C-6186AEBC3479}.png | 600]]
An interface is a collection of constants (final fields that cannot be changed) and abstract methods (named methods with no bodies of logic).
```java
/**
  * A Java interface to model the complexity of a task
  *        e.g., an exam question
  */
  interface Complexity
  {
	  void setComplexity(int complexity);
	  int getComplexity();
}
```
This above interface has the abstract methods setComplexity and getComplexity.
A class using this interface would provide bodies of logic for each abstract method, meaning all interface methods are "public abstract".
A class that implements an interface will explicitly mention so in the header of the class.
```java
public class Questions implements Complexity
{
	int difficulty;
	public void setComplexity(int complexity);
	{
	difficulty = complexity;
	}
	public int getComplexity()
	{
		return difficulty;
	}
}
```
A class is only defined as implementing another class if it declares so in the header via the keyword =="implements"==.
Since Java 8, concrete methods can be included in interfaces if they hold the keyword =="default"==.
![[{B83A767E-F572-4758-B34D-6B7F9200A4E6}.png | 600]]
#Comparable is an interface in the java.lang package. It contains the method "compareTo" which returns a value based on the comparison of two specificed objects.
```java
int result = obj1.compareTo(obj2);
```
If obj1 < obj2 then compareTo will return a negative integer.
If obj1 = obj2 then it would be 0.
If obj1 > obj2 then it would be positive.
This method allows us to compare objects of the same type with some sort of order.
String objects can be compared by their alphabetical order, Integer objects can be compared by their numerical order, but an Object class cannot be compared by any pre-defined order. This is why we use compareTo.

#Iterator is an interface in the java.util package.
Iterator is used to move through classes that collect many objects one at a time.
Its primary methods are ==hasNext==, which returns a boolean value, and ==next==, which returns an object. It also has a method called ==remove==, which takes no parameters and returns no value, it only removes the most recently returned object by the ==next== method.
Since Java 8 ==remove== has been a ==default== method and throws an instance of ==UnsupportedOperationException== and does nothing else. 
If a class implements Iterator then it can override the regular implementation and use ==remove== as normal.
Also since Java 8, Iterator has gained a new ==default== method called ==forEachRemaining==.

#Iterable is another interface, from the java.lang package. It has a method called ==iterator== which takes no parameters and returns an Iterator over the given collection.
Collection classes that implement Iterable enable its objects to be used by the ==for== statement i.e., they can be iterated through individually using a "for-each" statement.
Since Java 8,==forEach== and ==spilterator== have been added to the Iterable interface. Both new methods are ==default==.

### Inheritance

#Inheritance is like reusing a mold for a toy, its a cheaper, quicker, easier way to make a new class.
The child class inheriting from the parent class will retain its variables and methods but can add its own.
#Protected is a modifier that's unique to inheritance. Alike ==private== it hides its fields from any other class, except that ==protected== fields are available to the child class of a parent class while still maintaining encapsulation to a degree.
The keyword #super lets a child class refer to its parent class, often used to refer to the parent class' constructor.
In the same way that a child class can inherit its parent class' variables and methods it can also override them unless it is defined as ==final==.

Child classes can also be the parent of another class, so inheritance can evolve into a #Class-Hierarchy.
![[{5E9EFB6D-059D-4B7E-A71E-0762280BAA06}.png | 600]]
All Java classes are based on the model of the ==Object== class. ==Object== class has a toString method which is often overriden, an equals method that tests if two objects are aliases is often overriden, hashCode method which returns the hash code value of an object. When two objects are determined as aliases by equals, their hash code value is identical, so both methods must be redefined if one is overriden.

Abstract classes are useful for conceptually abstract objects, like a "Vehicle".
Abstract classes are useful for implementing collection classes.
```java
package dsaj;

import java.util.Iterator;

public abstract class AbstractSet<T> implements setADT<T> {
	// IMPLEMENTATION DETAIL OMITTED.
}
```

We can also make hierarchies of interfaces.
A good example would be an Animal hierarchy:
- Animal interface (can eat) ->
- Domesticated interface (can be pet) ->
- Pet interface (lives indoors) ->
- Dog class (type of pet)

### Polymorphism
#Polymorphism refers to something having too many forms. 
A polymorphic reference is a reference variable that refers to different types of objects at different times.
Polymorphism leads to dynamic binding, which means that the binding of the call (reference) to the code (object) occurs during runtime and not compile time.
An object reference can also refer to any object of a class related to it by inheritance.
```java
Mammal pet;
Horse secretariat = new Horse();
pet = secretariat; // a valid assignment
```
The horse object reference in ==secretariat== is assigned to "pet", which is designed to keep a Mammal object reference. The "pet" variable acts as its pointing towards a Mammal object, even though it's actually pointing to the Horse object - this is polymorphism through inheritance.
Polymorphism can also occur through an interface and so any object that implements said interface.
```java
public interface Speaker
{
	void speak();
	void announce(String announcement);
}
```
Here we have implemented the classes "Philosopher" and "Dog". Both implement "Speaker", so the client class "Seminar" can keep object references for either "Philosopher" or "Dog".
```java
public class Seminar
{
	// The speakerof this seminar.
	private Speaker current;
	
	/**
	  * The constructor of a seminar object. This type of speakers for
	  * this seminar is dependent on the type of seminar.
	  */
	  public Seminar(char type)
	  {
		  switch(type)
		  {
			  case 'd': this.current = new Dog();
				  break;
			  default : this.current = new Philosopher();
					break;
					}
				}
			}
```
Since Java 7, the expression in a switch statement can use more than just primitive data types (such as char, byte, short, int) alongside complex expressions (such as Character, Byte, Short, Integer, String, enum).
![[{B4E92CD1-9A5D-4D28-9E6A-7A02C5B87EE0}.png | 600]]

Since Java 5.0, <T.> has been a placeholder available to use. We can use <T.> which means #Generic-type, to define a class without an actual type present until the class is instantiated.
![[{E094520C-7E01-4361-91FD-43371FAFB29A}.png | 500]]
![[{10CC27FB-C14E-43F3-8972-03D6204C5315}.png | 600]]
Note that Raffle does not explicitly use the keyword implement or extends (implements) so while it uses the Box class it is only a client.
Box is a generic class in this case. It uses a generic type (<T.>) for a field (class variable) that has not been explicitly defined until the later Raffle constructor.

## Type-casting VS. Generics
With Java 1.4x or below, when we access objects in a collection (such as objects stored in an ArrayList object) we have to cast explicitly. Below the ==Auction== class uses a showLots method to represent lots in an auction. It uses an #Iterator to go through objects in the ==lots== (in the ArrayList object) one by one.
When an object reference is retrieved in ==lots== using hasNext we have to cast it explicitly to avoid a run time error.
![[Pasted image 20251015201907.png | 600]]
Here we can only treat the objects in ==lots== as themselves when we use #Type-casting. This is due to the nature of collection objects - they are designed to keep object references of any type, not necessarily object references of the same type (i.e., iterated objects in a collection object). A regular collection object assumes that the elements in each collection object are instances of the ==Object== class, So when we explicitly type-cast we are then able to treat the object as its true self instead of an instance of the ==Object== class.
![[{E1E22D25-A945-492D-8CA0-93472C24223D}.png | 600]]
Generics were introduced in Java 5.0, making use of the Type variable gives us a cleaner approach to collection objects. Generic types remove the need for explicitly type-casting when accessing an object from a collection.
```java
import java.util.ArrayList;
import java.util.Iterator;
public class Auction
{
	// The list of Lots in this auction.
	private ArrayList<Lot> lots = new ArrayList<Lot>(); // a generic ArrayList
	
	/**
	  * Show the full list of lots in this auction.
	  */
	  public void showLots()
	  {
	  Iterator<Lot> it = lots.iterator(); // <Lot> is specifying what type of object is being passed through the Iterator.
	  while(it.hasNext())
	  {
		  Lot lot = it.next(); // No type casting is needed
		  
		  System.out.println(lot); // No need to invoke toString() explicitly
		  }
	}
}
```
The variable ==lots== is now expected to hold the object reference of an ArrayList object that keeps reference to Lot objects. Because of the generic type (Here it's Lot instead of T) there is no line needed to explicitly type-cast the Lot object class. The Iterator object can return the lots passed through without needing to return it as a String through toString (the method).
![[{4E44588C-D5F7-42FD-B762-86172C4A9BEA}.png | 600]]

## Standard for VS. Enhanced for
==showLots== can be implemented using a standard ==for== (loop) statement.
```java
	/** Show the full list of lots in this auction. */
	public void showLots()
	{
		for(Iterator<Lot> it = lots.iterator(); // Initialise step
			it.hasNext()                           // Test step
				              // No update step is needed
			)
		{
			// Retrieve the next element in the collection and output it.
			System.out.println(it.next());
		}
	}
```
Alongside ==for== we can implement showLots using an "enhanced" ==for== statement. This makes it easier to construct a for-loop, and is also known as a for/in or for-each loop. The above for-loop can be rewritten as so:
```java
	public void showLots() {
		for(Lot lot : lots) // Declare a lot variable
					 // that will hold each <Lot> object
					 // from the lots collection
			System.out.println(lot); // print each object out
		}
	}
```
The right hand side of the colon is a reference to a collection object, ==lots==, generally it can also be a reference to a static array but those are the only two things it can be.
Left hand side of the colon must be an element of the collection/static array i.e., Lot object.
==System.out.println(lot)== automatically calls lot.toString(), so the object is converted to a ==String== for printing.

Enhanced ==for== statements are simpler to write for iterating a collection of objects, but it relies on the use of java.util.Iterator. This means that if the collection object does not have said Iterator, the enhanced ==for== statement will fail.
If a collection object is intended to use enhanced ==for== then it needs to implement the Iterable interface. Note that while you do need to import Iterators, Iterable is within the java.lang package AKA its pre-included.
##### Interesting note below #####
![[{CC6A0A77-8CE2-42B8-8761-0D86CF5D7A48}.png | 600]]

There are 3 ways we can handle #Exceptions.
- Don't handle it -> program crashes and results in error.
- Handle it where it occurs.
- Handle it elsewhere.
If you handle it where it occurs, you use a try/catch block around the risky code.
```java
try {
    // risky code
} catch (IOException e) {
    // handle the I/O error
}
```
Code within "finally" blocks always run even against exceptions occurring, which is good for closing resources like files.
Beyond Java 7, you can close files without "finally":
```java
public static String readFirstLineFromFile(String path) throws IOException
{
    try (BufferedReader br = new BufferedReader(new FileReader(path))) {
        return br.readLine();
    }
}
```
The resource ==BufferedReader== is declared inside the parentheses of the ==try== statement. Java automatically closes it when the try block finishes — whether the code completes normally or an exception is thrown.
![[{E761C43C-8333-465C-8C43-A0D5FD864253}.png | 600]]
