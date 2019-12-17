---
layout: post
title: Q&A for Python interview
date: 2019-11-17 00:00:00 +0000
description: Important questions for Python interview.
img: python.png # Add image post (optional)
tags: [Python]
---
Important topics in Q&A format is based on my experience. Feel free to update me in case of any observation or you want to add anything.

##### 1. How to debug pip installation error?
For debugging purpose, pip displays some installation message on console. It also offers ways to control console level log by -v,--verbose, -q and --quiet. Full log can be saved by providing --log option with file path, it will have complete installation log. There are cases where currupt download also creates issues at the time of installation, in that case try --no-cache-dir. If that also does not work then you can always try the installation from source file.

##### 2. Difference between list and dictionary?
###### List
* List in Python is a heterogeneous container for items.
* Elements present in List maintain their order.
* The elements present in list can be of any type (int, float, string, tuple etc.).
* Elements are accessed through their index values.
* If you have a collection of data that does not need random access, use List.
* Where you have to deal with values which can be changed, use List.
```python
mylist=[1,2,3,'4','sample']
```
###### Dictionary
* Dictionary is an unordered collection of key-value pairs.
* Dictionaries are used to handle large amount of data.
* Every element is having a key-value pair.
* Elements are accessed by using it’s key value.
* When you are dealing with unique keys and you are mapping values to the keys, use Dictionary.
```python
mydict = {1:'Python'}
```

##### 3. How to read 10 characters from a file?
```python
f = open('<file name>','r')
print(f.read(10))
```

##### 4. What are membership operators in Python? Write an example to explain both.
There are 2 types of membership operators in Python:  
in: If the value is found in a sequence, then the result becomes true else false  
not in: If the value is not found in a sequence, then the result becomes true else false  
```python
a=15
b=30
list = [3,6,15,20,25]

if (a in list):
	print('a is available in given list')
else:
	print('a is not available in given list')

 
if ( b not in list ):
	print('b is not available in given list')
else:
	print('b is available in given list')
```

##### 5. Command to get all keys from the dictionary.
```python
mydict = {1:'Raj',2:'Som'}
print(mydict.keys())
```

##### 6. What is monkey patching?
Monkey patching means adding a new variable or method to a class or module after it's been defined.  
Example: We define a class A as
```python
class A(object):
    def __init__(self, num):
        self.num = num

    def __add__(self, other):
        return A(self.num + other.num)
```
But now we want to add another function later in the code like below.
```python
def get_num(self):
    return self.num	
```
To do this as method of class A at runtime, we assign the function to class like below.  
```python
A.get_num = get_num
```
At runtime, assign the new method and use new methos like below.
```python
foo = A(42)
A.get_num = get_num
bar = A(6);
foo.get_num() # 42
bar.get_num() # 6
```

##### 7. What are *args and \**kwargs?
The special syntax, *args and \**kwargs in function definitions is used to pass a variable number of arguments to a function. The single asterisk form (*args) is used to pass a non-keyworded, variable-length argument list, and the double asterisk form is used to pass a keyworded, variable-length argument list.  
*args example :  
```python
def test_var_args(farg, *args):
    print('formal arg:{}'.format(farg))
    for arg in args:
        print('another arg:{}'.format(arg)

test_var_args(1, "two", 3)
```
Output
```python
formal arg: 1
another arg: two
another arg: 3
```
\**kwargs example
```python
def test_var_kwargs(farg, **kwargs):
    print('formal arg:{}'.format(farg))
    for key in kwargs:
        print('another keyword arg: {}: {}'.format(key, kwargs[key]))

test_var_kwargs(farg=1, myarg2="two", myarg3=3)
```
```python
formal arg: 1
another keyword arg: myarg2: two
another keyword arg: myarg3: 3
```

##### 8. What is Iterables in python?
When you create a list, you can read its items one by one. Reading its items one by one is called iteration:  
```python
mylist = [1, 2, 3]
for i in mylist:
	print(i)
```
Output
```python
1
2
3
```
mylist is an iterable. When you use a list comprehension, you create a list, and so an iterable:  
```python
mylist = [x*x for x in range(3)]
for i in mylist:
	print(i)
```
Output
```python
0
1
4
```
Everything you can use "for... in..." on is an iterable; lists, strings, files...  
These iterables are handy because you can read them as much as you wish, but you store all the values in memory and this is not always what you want when you have a lot of values.  

##### 9. What is Generators in python?
Generators are iterators, a kind of iterable **you can only iterate over once**. Generators do not store all the values in memory, **they generate the values on the fly**:  
```python
mygenerator = (x*x for x in range(3))
for i in mygenerator:
	print(i)
```
Output
```python
0
1
4
```
It is just the same except you used () instead of []. BUT, you cannot perform for i in mygenerator a second time since generators can only be used once: they calculate 0, then forget about it and calculate 1, and end calculating 4, one by one.  

##### 10. What does the "yield" keyword do?
