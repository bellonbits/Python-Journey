# Python Programming - Lecture 4 Notes

## Dictionary in Python

**Dictionaries** are used to store data values in **key:value** pairs.

### Dictionary Properties
- **Unordered**: Items don't have a defined order
- **Mutable**: Can be changed after creation
- **No Duplicate Keys**: Each key must be unique
- **Syntax**: `"key": value`

### Basic Dictionary Operations
```python
# Creating a dictionary
student = {
    "name": "Karan",
    "cgpa": 9.6,
    "marks": [98, 97, 85]
}

# Accessing values
print(dict["name"])   # Access using key
print(dict["cgpa"])   
print(dict["marks"])  

# Adding or updating values
dict["key"] = "value"  # To assign or add new key-value pair
```

### Example Dictionary
```python
student = {
    "name": "Alice",
    "age": 20,
    "grade": "A",
    "subjects": ["Math", "Physics", "Chemistry"]
}
```

## Nested Dictionaries

Dictionaries can contain other dictionaries as values:

```python
student = {
    "name": "John",
    "score": {
        "math": 95,
        "physics": 88,
        "chemistry": 92
    }
}

# Accessing nested dictionary values
print(student["score"]["math"])  # Output: 95
```

## Dictionary Methods

### 1. `keys()` - Returns All Keys
```python
myDict = {"name": "Alice", "age": 20, "grade": "A"}
print(myDict.keys())  # Output: dict_keys(['name', 'age', 'grade'])
```

### 2. `values()` - Returns All Values
```python
print(myDict.values())  # Output: dict_values(['Alice', 20, 'A'])
```

### 3. `items()` - Returns All (Key, Value) Pairs as Tuples
```python
print(myDict.items())  
# Output: dict_items([('name', 'Alice'), ('age', 20), ('grade', 'A')])
```

### 4. `get()` - Returns Value for Given Key
```python
print(myDict.get("name"))  # Output: Alice
print(myDict.get("height"))  # Output: None (if key doesn't exist)
```

### 5. `update()` - Inserts Specified Items to Dictionary
```python
newDict = {"height": 5.6, "city": "Delhi"}
myDict.update(newDict)
print(myDict)  # Original dictionary updated with new key-value pairs
```

## Set in Python

**Set** is a collection of unordered items where each element must be **unique** and **immutable**.

### Set Properties
- **Unordered**: No defined sequence
- **Unique Elements**: No duplicates allowed
- **Immutable Elements**: Elements themselves cannot be changed
- **Mutable Collection**: Can add/remove elements from set

### Creating Sets
```python
# Empty set (special syntax required)
null_set = set()  # Empty set syntax

# Set with elements
nums = {1, 2, 3, 4}

# Duplicate elements are automatically removed
set2 = {1, 2, 2, 2}  # Resolves to {1, 2}
print(set2)  # Output: {1, 2}
```

## Set Methods

### Basic Set Operations

#### 1. `add()` - Adds an Element
```python
my_set = {1, 2, 3}
my_set.add(4)
print(my_set)  # Output: {1, 2, 3, 4}
```

#### 2. `remove()` - Removes an Element
```python
my_set = {1, 2, 3, 4}
my_set.remove(3)
print(my_set)  # Output: {1, 2, 4}
```

#### 3. `clear()` - Empties the Set
```python
my_set = {1, 2, 3}
my_set.clear()
print(my_set)  # Output: set()
```

#### 4. `pop()` - Removes a Random Value
```python
my_set = {1, 2, 3, 4}
removed_element = my_set.pop()
print(f"Removed: {removed_element}")
print(my_set)
```

### Set Operations

#### 1. `union()` - Combines Both Sets
```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
result = set1.union(set2)
print(result)  # Output: {1, 2, 3, 4, 5}
```

#### 2. `intersection()` - Returns Common Values
```python
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}
result = set1.intersection(set2)
print(result)  # Output: {3, 4}
```

## Practice Problems

### 1. Store Word Meanings in Dictionary
Store following word meanings in a Python dictionary:
- table: "a piece of furniture", "list of facts & figures"
- cat: "a small animal"

```python
word_meanings = {
    "table": ["a piece of furniture", "list of facts & figures"],
    "cat": "a small animal"
}

print(word_meanings["table"])  # Output: ['a piece of furniture', 'list of facts & figures']
print(word_meanings["cat"])    # Output: a small animal
```

### 2. Count Required Classrooms
You are given a list of subjects for students. Assume one classroom is required for 1 subject. How many classrooms are needed by all students?

**Subject list**: "python", "java", "C++", "python", "javascript", "java", "python", "java", "C++", "C"

```python
subjects = ["python", "java", "C++", "python", "javascript", 
           "java", "python", "java", "C++", "C"]

# Convert to set to get unique subjects
unique_subjects = set(subjects)
classrooms_needed = len(unique_subjects)

print("Unique subjects:", unique_subjects)
print("Number of classrooms needed:", classrooms_needed)
# Output: Number of classrooms needed: 5
```

### 3. Store Marks in Dictionary
Write a program to enter marks of 3 subjects from the user and store them in a dictionary. Start with an empty dictionary and add one by one. Use subject name as key and marks as value.

```python
# Start with empty dictionary
marks = {}

# Get marks for 3 subjects
for i in range(3):
    subject = input(f"Enter subject {i+1} name: ")
    mark = float(input(f"Enter marks for {subject}: "))
    marks[subject] = mark

print("Final marks dictionary:", marks)

# Example output:
# Enter subject 1 name: Math
# Enter marks for Math: 95
# Enter subject 2 name: Physics  
# Enter marks for Physics: 88
# Enter subject 3 name: Chemistry
# Enter marks for Chemistry: 92
# Final marks dictionary: {'Math': 95.0, 'Physics': 88.0, 'Chemistry': 92.0}
```

### 4. Store 9 and 9.0 as Separate Values in Set
Figure out a way to store 9 and 9.0 as separate values in the set.

```python
# Problem: Sets treat 9 and 9.0 as the same value
regular_set = {9, 9.0}
print(regular_set)  # Output: {9} - only one value stored

# Solution: Convert to strings or use tuples with type info
solution_set = {"9", "9.0"}  # Using strings
print(solution_set)  # Output: {'9', '9.0'}

# Alternative solution: Store as tuples with type information
type_set = {(9, int), (9.0, float)}
print(type_set)  # Output: {(9, <class 'int'>), (9.0, <class 'float'>)}

# Another solution: Store with type names as strings
mixed_set = {("9", "int"), ("9.0", "float")}
print(mixed_set)  # Output: {('9', 'int'), ('9.0', 'float')}
```

## Summary

### Dictionary vs Set Comparison

| Feature | Dictionary | Set |
|---------|------------|-----|
| Structure | Key-Value pairs | Unique elements only |
| Access | By key: `dict[key]` | No direct access (membership testing) |
| Duplicates | No duplicate keys | No duplicate elements |
| Ordering | Unordered (Python 3.7+ maintains insertion order) | Unordered |
| Mutability | Mutable | Mutable (but elements must be immutable) |
| Use Case | Store related data | Mathematical set operations, remove duplicates |

---

*These notes cover Python dictionaries and sets, their properties, methods, and practical applications with solved examples.*
