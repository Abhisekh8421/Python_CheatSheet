
# Python Complete  Cheatsheet 

---

# Variable Naming Conventions

```python
AbhiSekh = "sample text-1"      # Pascal Case
abhi_sekh = "sample text-2"     # Snake Case
abhiSekhSuru = "sample text-3"  # Camel Case
```

---

# Type & Memory Location

```python
ExampleVariable = 10
print(type(ExampleVariable))
print(id(ExampleVariable))

ExampleVariable = ExampleVariable + 5
print(id(ExampleVariable))
```

### Output (id will change):

```
<class 'int'>
140123456789456
140123456789600
```

`id()` shows memory location.
New memory is created after reassignment.

---

# String Immutability

```python
name = "AbhiSekh"
print(id(name))

name += "c"
print(id(name))
```

### Output:

```
140123456700000
140123456700128
```

Strings are immutable → new memory created.

---

# f-String Formatting

```python
name = "AbhiSekh"
age = 22
print(f"My name is {name} and I am {age} years old.")
```

### Output:

```
My name is AbhiSekh and I am 22 years old.
```

f-string is used for formatted output.

---

# String Methods

```python
name = "    ExampleName hello hi     "

print(name.lower())
print(name.strip())
print(name.count("h"))
print(name.find("hi"))
print(name.split(" "))
```

### Output:

```
    examplename hello hi     
ExampleName hello hi
2
21
['', '', '', '', 'ExampleName', 'hello', 'hi', '', '', '', '', '']
```

String methods modify or inspect string content.

---

# String Slicing

```python
example_1 = "PYTHON"

print(example_1[0:4])
print(example_1[::-1])
print(example_1[::2])
```

### Output:

```
PYTH
NOHTYP
PTO
```

Slicing extracts part of string.
`[::-1]` reverses string.

---

# Extract Username

```python
email = "abhisekhsuru@gmail.com"
username = email[0:email.index("@")]
print(username)
```

### Output:

```
abhisekhsuru
```

Extract substring before "@".

---

# Type Conversion

```python
exampleForExplicit = "5"
exampleForExplicit = int(exampleForExplicit)
print(exampleForExplicit + 5)
```

###  Output:

```
10
```

Converts string to integer.

---

# Arithmetic Operators

```python
op1 = 18
op2 = 3

print(op1 + op2)
print(op1 - op2)
print(op1 * op2)
print(op1 / op2)
print(op1 // op2)
print(op1 % op2)
print(op1 ** op2)
```

### Output:

```
21
15
54
6.0
6
0
5832
```

---

# Logical Operators

```python
x = True
y = False

print(x and y)
print(x or y)
print(not x)
```

### Output:

```
False
True
False
```

Logical operators combine conditions.

---

# Truthy & Falsy

```python
print(bool(0))
print(bool(""))
print(bool([]))
print(bool([1,2,3]))
```

### Output:

```
False
False
False
True
```

Empty values → False
Non-empty → True

---

# Conditional Statement

```python
num = 10

if num > 0:
    print("Positive")
else:
    print("Negative")
```

### Output:

```
Positive
```

Executes block based on condition.

---

# For Loop

```python
for i in range(3):
    print(i)
```

### Output:

```
0
1
2
```

Runs fixed number of times.

---

# While Loop

```python
count = 0
while count < 3:
    print(count)
    count += 1
```

### Output:

```
0
1
2
```

Runs until condition becomes False.

---

# Palindrome Check

```python
Name1 = "madam"
Name2 = ""

for i in range(len(Name1)-1, -1, -1):
    Name2 += Name1[i]

print(Name1 == Name2)
```

### Output:

```
True
```

Checks if string equals its reverse.

---

# Reverse Number

```python
number = 1234
reverseNum = 0

while number > 0:
    digit = number % 10
    reverseNum = (reverseNum * 10) + digit
    number = number // 10

print(reverseNum)
```

### Output:

```
4321
```

Extracts digits and builds reversed number.

---

# Functions

