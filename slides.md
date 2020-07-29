---
title: OOP in Python
theme: moon
revealOptions:
    transitionSpeed: default
---

<!-- .slide: data-background="./images/code.jpg" -->
# OOP in Python

----


OOP is a style of programming that models Objects in code

---

## What is an Object?

An object typically has *attributes* and *behaviour*

----

Attributes is something we have

- Age
- Address
- Height

----

Behaviour is something we do

- Walk
- Talk
- Run

---

## Other types of programming

- Imperative
- Functional

---

## Representing the world in code

How do we represent the world in Python code?

----

If we want to represent a salesperson, we could represent them as a list of data

```python
james = ["James", 32, 1000]
```
----
We can extract data about our salesperson James

```python
name = james[0]
age = james[1]
sales_budget = james[3]
```

----

How does that make you feel?

---

## Defining a class

```python
class SalesPerson:
    pass

james = SalesPerson()
```

----

### Terminology

- `james` is an **instance** of `SalesPerson`
- we have **instantiated** a new **instance** of `SalesPerson`

---

## Add attributes

----

We can *initialize* the class with some data

```python
class SalesPerson:
    def __init__(self, name, age, sales_budget):
        self.age = age
        self.name = name
        self.sales_budget = sales_budget

>>> james = SalesPerson(name="James", age=32, sales_budget=1000)
>>> james.age
32
```

----

Now we can make as many salespeople as we want

```python
>>> mike = SalesPerson(name="Mike", age=40, sales_budge=2000)
>>> mike.age
40
```

---

## The mystical `self`

- A class is a **blueprint** of something. 
- A blueprint can create many **instances** with it's own unique data.

----

- When we need to refer to an **instance** of a blueprint `self` is the placeholder we use
- Python passes it as the first argument to any **method** defined on the class

---

## Class attributes

- Classes have **instance** attributes, which we define in the `__init__`
- Classes also have **class** attributes, which are shared between all instances

----

### Class attribute

```python
class SalesPerson:
    company = "Alm Brand"

    def __init__(self, name, age, sales_budget)
        self.name = name
        self.age = age
        self.sales_budget = sales_budget

>>> james = SalesPerson("James", 32, 1000)
>>> mike = SalesPerson("Mike", 40, 2000)
>>> james.company
"Alm Brand"
>>> mike.company
"Alm Brand"
```

---

## Add behaviour

We can add **behaviour** to our class - these usually act on **attributes**

```python
class SalesPerson:
    company = "Alm Brand"

    def __init__(self, name, age, sales_budget):
        self.name = name
        self.age = age
        self.sales_budget

    def greet(self):
        print(f"Hi, I'm {self.name} from {self.company}")

>>> james = SalesPerson("James", 32, 1000)
>>> james.greet()
"Hi, I'm James from Alm Brand"
```
----

### We can change attributes

> We're all consenting adults
>
> -- <cite>Guido van rossum</cite>

```python
>>> james.name = "Jamie"
>>> james.greet()
"Hi, I'm Jamie from Alm Brand"
```

---

## dunder methods

- Short for *double underscore* - also called *magic methods*
- Used to change how an object interacts with python
- Examples include:  
  - `__init__`
  - `__repr__`
  - `__add__`

----

### \_\_repr\_\_

If we print `james`, it's not very informative

```
>>> print(james)
<__main__.SalesPerson object at 0x7f479d47db50>
```

----

We need to tell Python what to do when **representing** a Sales person

```python
class SalesPerson:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        print(f"Hi, I'm {self.name}")

    def __repr__(self):
        return f"SalesPerson {self.name}: {self.age} years old"

>>> james = SalesPerson("James", 32, 1000)
>>> print(james)
"SalesPerson James: 32 years old"
```

---

# Exercise

Create an Organization class.

#### It should
 - have a `num_employees` attribute showing how many employees there are
 - have a `name` attribute
 - have an informative `__repr__`

----

# Solution

```python

class Organization:
    def __init__(self, name, num_employees):
        self.name = name
        self.num_employees = num_employees

    def __repr__(self):
        return f"{self.name}: {self.num_employees} employees"
```

---

# Composition and Inheritance

OOP has two powerful concepts that allow objects to interact with each other:

----

## Composition

**Compose** objects together - Objects can contain other objects and call their methods and attributes

----

### Inheritance

**Inherit** from other objects - Objects can inherit from other objects and call its parents methods and attributes

---

## Inheritance

Used to **specialize** an existing class - we usually call this *subclassing*

----

These are **specialized** versions of a SalesPerson and can have specific **behaviour**


```python
class Phoner(SalesPerson):
    def call(self, telephone_number):
        ...

class TiedAgent(SalesPerson):
    def meet(self, address):
        ...
```

----

Inherited classes still have access to its parents methods

```python
>>> mike = Phoner("Mike", 40, 2000)
>>> mike.greet()
"Hi, I'm Mike"
```

----

We can also overwrite methods from the parent

```python
class Phoner(SalesPerson):
    def greet(self):
        print(f"Hi, I'm {self.name} and I'm a phoner")
```

----

Or extend methods

```python

class Phoner(SalesPerson):
    def __init__(self, name, age, sales_budget, phone_number):
        super().__init__(name, age, sales_budget)
        self.phone_number = phone_number

>>> jane = Phoner(name="Jane", age=20, sales_budget=0, phone_number=35477777)
>>> jane.phone_number
35477777
```
