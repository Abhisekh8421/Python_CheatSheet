
# Object-Oriented Programming (OOP) Using Python

## Technical Paper



---

# 1. Introduction

Object-Oriented Programming (OOP) is a programming style based on the concept of **objects**.

An object contains:

* Data (variables)
* Behavior (functions)

In Python, everything is treated as an object.

OOP helps in:

* Code reusability
* Better organization
* Scalability
* Security of data
* Real-world modeling

---

# 2. Class and Object

## 2.1 What is a Class?

A class is a blueprint for creating objects.

## 2.2 What is an Object?

An object is an instance of a class.

### Example

```python
class Factory:
    a = 10  # class attribute

    def __init__(self, name="hi", place=""):
        self.name = name
        self.place = place

    def show_place(self):
        print(f"The factory is in {self.place}")


f1 = Factory(place="Visakhapatnam")
f1.name = "Abhi"
print(f1.__dict__)
```

### Explanation

* `__init__` is a constructor.
* `self` refers to the current object.
* Each object has its own attributes.
* Class attributes are shared among all objects.

---

# 3. Class Attributes vs Instance Attributes

## Instance Attributes

* Belong to individual objects.
* Defined inside `__init__`.

## Class Attributes

* Shared among all objects.
* Defined outside `__init__`.

### Example

```python
class Factory:
    Factory_name = "Bags"

    def __init__(self, material, zips, pockets):
        self.material = material
        self.zips = zips
        self.pockets = pockets

    @classmethod
    def change_Factory_name(cls, new_name):
        cls.Factory_name = new_name

    def show(self):
        print(f"{self.material}, {self.pockets}, {self.zips}")
```

---

# 4. Class Methods

A class method works with the class instead of the object.

```python
class Person:
    def __init__(self, age, name):
        self.age = age
        self.name = name

    @classmethod
    def from_birth_year(cls, year, name):
        return cls(2025 - year, name)


p = Person.from_birth_year(2000, "Abhi")
print(p.__dict__)
```

---

# 5. The Four Pillars of OOP

1. Inheritance
2. Polymorphism
3. Encapsulation
4. Abstraction

---

# 6. Inheritance

Inheritance allows a child class to use properties and methods of a parent class.

### Benefits

* Code reuse
* Logical hierarchy
* Extensibility

### Example

```python
class Parent:
    def __init__(self, name, age):
        self.name = name
        self.age = age

class Child(Parent):
    def show(self):
        print(self.__dict__)

obj = Child("Abhi", 22)
obj.show()
```

---

## 6.1 Using super()

If child defines its own constructor, it must call parent constructor manually.

```python
class Child(Parent):
    def __init__(self, name, age, height):
        super().__init__(name, age)
        self.height = height
```

---

## 6.2 Method Resolution Order (MRO)

MRO decides the order in which Python searches classes.

Important in multiple inheritance.

Python follows **left-to-right order**.

---

# 7. Polymorphism

Polymorphism means "many forms".

Same method name behaves differently.

### Example

```python
class Shape:
    def area(self):
        print("No dimensions")

class Rectangle(Shape):
    def __init__(self, length, breadth):
        self.length = length
        self.breadth = breadth

    def area(self):
        return self.length * self.breadth
```

---

## 7.1 Method Overriding

When child class changes parent method behavior.

---

## 7.2 Duck Typing

"If it looks like a duck and acts like a duck, it is a duck."

```python
class Animal:
    def show(self):
        print("Animal showing")

class Human:
    def show(self):
        print("Human showing")

def make_show(obj):
    obj.show()

make_show(Animal())
make_show(Human())
```

---

# 8. Encapsulation

Encapsulation means:

* Bundling data and methods together
* Restricting direct access

## Private Variables

```python
class Factory:
    __a = 10

    def show(self):
        print(self.__a)
```

Python uses **name mangling** for private variables.

Access internally as:

```
obj._ClassName__variable
```

---

## 8.1 Getters and Setters

Used to validate data.

### Without Validation (Problem)

```python
p.age = -10  # invalid
```

### With Getter & Setter

```python
class Person:
    def __init__(self, age):
        self.__age = age

    @property
    def age(self):
        return self.__age

    @age.setter
    def age(self, value):
        if value < 0:
            raise ValueError("Age cannot be negative")
        self.__age = value
```

---

# 9. Abstraction

Abstraction hides implementation details and enforces structure.

Uses `ABC` module.

```python
from abc import ABC, abstractmethod

class Shape(ABC):

    @abstractmethod
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, length, breadth):
        self.length = length
        self.breadth = breadth

    def area(self):
        return self.length * self.breadth
```

### Why Use Abstraction?

* Large systems
* Framework design
* Enforcing contracts
* Following SOLID principles

Without abstraction → Errors happen at runtime
With abstraction → Errors happen early

---

# 10. Dunder (Magic) Methods

Special methods with double underscores.

Examples:

* `__init__`
* `__str__`
* `__add__`

```python
class Animal:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self):
        return f"Name: {self.name}"

    def __add__(self, other):
        return self.age + other.age
```

---

# 11. Decorators

A decorator adds extra functionality to a function without modifying it.

```python
def decorate(func):
    def wrapper(a, b):
        print("Start")
        func(a, b)
        print("End")
    return wrapper

@decorate
def addition(a, b):
    print(a + b)
```

---


# 12. Conclusion

Object-Oriented Programming in Python provides:

* Better structure
* Reusable code
* Secure data handling
* Scalable systems

By using:

* Inheritance
* Polymorphism
* Encapsulation
* Abstraction

We can build clean and professional applications.

Python makes OOP simple and powerful.


