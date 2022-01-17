---
layout: post
title: "Learning Python 3 - More on Classes"
date: 2022-01-15 13:00:00 +0000
published: true
---

Continued from the [previous post on classes](/2022/01/07/learning-python-2-classes.html) here is addition learning I did around multiple inhertiance. This works in a cleaner way that PHP where a child can only inherit directly from one base class (using `extend`) but can implement as many interfaces to other classes as you want (using `implement`). However, a potential gotcha of the Python inhertiance chain is the order in which subclasses call their parents, the method resolution order method helps with this as shown below.

## Multiple Inheritance

Python supports multiple inheritance with the following syntax:

```python

class A(object):
    def __init__(self, prop1, prop2):
        self.prop1 = prop1
        self.prop2 = prop2

    def some_function():
        # using pass here to leave these examples as stubs that don't cause errors
        pass

class B(object):
    def __init(self, prop3, prop4):
        self.prop3 = prop3
        self.prop4 = prop4

    def some_other_function():
        pass

# class C inherients from both A and B
class C(A, B):
    pass
```

Python has a built in method called method resultion order called via `class_var.__mro__` or `class_var.mro()` which can be used to visual the inheritance chain of a given object:

```python

print(C.mro())

# prints: [<class '__main__.C'>, <class '__main__.A'>, <class '__main__.B'>]

```

## More Complicated Examples:

For more complicated examples see: [Programiz - Multiple Inheritance in Python](https://www.programiz.com/python-programming/multiple-inheritance) and [Programiz - Super Method in Python](https://www.programiz.com/python-programming/methods/built-in/super). I found these really useful.