---
layout: post
title: "Learning Python 2 - Classes"
date: 2022-01-07 16:00:00 +0000
published: true
---

Continued from the [previous post on functions](/2022/01/07/learning-python-1-functions.html) I also dabbled with class definitions and inhertiance. Note that I'm trying to follow the [PEP-8 Sytle Guide](https://www.python.org/dev/peps/pep-0008/) to ingrain some best practises asap.

## Basic Class Syntax

```python
# Basic class structure - defined with lower case class keyword, uppercase class name,
# takes arg of object to inherit from built-in object template.

class Student(object):
    '''Student class'''
    # Can set class properties that will be shared / the same across all instances.
    status = 'enrolled'
    
    def __init__(self,name,age):
        '''Construct takes args of self and whatever properties are set on instantiation.'''
        self.name = name
        self.age = age
        self.notes = []

    def get_info(self):
        '''Example getter.'''
        print(f"name: {self.name}, age: {self.age} yrs")
        
    def add_notes(self,note):
        '''Example setter.'''
        self.notes.append(note)
        
# Inhertiance example, younger students inherit from Student but have their own methods / properties.
class LittleDragon(Student):
    type = 'litle dragon'
    
    def __init__(self, name, age, guardian_name):
        # super() calls the constructer of the parent class.
        self.guardian_name = guardian_name
        super().__init__(name, age) 
        
    def get_info(self):
        '''Example getter, overrides the method with the same name on the parent.'''
        print(f"name: {self.name}, age: {self.age} yrs, guardian name: {self.guardian_name}")
```

To play around with these instantiating these objects in the VS Code terminal I Googled around and found this was the most straight forward way:

```python
# open python3:
% python3
# execute the script to make the classes available:
>>> exec(open('class_examples.py').read())
# instantiate and assign the Student class:
>>> student = Student('Bob',27)
# can now read properties and methods from the object with the dot notation syntax:
>>> student.age
# prints 27
# instantiate and assign a Little Dragon:
>>> little_dragon = LittleDragon('Ellie',5,'Rebecca')
# as above, can read properties and methods from the object:
>>> little_dragon.get_info()
# prints name: Ellie, age: 5 yrs, guardian name: Rebecca
```