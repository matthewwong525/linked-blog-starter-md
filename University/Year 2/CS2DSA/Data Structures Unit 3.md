Note that [[Data Structures Unit 1]] was made purely from my own notes, whereas this [[Data Structures Unit 2]] and this Unit 3 has been made with assistance from claude.ai to summarise chapters.
## Abstract Data TYPES (adtS)
An #ADT is a mathematical specification of set of data and the operations that can be performed on that set of data. This data set is *abstract* in that the focus is the properties of the data and behaviour of the operations, the actual structure of the data(e.g., array, linked list) is not specified nor the implementations of the operations (e.g., iteration) acting on the set of data.
With an ADT we know the logical structure of the data type (linear, hierarchically, ordered or unordered etc) and what we can do with it.
An example of ADT can be a string, list, stack, queue, set, map, tree or even a rational number (like a fraction or something).
ADTs can be implemented in many ways such as a stack being implemented using an array or linked list.

A collection is an object that hosts a group of objects, usually a fixed type. These objects can be organised in different ways depending on the collection type.
Collections are categorized as:
- Unordered: No logical order between elements
- Linear: Elements arranged in a straight line (each followed by a unique next element)
- Nonlinear: Elements arranged hierarchically or in a network
![[{4409FA93-EED8-438F-9443-2CCA035D7134}.png | 600]]
These objects are usually ordered by the order they were added (like a queue) or by their relationships (like alphabetical order).
Internal storage structure doesn't have to match logical structure, a list can appear logically linear but be stored in a binary search tree for faster searching.

Collections can also be catorigsed as :
- #Bounded - there is a limit to the number of elements that the collection can contain (size/capacity) such as arrays.
- #Unbounded - there is no limit on the size of the collection beyond machine memory such as ArrayList
All collections should provide the methods ==isEmpty()== to check if its empty and ==size()== to check its element count.
Bounded collections specifically need ==isFull()== to check if the collection has reached the maximum capacity and ==capacity()== to check the maximum possible size.

A collection is an abstraction in the sense that it separates interface from implementation (what client classes can do, how it works internally). Java interfaces define these operations.
This makes the collection flexible - you can swap implementations without affecting the client code e.g., replacing ArrayList with a LinkedList without changing any code in the collection. We obtain this benefit because the Iterator interface handles all these operations itself whereas we don't have to indulge on how the Iterator works with an ArrayList vs. a LinkedList.
![[{0C948C64-E00D-451B-8FD7-2E75B0A53D41}.png | 600]]
Collections are useful in that any computer software will often work with a large number of homogeneous objects. If we understand the properties of these collections we can make more informed decisions, here are some issues of collections we should consider:
- How does it operate conceptually?
- What is its formal interface definition?
- What problems does it solve?
- How might it be implemented?
- What are the benefits and costs (storage and execution time)?

#Interfaces are ideal for defining collection ADTs because of how they acknowledge abstract methods. Interfaces don't contain data members so they provide a simple and abstract view of operations.
Java interfaces on their own are incomplete though, they need classes with fields to utilise those elements.
The operations that work on a collection of objects are largely independent of the nature of those objects.
From this we can gather that classes and interfaces in the context of collection structures should be ==generic==.

![[{EE87FD3A-AE49-4A0E-9653-35871DAE15E7}.png | 600]]
Stacks are #LIFO (Last in, First out) linear collections. They involve the following operations:
- `push(element)` — add to top
- `pop()` — remove and return top element
- `peek()` — return top element without removing
- `isEmpty()`, `size()` — standard collection operations

![[{3CE544A2-6FA9-4296-930A-019C8591607D}.png | 500]]

Stacks are formally defined through a Java interface. Here's the UML representation and the full code:
```java
//********************************************************************
// StackADT.java Adapted from Lewis/Chase
// Defines the interface to a stack data structure.
//********************************************************************
package dsaj;

public interface StackADT<T> {
    /**
     * Adds one element to the top of the stack.
     */
    public void push(T element);

    /**
     * Removes and returns the top element from the stack.
     */
    public T pop();

    /**
     * Returns the top element of the stack without removing it.
     */
    public T peek();

    /**
     * Returns true if the stack contains no elements and false otherwise.
     */
    public boolean isEmpty();

    /**
     * Returns the number of elements in the stack.
     */
    public int size();
}
```
**Note:** The methods use generics (`<T>`), meaning the stack can store any type of object. When you create a stack, you specify what type of elements it holds (e.g., `StackADT<String>` for strings, `StackADT<Integer>` for integers).
For bounded stacks with a maximum capacity, the interface is extended:
```java
//********************************************************************
// BoundedStackADT.java Author: Alan Barnes
// Extends the interface StackADT with methods for bounded stacks.
//********************************************************************
package dsaj;

public interface BoundedStackADT<T> extends StackADT<T> {
    /**
     * Returns true if the stack contains no room for more
     * elements to be added and false otherwise.
     */
    public boolean isFull();

    /**
     * Returns the maximum number of elements the stack can hold
     */
    public int capacity();
}
```
This interface extends `StackADT<T>`, so bounded stacks inherit all the basic stack operations plus the two new bounded-specific methods.

