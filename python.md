---
title: Python
kind: cheatsheet
keywords: [code, cheatsheet]
created_at: 2015-apr-14 23:22:00
---

## Reflection

```python
type(a) # find out type of a
type(a) is b # is a a b?
dir(a) # list supported methods of a
hasattr(a, "methodName") # does it have methodName
```

## Modules

```python
import math
from math import ceil, floor
```

## Functions

```python
def add(a, b):
    return a+b

a=5

def func():
    global a # without this a local version would be used
    return a*a

(lambda x: x>2)(3) # true
```

## Classes

```python
class Car(object):
    kind = "vehicle" # class attribute

    # initializer
    def __init__(self):
        print("I'm new!")
        self.speed = 0

    def drive(self, speed):
        print "driving at %f mph" % speed
        self.speed = speed

    @classmethod
    def clm(cls):
        print "class something"

    @staticmethod
    def staticsomething():
        print "something else"
```
