# Introduction to python interpreter (Python 2.7)
>gist of the blog on python interpreter from http://akaptur.com/


## Functions and objects
```python
>>> a = "hello"
```
>What exactly happens when i press enter after typing in this code?? :unamused:

Four steps happen when that line of code is to be excuted: lexing,parsing,compiling and interpreting.
__**Lexing**__ is breaking of the code you just typed into tokens. The __**parser**__ takes these tokens and 
generates a structure that shows their relationship to each other(Abstarct syntax tree).The __**compiler**__ then takes
the AST and turns it into code objects. Then the __**interpreter**__ takes each of these code objects and executes the code
it represnts.

Note: Function objects, Code objects and bytecode are all different things. 

### Function Objects
Function objects are the "function objects". Functions are first-class objects (In short, first class objects means it is same as other objects, there no exclusive restrictions on how we can use them) in python, like a list is an object or an isntance of ```MyObject``` is an object.

```python
>>> def  foo(a):
...     x= 3
...
>>> foo
<function foo at 0x02261B30>
```

In the above example, we are not invoking foo(There is difference between ```foo()``` and ```foo```). We can pass ```foo``` as 
an argument, or we can bind it to another name(```function_name = foo```). 

### Code Objects

```python
>>> def  foo(a):
...     x= 3
...
>>> foo
<function foo at 0x02261B30>
>>> foo.func_code
<code object foo at 02216C80, file "<stdin>", line 1>
```
As you can see, code object is an attribute of the function object. Function object has lot of other attributes too. 
A code object is generated by the python compiler and interpreted by the interpreter. It contains information that the interpreter
needs to interpret. Let's look at the attributes of the code object.
```python
>>> dir(foo.func_code)
['__class__', '__cmp__', '__delattr__', '__doc__', '__eq__', '__format__', '__
__', '__getattribute__', '__gt__', '__hash__', '__init__', '__le__', '__lt__',
__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__',
_sizeof__', '__str__', '__subclasshook__', 'co_argcount', 'co_cellvars', 'co_c
e', 'co_consts', 'co_filename', 'co_firstlineno', 'co_flags', 'co_freevars', '
_lnotab', 'co_name', 'co_names', 'co_nlocals', 'co_stacksize', 'co_varnames']
```
>dir() is an in-built python function, which tries to give some info about the object like the attributes in that module
namespace.

Even i don't understand a bunch of that stuff, but the blog post which i am referring to asks us to look at three attributes.
```python
>>> foo.func_code.co_varnames
('a', 'x')
>>> foo.func_code.co_consts
(None, 3)
>>> foo.func_code.co_argcount
1
```
By looking at these above arguments, we can make out that the code object gives the information needed by an interpreter to understand
a piece of code or a code block. But so far, we haven't seen any instructions on how to execute a code block. Well, that information is given by the *bytecode*. 

###Bytecode
Bytecode is an attribute of the code object. Here is what an bytecode looks like:
```python
>>> foo.func_code.co_code
'd\x01\x00}\x01\x00d\x00\x00S'
```
What's going on here? :confused:

So what is *bytecode*? Well, it's just a series of bytes(duh!). Most of them are not so printable. So let's take ```ord``` of each byte to see the integer of each byte
```python
>>> [ord(b) for b in foo.func_code.co_code
[100, 1, 0, 125, 1, 0, 100, 0, 0, 83]
```
The interpreter loops through each of these bytes, look up what it should do and do that thing. Bytecode doesn't include any python objects,references to objects or anything like that. One way to understand what these numbers mean to interpreter is to look through the CPython interpreter file (```ceval.c```). 
####Disassembling bytecode
We will be using ```dis``` module to look at the disassembling bytecode. Disassembling means taking a series of byte codes and print out something human readable. We'll use ```dis.dis()``` function to analyze the code objects of our function ```foo()```. These are nothing but a series of stack operations for the interpreter to do.

```python
>>> def foo(a):
...  x=3
...  return 3
...
>>> import dis
>>> dis.dis(foo.func_code)
  2           0 LOAD_CONST               1 (3)
              3 STORE_FAST               1 (x)

  3           6 LOAD_CONST               1 (3)
              9 RETURN_VALUE
```
>You can see ```dis.dis(foo)``` also doing the same thing. It's just convenience. 
The  numbers in the left-hand side are the line numbers in the original code. The second column is the offset into the bytecode. The middle column shows the name of the bytes, which are clearly for human interpretation. The interpreter doesn't benefit from these names.

The last two columns give information about the instructions's argument,only if there is an argument. Fourth column shows the argument
index and the last column is the argument itself. If you look at our function ```foo(a)```, we are passing arg ```a``` but we have never used ```a```, we have used a second argument ```x```. That is what the fourth column shows, the argument index 0 is for ```a``` and 1 is for ```x```.
