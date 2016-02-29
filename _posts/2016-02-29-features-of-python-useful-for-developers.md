---
layout:     post
title:      Featurs of Python Useful for Developers
date:       2016-02-29 12:00:00
summary:    A compilation of useful practices for the Python programming language.
categories: python idiomatic practices
---

Below is a collection of modules/idiomatic practices that I think are useful for Python developers (this will be periodically updated):

# `collections`

The `collections` module (featured in the standard library), is a series of high performance container data types that can be used for a variety of different purposes.

## `namedtuple`

`collections.namedtuple` is as a factory function for creating tuple subclasses with named fields.

The following example demonstrates the effectiveness of using a `namedtuple`:

**Without `namedtuple`**

    >>> color = (255, 255, 255)
    >>> print color[0]
    255

**With `namedtuple`**

    >>> import collections
    >>> Color = collections.namedtuple('Color', ['red', 'green', 'blue'])
    >>> color = Color(255, 255, 255)
    >>> print color.red
    >>> 255

`namedtuple` requires two arguments during instantiation, the name of the `namedtuple` and the attributes that are associated with it. The second argument can either be a list of `str` objects *or* a `str` object delimited via spaces (e.g. `red green blue`).

Using named fields makes it easier for other developers to associate meaning to the values in a `tuple` object.

`namedtupled` objects also include the `_asdict()` method which returns an instance of an `OrderedDict` object (another data type of the `collections` module):

    >>> print color._asdict()
    OrderedDict([('red', 255), ('green', 255), ('blue', 255)])

`OrderedDict` is another data type of the `collections` module. More information on the `OrderedDict` data type can be found [here](https://docs.python.org/2/library/collections.html#collections.OrderedDict).

## Context managers

Context managers are a unique feature to Python. They involved the use of a `with` statement, which provide both `__enter__()` and `__exit__()` [https://pythonconquerstheuniverse.wordpress.com/2012/03/09/pythons-magic-methods/]("dunder") methods that are invoked upon entry and exit within the body of the `with` statement.

```python
with open('endpoints.json', 'rb') as fp:
    # do something with the opened file
```

Without context specifiers, the above code would involve the use of `try/finally` statements:

```python
try:
    fp = open('endpoints.json', 'rb')
     do something with the opened file
finally:
    fp.close()
```

You can implement your own functionality for `with` statements within custom classes by overriding the `__enter__` and `__exit__` methods. See the [https://en.wikipedia.org/wiki/Operator_overloading](wiki) page for more information on operator overloading.

## List comprehensions

Another unique feature of Python is list comprehensions (listcomps). There are a few advantages to using list comprehensions in Python:

  - They often have better runtime performance that a traditional `for` loop
  - They're often easy to read
  - They reduce the amount of code that needs to be written

Observe the following two examples, one uses a traditional `for` loop, the other uses a list comprehension:

**Traditional `for` loop**

```python
squared = []
for i in range(10):
    squared.append(i ** 2)
print squared
```

**List comprehension**

    >>> print [i ** 2 for i in range(10)]

Both examples return a new list object with each number `0..9` being squared.

Here's a more complex example:

```python
sizes = ['small', 'medium', 'large']
colors = ['red', 'green', 'blue']
combinations = []
for size in sizes:
    for color in colors:
        combinations.append((size, color))
print combinations
```

```python
sizes = ['small', 'medium', 'large']
colors = ['red', 'green', 'blue']
print [(size, color) for size in sizes for color in colors]
```

Both examples produce the following output:

```python
[('small', 'red'), ('small', 'green'), ('small', 'blue'), ('medium', 'red'), ('medium', 'green'), ('medium', 'blue'), ('large', 'red'), ('large', 'green'), ('large', 'blue')]
```

List comprehensions also support filtering by specifying what's known as a predicate. For example, if you wanted to return a new list of *only* numbers divisible by 2, then you would do the following:

```python
evens = []
for i in range(100):
    if i % 2 == 0:
        evens.append(i)
print evens
```

```python
print [i for i in range(100) if i % 2 == 0]
```

The `if` statement on the right side of the `range` statement is the predicate of the list comprehension.
