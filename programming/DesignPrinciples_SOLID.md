
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
LSP is about when to extend a class vs use an other strategy to achieve your goal.
A good example of LSP is the board & the 3D board.
![Board & 3D-Board](https://oncodebynotmyself.files.wordpress.com/2011/03/board_thumb.png)
When we are extedning the board class to 3d board, we have to re write all the AddUnit(),GetTile(),GetUnits(),RemoveUnits() methods because now these methods in the board class would support only the x&y co-ordinates but z co-ordinate should be supported for 3d board.
[Stackoverflow example](https://stackoverflow.com/questions/56860/what-is-the-liskov-substitution-principle)
