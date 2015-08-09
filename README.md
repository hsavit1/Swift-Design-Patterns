#### A discourse in design patterns. Based off the wonderful book _Pro-Swift-Design-Patterns_. Please go grab a copy

# Themes
- tightly coupled components are the antithesis of design patterns. Two components are tightly coupled when one depends on the inner workings of another, or, put another way, when you can make a change to one component without also updating the other.
- item
- item

======
======
======
======


# Creation Patterns
1. The Object Template Pattern
2. The Prototype Pattern
3. The Singleton Pattern
4. The Object Pool Pattern
5. Object Pool Variations
6. The Factory Method Pattern
7. Abstract Factory Pattern
8. The Builder Pattern 

# Structural Patterns
1. The Adapter Pattern
2. The Bridge Pattern
3. The Decorator Pattern
4. The Façade Pattern
5. The Flyweight Pattern
6. The Proxy Pattern

# Behavioral Patterns
1. The Chain of Responsibility Pattern
2. The Command Pattern
3. The Mediator Pattern
4. The Observer Pattern
5. The Memento Pattern
6. The Strategy Pattern
7. The Visitor Pattern

=====
=====
=====
=====

# Creational 

###The Object Template Pattern

####What
The object template pattern uses a class or struct as the specification for the data types and logic for a given data type. Objects are created using the template, and values for the data are set during initialization, either through the use of default values in the template or using values provided by the component to the class or struct initializer, also known as the constructor.
    
####Why
The object template pattern provides the foundation for grouping data values and the logic that manipulates them together, known as encapsulation. Encapsulation allows an object to present an API to its consumers while hiding the private implementation of that API. This helps prevent the tight coupling of components.
    
####How
The object template pattern uses a class or struct to define a template from which objects are created. When an application component requires an object, it calls on the Swift runtime to create it by specifying the name of the template and any runtime initialization data values that are required to configure the object
    
------

###The Prototype Pattern

####What
The main benefit is to hide the code that creates objects from the components that use them; this means that components don’t need to know which class or struct is required to create a new object, don’t need to know the details of initializers, and don’t need to change when subclasses are created and instantiated. This pattern can also be used to avoid repeating expensive initialization each time a new object of a specific type is created.
   
####Why
The object template pattern provides the foundation for grouping data values and the logic that manipulates them together, known as encapsulation. Encapsulation allows an object to present an API to its consumers while hiding the private implementation of that API. This helps prevent the tight coupling of components.

####How
The prototype pattern uses an existing object—rather than a class or struct—to create new objects. This is often referred to as cloning, since the new object is an identical copy of the existing one, including any changes made to the object’s stored properties that have been made since it was created
    
####Your Moment of Zen
````
func copyWithZone(zone: NSZone) -> AnyObject {
    return Sum(first:self.firstValue,
		second: self.secondValue,
        cache: self.resultsCache);
}
````

------

###The Singleton Pattern

####What
   
####Why

####How
    
####Your Moment of Zen

------

###The Object Pool Pattern

####What
   
####Why

####How
    
####Your Moment of Zen

------

###Object Pool Variations

####What
   
####Why

####How
    
####Your Moment of Zen

------

###The Factory Method Pattern

####What
   
####Why

####How
    
####Your Moment of Zen

------

###Abstract Factory Pattern

####What
   
####Why

####How
    
####Your Moment of Zen

------

###The Builder Pattern 

####What
   
####Why

####How
    
####Your Moment of Zen

------

    