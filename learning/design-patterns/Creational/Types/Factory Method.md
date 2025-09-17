**Factory method** is a creational design pattern which solves the problem of creating product objects without specifying their concrete classes.

The Factory Method defines a method, which should be used for creating objects instead of using a direct constructor call (`new` operator). Subclasses can override this method to change the class of objects that will be created.

**Key Points**:
- The method in the interface returns an instance of a product.
- Subclasses override the method to change the class of objects that will be created.
- Promotes loose coupling by reducing dependency on specific implementations.

**Example**: 
1. A document creation framework where each type of document (PDF, Word, etc.) has a different factory method.
2. Production of cross-platform GUI elements

