## Python: range() vs xrange()
'range() and xrange()' are the two functions often used for itertations in python.  In python3, 'xrange()' has been deprecated. 'range()' behaves like 'xrange()'. 

''' python
>>> [x for x in range(10)]
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> [x for x in xrange(10)]
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>>
'''

What they do might be similar, but how they do it is totally different.
Both are implemented in different ways and have different properties associated with them. 

### Return type and memory 

''' python
>>> type(range(10))
<type 'list'>
>>> type(xrange(10))
<type 'xrange'>
>>>
'''
The return type of 'range()' is a list, whereas 'xrange()' returns an object of type 'xrange' which is an object. This is an sequence type which yields the same values without actually storing them. This concept is called the **lazyloading**. This 'xrange' takes 1-3 arguments, **start,stop,step**. Unlike range, xrange generates the result list or values only when needed. 

The advantage of 'xrange()' over 'range()' is minimal when the size of the range is small. If the range is very huge, then 'xrange()' takes up very little memory compared to 'range()' which has to generate a list of the same size.

''' python
>>> import sys
# range 10
>>> sys.getsizeof(range(10))
76
>>> sys.getsizeof(xrange(10))
20
# range 1,00,000
>>> sys.getsizeof(range(100000))
400036
>>> sys.getsizeof(xrange(100000))
20
>>>
'''

Whoa! :astonished: 