Rather than creating a separate `BoundedStackADT` interface, a more flexible approach is to define a separate `Bounded` interface and have classes implement both:
```java
//********************************************************************
// Bounded.java Author: Alan Barnes
//
// Defines the interface for a collection with limited capacity.
//********************************************************************
package dsaj;

public interface Bounded
{
    /**
     * Returns true if the collection contains no room for more
     * elements to be added and false otherwise.
     */
    public boolean isFull();

    /**
     * Returns the maximum number of elements the collection can hold
     */
    public int capacity();
}
```
With this approach, a bounded stack would implement both `StackADT<T>` and `Bounded`. This is more flexible because the `Bounded` interface can be reused by other bounded collections (queues, lists, etc.) without code duplication.

The stack ADT is an abstraction—it specifies what operations are available and what they do, but doesn't dictate how the stack is implemented. A stack could be implemented using:

- An array
- A linked list
- Any other data structure

Regardless of implementation, any class that implements `StackADT<T>` provides the same interface. Client code can use the stack without knowing or caring about the internal structure.

Stacks are used in many real-world scenarios:

- **Undo/Redo functionality** — each action is pushed onto a stack; undo pops the most recent action
- **Function call stacks** — the runtime uses a stack to manage function calls and local variables
- **Expression evaluation** — converting infix to postfix notation or evaluating postfix expressions
- **Browser back button** — visited pages are pushed onto a stack; back button pops to the previous page
- **Depth-first search** — exploring tree or graph structures

A queue is a #FIFO (First-in, First-out) linear collection with openings at both ends. Elements are added at the same end they're removed.
![[{21BEC6AD-FFDB-42DB-877E-7D1F464B22EA} 1.png | 600]]
Some of its operations include:
- `enqueue(element)` — add to tail
- `dequeue()` — remove and return head element
- `first()` — return head element without removing
- `isEmpty()`, `size()` — standard operations
Queues are different to Stacks in that their operations occur at different areas, a pure queue also doesn't allow access to middle elements also.
![[{26A8046F-82E2-40F5-9F3D-999927B8133C}.png | 500]]

Lists are flexible linear collections, unlike Stacks or Queues elements can be added or removed at any point. Lists also support searching without access restrictions.
![[{5117EAFE-6D83-4F06-88DA-B294BBCADDF0}.png | 600]]
Some operations include:
- `removeFirst()`, `removeLast()`, `remove(element)` — remove operations
- `first()`, `last()` — access first/last
- `contains(target)` — search operation
- `isEmpty()`, `size()` — standard operations
Unlike stacks and queues, lists don't define a specific `add` operation in the interface because different list types add elements differently. Specific list types extend `ListADT` to define their own add behavior, as the way you add items is dependent on the list type.
```java
// ListADT.java Authors: Lewis/Chase (Modified by Wong)
// Defines the interface to a general list collection. Specific
// types of lists will extend this interface.
package dsaj;

public interface ListADT<T> extends Iterable<T> {
    /**
     * Removes and returns the first element from this list.
     */
    T removeFirst();

    /**
     * Removes and returns the last element from this list.
     */
    T removeLast();

    /**
     * Removes the specified element from this list.
     */
    boolean remove(T element);

    /**
     * Returns a reference to the first element in this list.
     */
    T first();

    /**
     * Returns a reference to the last element in this list.
     */
    T last();

    /**
     * Returns true if this list contains the specified target element.
     */
    boolean contains(T target);

    /**
     * Returns true if this list contains no elements.
     */
    boolean isEmpty();

    /**
     * Returns the number of elements in this list.
     */
    int size();
}
```
**Key points about this interface:**
- It extends `Iterable<T>`, which means any class implementing `ListADT` automatically inherits the `iterator()` method
- It doesn't include an explicit `add()` method because different list types add elements differently (ordered vs. unordered, for example)
- The document notes that specific list types would extend this interface to define their own add behavior
- Like stacks and queues, it uses generics to work with any element type