## *args Example

```python
def add(*numbers):
    return sum(numbers)

print(add(1, 2, 3, 4))
```

### Output:

```
10
```

Accepts variable number of arguments.

---

## **kwargs Example

```python
def info(**info):
    for key, value in info.items():
        print(f"{key} : {value}")

info(name="abhi", age=20)
```

### Output:

```
name : abhi
age : 20
```

Accepts variable keyword arguments.

---

# Lists

```python
my_list = [2, 3, "hello"]
my_list.append("new")
print(my_list)
```

### Output:

```
[2, 3, 'hello', 'new']
```

Lists are ordered, mutable, allow duplicates.

---

# Nested List

```python
nested_list = [[1,2,3],[4,5,6]]

for sublist in nested_list:
    for item in sublist:
        print(item, end=" ")
```

### Output:

```
1 2 3 4 5 6
```

Iterates through nested list.


---

# Lists – Complete Example (With Outputs)

---

## Create a List

```python
my_list = [2, 3, "hello", 4.5, True]
print(my_list)
```

### Output:

```
[2, 3, 'hello', 4.5, True]
```

Lists are ordered, mutable, allow duplicates, and can store different data types.

---

# Insertion Operations

```python
my_list.append("new item")
print(my_list)
```

### Output:

```
[2, 3, 'hello', 4.5, True, 'new item']
```

`append()` adds item at the end.

---

```python
my_list.insert(2, "inserted item")
print(my_list)
```

### Output:

```
[2, 3, 'inserted item', 'hello', 4.5, True, 'new item']
```

`insert(index, value)` inserts at specific position.

---

```python
my_list.extend([7, 8, 9])
print(my_list)
```

### Output:

```
[2, 3, 'inserted item', 'hello', 4.5, True, 'new item', 7, 8, 9]
```

`extend()` adds multiple elements.

---

# Deletion Operations

```python
my_list.pop()
print(my_list)
```

### Output:

```
[2, 3, 'inserted item', 'hello', 4.5, True, 'new item', 7, 8]
```

`pop()` removes last item.

---

```python
my_list.pop(1)
print(my_list)
```

### Output:

```
[2, 'inserted item', 'hello', 4.5, True, 'new item', 7, 8]
```

`pop(index)` removes element at index.

---

```python
my_list.remove("hello")
print(my_list)
```

### Output:

```
[2, 'inserted item', 4.5, True, 'new item', 7, 8]
```

`remove(value)` removes first occurrence.

---

```python
print(my_list[my_list.index("inserted item")])
```

### Output:

```
inserted item
```

`index(value)` returns position of element.

---

```python
my_list.clear()
print(my_list)
```

### Output:

```
[]
```

`clear()` removes all elements.

---

# Sorting & Reversing

```python
my_list = [5, 2, 9, 1, 5, 6]

my_list.sort()
print(my_list)
```

### Output:

```
[1, 2, 5, 5, 6, 9]
```

`sort()` sorts in ascending order.

---

```python
my_list.reverse()
print(my_list)
```

### Output:

```
[9, 6, 5, 5, 2, 1]
```

`reverse()` reverses list order.

---

# Built-in List Functions

```python
my_list = [5, 2, 9, 1, 5, 6]

print(min(my_list))
print(max(my_list))
print(sum(my_list))
print(len(my_list))
print(my_list.count(5))
print(my_list.index(9))
print(my_list.copy())
```

### Output:

```
1
9
28
6
2
2
[5, 2, 9, 1, 5, 6]
```


* `min()` → smallest value
* `max()` → largest value
* `sum()` → total sum
* `len()` → length
* `count()` → occurrences
* `index()` → first position
* `copy()` → shallow copy

---

# Remove Boolean Example

```python
my_list = [2, 3, True, 5]
my_list.remove(True)
print(my_list)
```

### Output:

```
[2, 3, 5]
```

Removes first occurrence of value.

---

# List Slicing

