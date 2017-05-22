
## SOLID - Design Principles  ##
 - **S** - Single Responsibility 
 - **O** - Open/Close principle
 - **L** - Liskov substitution principle
 - **I** - Interface segregation principle
 - **D** - Dependency inversion

### Single responsibility  ###
Every class or module of a software should have responsibility over a single part of the functionality provided by the software, and that responsibility should entirely be encapsulated by the class. So that, a change made in this class or module doesn't affect the other modules of the software.

### Open/Close principle ###
A class should be open for extension, but closed for modification. 
Open/Close principle can be ensured by the use of abstract classes and concrete classes for implementing the behaviour of abstract classes.
This ensures that concrete classes extend the abstract classes, instead of changing them. Some examples of this are Template Pattern and Strategy Pattern.

### Liskov Substitution principle ###
Functions that uses pointers or references to base class must be able to use objects of derived class without knowing it.
A typical example which violates this principle is the 

