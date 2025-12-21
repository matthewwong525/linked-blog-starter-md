Note that [[Data Structures Unit 1]] was made purely from my own notes, whereas this [[Data Structures Unit 2]], [[Data Structures Unit 3]] and this Unit 4 has been made with assistance from claude.ai to summarise chapters.

## Working with Arrays
We can define arrays using primitive types like int or double, or user-authored classes, using the following form:
```java
int[] a;
a = new int[10];

double[] b = new double[20];

int[] c = {5, 2, 1, 4};
```
Line 1 declares a variable "a" that can hold a #Reference to an array object, type int.
Line 2 allocates storage for an array object size 10 (0-9) which can be accessed using the notation "a[1], ..., a[9]".
![[{D3091C7E-2AE5-4C35-B865-12C27409FD70}.png]]
Array elements are initialised to a zero-bit pattern, so an int array's elements are all initialised to 0 and arrays of reference types they are null. Boolean arrays initialise to false.
Line 4shows how we can declare an array variable and also allocate storage for it in a single declaration.

We can also allocate storage for an array object and initialise it using array aggregation. This can only be done when declaring new array variables however, not when re-initialising arrays that have already been created.
```java
double d = new double[4] = {1.0, 2.0, 3.0, 4.0};   // !!! ERROR
```
The number of elements in an array can be accessed through the final field "length" of the array. Typically this is used in a loop to process each array element.
```java
for (int i = 0; i < a.length; i++) {
	a[i] += 2; // add 2 to each element of array a
	}
```
Enhanced for loops are often more convenient.
```java
for (double elem : b) {
	elem  -elem; // change the sign of each element for array b
	}
```
## Time Complexity of Array Operations
Accessing array elements is fast, O(1), as it involves calculating the address of the array element and then accessing the data of that address. Processing a 1-D array of size n will involve a loop being executed n times. If one element is O(1), the entire process is O(n).
```java
// increase the salary of each grade point by 1%
for (int 1 = 0; i < salaries.length; i++) {
	salaries[i] += salaries [i] * 0.01;*
	}
```
If a company increases all salaries by 1% then each element of the array needs have that increase applied. The operation in line 4 does not depend on the size of the array, so it executes at O(1). Completing the salary increase process is dependent on the array "salaries" size, so the loop is O(n) where n is the length of the array.

## A Bounded Stack Implementation
Once storage for an array is allocated, it has fixed size for its
lifetime. Array-based collections therefore have maximum size (bounded
collections).
ArrayStack implements BoundedStackADT:
- The stack grows upward from array start as items are pushed, shrinks as
items are popped.
- An int variable currentSize tracks the stack top position (index of
first free location).
- A clear method empties the stack (sets currentSize to 0).
```java
public class ArrayStack<T> implements BoundedStackADT<T> {
	private static final int DEFAULT_CAPACITY = 100;
	
	private T[] elems; // an array to hold the stack elements
	private final int maxSize; // maximum capacity of the stack
	private int currentSize; // its current size
	
	/** Construct a new empty stack with the specified capacity */
	@SuppressWarnings("unchecked")
	public ArrayStack(int maxSize) {
	elems = (T[]) (new Object[maxSize]);
	currentSize = 0;
	this.maxSize = maxSize;
}

/** Construct a new empty stack with default capacity */
public ArrayStack() {
	this(DEFAULT_CAPACITY); // call the one argument constructor above
}

@Override
public int size() {
	return currentSize;
}

@Override
public boolean isEmpty() {
	return (currentSize == 0);
}

@Override
public int capacity() {
	return maxSize;
}

@Override
public boolean isFull() {
	return (currentSize == maxSize);
}

@Override
public void push(T element) {
	// check if the stack is full
	if (currentSize == maxSize) {
	throw new IllegalStateException("Stack full in method push");
}
// add the element at the top of the stack
elems[currentSize] = element;
// increase the size by 1
currentSize++;
}

@Override
public T pop() {
	// check if the stack is empty
	if (currentSize == 0) {
		throw new IllegalStateException("Stack empty in method pop");
	}

	// decrease the size of the stack by 1
	currentSize--;
	// return the element on top of the stack
	return elems[currentSize];
}

@Override
public T peek() {
	// check if the stack is empty
		if (currentSize == 0) {
		throw new IllegalStateException("Stack empty in method peek");
	}

	// return the element on top of the stack
	// N.B. the index of the top element is one less than currentSize
	return elems[currentSize - 1];
	}

// empty the stack
public void clear() {
	currentSize = 0;
	}
}
```
Two constructors appear above:
- a constructor with no argument (line 17) allocates an empty stack with a capacity of 100 (defined on line 2).
- The user can also specify a capacity by using the argument constructor on line 9.
Java forbids creation of a generic type array, so the type Object must be created and a cast is necessary on lines 10 to convert it to type T[].
Another way of creating a generic array is using the static method newInstance in java.lang.reflect.Array to create a new array with the type and length:
```java
import java.lang.reflect.Array;

// details omitted

/** Construct a new empty stack with the specified capacity */
@SuppressWarnings("unchecked")
public ArrayStack(int maxSize) {
	// another way to create a generic array
	elems = (T[]) Array.newInstance(Object.class, maxSize);
	currentSize = 0;
	this.maxSize = maxSize;
}

// details omitted
```
The class ArrayStack inherits 7 methods from the BoundedStackADT interface which is a sub-interface of Bounded and QueueADT. To ensurethe Java compiler knows that those 7 inherited methods have been overridden in class ArrayStack and that the compiler would not treat them as new methods, each of those 7 methods is marked using the annotation @override.
- Lines 22 – 39: the implementation of the four accessor methods isEmpty, isFull, size and capacity is straightforward.
- Lines 42 – 51: push first checks to see if the stack is full and if so throws an unchecked exception. Otherwise it stores the element at the top of the stack and increases the size of the stack by one. Note: currentSize is the index of the first free location above the top of the stack.
- Lines 54 – 64: pop first checks to see if the stack is empty and if so throws an exception. Otherwise it decreases the size of the stack by one and returns the item at the (old) top of the stack.
- Lines 67 – 71: peek first checks to see if the stack is empty and if so throws an exception. Otherwise it simply returns the item at the top of the stack. clear simply sets the currentSize of the stack to zero effectively making the elements currently in the stack inaccessible to clients. A look at the implementation of the methods of ArrayStack reveals that none of the methods involve any looping constructs, and so all will execute in constant time, i.e. the time complexity T (n) = O(1).
## Implementing an Unbounded Stack using Array
Due to the static nature of an array, they are not a typical choice for implementing unbounded collections. It's possible to expand the storage capacity of an array automatically however.
To "expand" its capacity, we have to make a new, larger array and copy all the existing elements to it.
```java
private void expandCapacity() {
	/* Create a new larger Object array that can hold twice
	 * as many elements as the old one and cast this Object array 
	 * to a T array, where T is a type variable
	T() larger = (T[]) new Object[contents.length*2]);]
	
	// Copy elements in the older array to the new one individually.
	for (int index=0; index < contents.length; index++) {
		larger[index] = contents[index];
		}
	// Update the contents of this stack using the new arrau
	contents = larger;
	}
```
At each push operation, before adding an element to the stack, the capacity of the stack is checked. If the array is full, expandCapacity is called before the element is pushed. This is only needed when using bounded stacks.
