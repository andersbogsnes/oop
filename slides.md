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

# What is an Object?

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

# Other types of programming

- Imperative
- Functional

---

# Representing the world in code

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

# Defining a class

```python
class Salesperson:
    pass

james = Salesperson()
```

----

## Terminology

- `james` is an **instance** of `Salesperson`
- we have **instantiated** a new **instance** of `Salesperson`

---

# Initialize a class with data

----

We can *initialize* the class with some data

```python
class Salesperson:
    def __init__(self, name, age, sales_budget):
        self.age = age
        self.name = name
        self.sales_budget = sales_budget

>>> james = Salesperson(name="James", age=32, sales_budget=1000)
>>> james.age
32
```

---

## The mystical `self`

A class is a **blueprint** of something. A blueprint can create many **instances** with it's own unique data.

----

When we need to refer to an **instance** of a blueprint, `self` is the placeholder we use

Python passes it as the first argument to any **method**
defined on the class