```python
my_list = [5, 2, 9, 1, 5, 6]

print(my_list[::-1])
print(my_list[::2])
print(my_list[1:4])
print(my_list[-1])
print(my_list[-3:-1])
print(my_list[::])
```

### Output:

```
[6, 5, 1, 9, 2, 5]
[5, 9, 5]
[2, 9, 1]
6
[1, 5]
[5, 2, 9, 1, 5, 6]
```


* `[::-1]` → reverse
* `[::2]` → step slicing
* `[1:4]` → range slice
* `[-1]` → last element
* `[-3:-1]` → negative slicing
* `[::]` → entire list copy





---

# Dictionaries

```python
my_dict = {"name": "Abhi", "age": 22}
print(my_dict["name"])

my_dict["age"] = 23
print(my_dict)
```

### Output:

```
Abhi
{'name': 'Abhi', 'age': 23}
```

Dictionary stores key:value pairs.
Keys must be immutable.

---

# Nested Dictionary

```python
nested_dict = {
    "student1": {"name": "Alice", "age": 20}
}

print(nested_dict["student1"]["name"])
```

### Output:

```
Alice
```

 Access nested dictionary using multiple keys.



---

# Dictionary – Complete Example (With Outputs)

## Create a Dictionary

```python
my_dict = {
    "name": "AbhiSekh",
    "age": 22,
    "is_student": True,
    "courses": ["Math", "Science", "History"],
}
```

Dictionary stores data in **key:value pairs**.
Keys must be immutable.
Values can be any data type.

---

## Traversing the Dictionary

```python
for key, val in my_dict.items():
    print(f"{key} : {val}")
```

### Output:

```
name : AbhiSekh
age : 22
is_student : True
courses : ['Math', 'Science', 'History']
```

`.items()` returns key-value pairs.

---

## Accessing Values

```python
print(my_dict["name"])
print(my_dict.get("age"))
```

### Output:

```
AbhiSekh
22
```

`dict[key]` → Direct access (gives error if key not found).
`dict.get(key)` → Safe access (returns None if not found).

---

## Adding / Updating Key-Value Pairs

```python
my_dict.update(
    {"age": 23, "is_student": False, "hi": "hello"}
)

print(my_dict)
```

### Output:

```
{'name': 'AbhiSekh', 'age': 23, 'is_student': False, 'courses': ['Math', 'Science', 'History'], 'hi': 'hello'}
```

`update()` updates existing keys or adds new ones.

---

```python
my_dict["email"] = "abhishek@example.com"
my_dict["age"] = 23

print(my_dict)
```

### Output:

```
{'name': 'AbhiSekh', 'age': 23, 'is_student': False, 'courses': ['Math', 'Science', 'History'], 'hi': 'hello', 'email': 'abhishek@example.com'}
```

Assigning with `dict[key] = value` adds or updates.

---

## Deleting Key-Value Pairs

```python
my_dict.pop("is_student")
my_dict.popitem()
del my_dict["courses"]

print(my_dict)
```

### Output:

```
{'name': 'AbhiSekh', 'age': 23, 'hi': 'hello'}
```

`pop(key)` removes specific key.
`popitem()` removes last inserted key.
`del dict[key]` deletes specific key.

---

```python
my_dict.clear()
print(my_dict)
```

### Output:

```
{}
```

`clear()` removes all items from dictionary.

---

## Dictionary Methods

```python
my_dict = {"name": "Abhi", "age": 22}

print(my_dict.keys())
print(my_dict.values())
print(my_dict.items())
```

### Output:

```
dict_keys(['name', 'age'])
dict_values(['Abhi', 22])
dict_items([('name', 'Abhi'), ('age', 22)])
```

`.keys()` → Returns all keys
`.values()` → Returns all values
`.items()` → Returns key-value pairs

---

## Loop Through Dictionary Again

```python
for key, value in my_dict.items():
    print(f"{key}: {value}")
```

### Output:

```
name: Abhi
age: 22
```

This program iterates through each key:value pair in a dictionary and prints them.