#Sets can be thought as a collection of distinct objects of a particular type.
Objects can only appear once in a set.
Sets have no order.

Like most collections, sets need basic operations to manage their contents:
- **Determine if empty:** Check whether the set contains any elements
- **Determine size:** Return the number of elements in the set
- **Add elements:** Add one or more specified elements to the set
- **Remove elements:** Remove one or more specified elements from the set
- **Remove all except specified:** Remove every element from a set except those in a specified set

Sets have unique operations that reflect their mathematical properties:
- **contains(element)** — determine if a particular element a is a member of the set (test if a ∈ A)
**Union (A ∪ B):** Produces a new set containing all elements that appear in A or B (or both). Elements that appear in both sets appear only once in the result because sets contain distinct elements.
- Example: {d, e, n} ∪ {d, a, n, i} = {d, e, a, n, i}

**Intersection (A ∩ B):** Produces a new set containing only those elements that are members of both A and B.
- Example: {d, e, n} ∩ {d, a, n, i} = {d, n}

**Difference (A \ B):** Produces a new set containing all elements of A that are not members of B.
- Example: {d, e, n} \ {d, a, n, i} = {e}

**Equals:** A predicate that determines if two sets A and B have the same members. Importantly, this must ignore any internal ordering of elements in the underlying data structure. For example, {a, e, i, o, u} and {u, o, i, e, a} should be regarded as equal even though their internal representation differs. To achieve this, any implementation must override the `equals()` method inherited from the Object class.

**isSubset (A ⊆ B):** Determines if set A is a subset of B. A is a subset of B if every member of A is also a member of B. Note that a set is a subset of itself, and the empty set is a subset of any set.

While not as fundamental as the above operations, the following are often provided:
- **pick()** — select and return a random element from the set without removing it. This reflects the unordered nature of sets by allowing arbitrary access.
- **removeRandom()** — select and remove a randomly chosen element from the set.
- **iterator()** — provide an iterator so elements can be processed one by one. To properly reflect the unordered nature of a set, this could present elements in random order or, for efficiency, might use the internal ordering of the underlying data structure.
This is the Java interface for a set ADT:
```java
//********************************************************************
// SetADT.java Author: Alan Barnes
// Defines the interface to a set collection.
//********************************************************************
package dsaj;

/* We make SetADT<T> extend the interface Iterable<T> so as to make
 * it possible for us to use enhanced for loops with sets 
 */
public interface SetADT<T> extends Iterable<T>
{
    /**
     * Adds the element to the set if not already present and returns true.
     * If the element is already present, the set is not modified
     * and false is returned.
     */
    public boolean add(T element);

    /**
     * Adds all elements of set A to this set
     * Returns true if the set is modified, otherwise false
     */
    public boolean addAll(SetADT<T> A);

    /**
     * Removes the element from the set if it is present and returns true
     * If the element is not present, the set is not modified
     * and false is returned.
     */
    public boolean remove(T element);

    /**
     * Removes all the elements of set A from this set.
     * Returns true if the set is modified, otherwise false
     */
    public boolean removeAll(SetADT<T> A);

    /**
     * Removes all the elements from this set except those in set A.
     * Returns true if the set is modified, otherwise false
     */
    public boolean retainAll(SetADT<T> A);

    /**
     * Returns true if this set contains the specified element
     */
    public boolean contains(T element);

    /**
     * Returns a new set which is the union of this set and set A
     */
    public SetADT<T> union(SetADT<T> A);

    /**
     * Returns a new set which is the intersection of this set and set A
     */
    public SetADT<T> intersection(SetADT<T> A);

    /**
     * Returns a new set which is the difference of this set and set A
     */
    public SetADT<T> difference(SetADT<T> A);

    /**
     * Returns true if this set and the set A contain exactly
     * the same elements
     */
    public boolean equals(SetADT<T> A);

    /**
     * Returns true if this set is a subset of set A
     */
    public boolean isSubset(SetADT<T> A);

    /**
     * Returns true if this set contains no elements
     */
    public boolean isEmpty();

    /**
     * Returns the number of elements in this set
     */
    public int size();
}
```

