# Value and Reference type

The general difference is that reference types lives on a heap which has a pointer to the data on a stack, whereas value types are inline, that is they are only in that context where your variable is created, until an explicit reference is passed. Value types are stored on a stack. 

A value type holds data within its memory.
A reference type variable holds a pointer, or a reference to the address where the data is stored.

When a value type is copied, it copies all the data into new variable, whereas the reference type when copied still points to the original object.

Value types always contains a valuee, unless nullable types are declared.
Reference types can have null reference.

Class is a reference type.
Struct is a value type.

Both support interface.

Inheritance is only supported by clasess 
