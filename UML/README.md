## 1. Inheritance (Generalization)

### Use Case
 Represents an "is-a" relationship. It signifies that a subclass is a specialization of the parent class, inheriting its attributes and behaviors.
### Example
 In the given example, Dog is a specific type of Animal, inheriting the eat() method from the base class.
### Additional Notes

Inheritance allows code reuse and promotes a hierarchical organization of classes.
The base class (or superclass) provides a common interface or behavior, and subclasses (or derived classes) extend or specialize this behavior.
## 2. Implementation (Realization or Execution)

### Use Case
 Represents a relationship between an interface (abstract class or pure virtual class) and its concrete implementation. The concrete class "realizes" or "implements" the functionality defined by the interface.
 ### Example
  The Circle class implements the abstract Shape class, providing a concrete implementation for the draw() method.
### Additional Notes
Interfaces provide a way to define a contract without specifying the implementation details.
Classes that implement an interface must provide a concrete implementation for all the methods declared in the interface.
## 3. Dependency

### Use Case
 Represents a "uses-a" relationship. It indicates that one class depends on another class, meaning that a change in the definition of the dependent class may affect the class that depends on it.
### Example 
The Service class depends on the Logger class for logging functionality.
### Additional Notes

Dependency is a more generic relationship compared to association. It signifies a weaker connection between classes.
## 4. Association

### Use Case
 Represents a "has-a" relationship. It indicates that two classes are associated with each other, meaning that one class has a reference to another.
### Example
 The Car and Driver classes are associated through the CarDriverAssociation class.
### Additional Notes

The association can be one-to-one, one-to-many, or many-to-many.
Arrows at the ends of the line can indicate the direction of the association, showing which class is aware of the other.
## 5. Aggregation

### Use Case 
Represents a "whole-part" relationship. It indicates that one class is composed of or has a collection of objects of another class.
### Example 
The Company class aggregates Department and Employee classes.
### Additional Notes

Aggregation implies a weaker relationship compared to composition.
The aggregated class can exist independently of the container class.
## 6. Composition

### Use Case
 Represents a stronger form of "whole-part" relationship than aggregation. It indicates that one class is composed of or has a collection of objects of another class, and the parts cannot exist without the whole.
### Example
 The CarComposition class composes the Engine class.
### Additional Notes

Composition implies a stronger ownership relationship compared to aggregation. The lifecycle of the part is tied to the lifecycle of the whole.

![image](../Images/relationships-between-classes.pngrelationships-between-classes.png)