A set is an unordered collection of distinct elements, whereas a #multi-set or bag is a generalised rendition of a set.
While a set contains distinct elements with each appearing at most once, a multi-set allows the same element to appear multiple times.

The multiplicity (count) of elements matters. The multi-set {a, a, e, i} with 4 elements is different from {a, e, i} with 3 elements. When you add an element that already exists, the multi-set changes because that element now occurs one additional time.
Like sets, the order in which elements are listed is irrelevant. {a, a, e, i} = {e, a, i, a} = {i, e, a, a}.

Multi-sets are useful for modelling collections where duplicates are meaningful:
- A bag of marbles (multiple of the same color)
- Inventory tracking (quantity of each item)
- Frequency analysis (counting occurrences of words or characters)
Multi-sets share some operations with sets:

- `isEmpty()` — check if empty
- `size()` — return total number of elements (including duplicates)
- `contains(element)` — check membership
```java
//********************************************************************
// MultisetADT.java Author: Alan Barnes
//
// Defines the interface to a multi-set collection.
//********************************************************************

package dsaj;

/* We make MultisetADT<T> extend the interface Iterable<T> so as to make
 * it possible for us to use enhanced for loops with multi-sets 
 */
public interface MultisetADT<T> extends Iterable<T>
{
    /**
     * Adds the element to the multi-set and returns true
     */
    public boolean add(T element);

    /**
     * Adds all elements of multi-set A to this multi-set
     * Returns true if the multi-set is modified, otherwise false
     */
    public boolean addAll(MultisetADT<T> A);

    /**
     * Removes the element from the multi-set if it is present and returns true
     * If the element is not present, the multi-set is not modified
     * and false is returned.
     */
    public boolean remove(T element);

    /**
     * Removes all elements of A from this multi-set
     * Returns true if the multi-set is modified, otherwise false
     */
    public boolean removeAll(MultisetADT<T> A);

    /**
     * Removes all elements from this multi-set
     * except those that are in A.
     * Returns true if the multi-set is modified, otherwise false
     */
    public boolean retainAll(MultisetADT<T> A);

    /**
     * Returns a new multi-set which is the union of this multi-set and A
     */
    public MultisetADT<T> union(MultisetADT<T> A);

    /**
     * Returns a new multi-set which is the sum of this multi-set and A
     */
    public MultisetADT<T> sum(MultisetADT<T> A);

    /**
     * Returns a new multi-set which is the intersection
     * of this multi-set and A
     */
    public MultisetADT<T> intersection(MultisetADT<T> A);

    /**
     * Returns a new multi-set which is the difference
     * of this multi-set and A
     */
    public MultisetADT<T> difference(MultisetADT<T> A);

    /**
     * Returns true if this multi-set and A contain
     * exactly the same elements
     */
    public boolean equals(SetADT<T> A);

    /**
     * Returns true if this multi-set contains the element
     */
    public boolean contains(T element);

    /**
     * Returns true if this multi-set is a sub-bag of A
     */
    public boolean isSubbag(MultisetADT<T> A);

    /**
     * Returns the number of times element appears in this multi-set
     */
    public int count(T element);

    /**
     * Returns true if this multi-set contains no elements
     */
    public boolean isEmpty();

    /**
     * Returns the number of elements in this multi-set
     */
    public int size();
}
```

#Maps are ADTs that map a set of keys to a set of values. Each key is associated with one value.
![[{406CB609-EE06-4AC8-B152-5F6C83C32288}.png | 600]]
The type operations of the map ADT include:
- Add (associate a new value with a new key in the map)
- Reassign (associate an existing key in the map with a new value)
- Remove (remove a key with its associated value from the set of key-value pairs in the map)
- Lookup (find the value, if any, in the map that is associated with a given key)
```java
//*********************************************************************
// MapADT.java Author: Sylva Wong
//
// Defines the interface to a map collection.
//********************************************************************

public interface MapADT<K,V>
{
    /**
     * Adds a new key-value pair to the map.
     */
    public void add(K key, V value);

    /**
     * Removes a key with its associated value from the map
     * and returns the associated value.
     */
    public V remove(K key);

    /**
     * Returns the value (if any) associated with the given key.
     */
    public V lookup(K key);

    /**
     * Associate an existing key in the map with a new value and
     * returns the old value associated with the key.
     */
    public V reassign(K key, V newValue);
}
```
A map is also known as a #dictionary, associative array and lookup table.
Maps can be used for the following:
- modelling the records in an address/phone book
- modelling the records in a database table
- modelling any lookup table
