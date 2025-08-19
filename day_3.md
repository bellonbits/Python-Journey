# Python Programming - Lecture 3 Notes

## Lists in Python

A **list** is a built-in data type that stores a set of values.

### Basic List Creation
```python
marks = [87, 64, 33, 95, 76]
```

### Mixed Data Types
Lists can store elements of different types (integer, float, string, etc.):
```python
student = ["Karan", 85, "Delhi"]
# Access: student[0], student[1], student[2]
```

### List Properties
- **Mutable**: Elements can be changed after creation
- **Indexed**: Access elements using index (starting from 0)
- **Dynamic**: Can grow or shrink in size

### Basic List Operations
```python
marks = [87, 64, 33, 95, 76]

# Accessing elements
print(marks[0])  # Output: 87
print(marks[1])  # Output: 64

# Modifying elements (allowed in Python)
student[0] = "Arjun"  # Changes "Karan" to "Arjun"

# Getting length
length = len(student)  # Returns length of list
```

## List Slicing

List slicing works similar to string slicing:
**`list_name[starting_idx : ending_idx]`** (ending index is not included)

### Slicing Examples
```python
marks = [87, 64, 33, 95, 76]

# Basic slicing
print(marks[1:4])   # Output: [64, 33, 95]

# From beginning to index
print(marks[:4])    # Same as marks[0:4] → [87, 64, 33, 95]

# From index to end
print(marks[1:])    # Same as marks[1:len(marks)] → [64, 33, 95, 76]

# Negative slicing
print(marks[-3:-1]) # Output: [33, 95]
```

## List Methods

### 1. `append()` - Add Element at End
```python
list = [2, 1, 3]
list.append(4)
print(list)  # Output: [2, 1, 3, 4]
```

### 2. `insert()` - Insert Element at Specific Index
```python
list = [2, 1, 3]
list.insert(1, 5)  # Insert 5 at index 1
print(list)  # Output: [2, 5, 1, 3]
```

### 3. `sort()` - Sort in Ascending Order
```python
list = [2, 1, 3]
list.sort()
print(list)  # Output: [1, 2, 3]
```

### 4. `reverse()` - Reverse the List
```python
list = [1, 2, 3]
list.reverse()
print(list)  # Output: [3, 2, 1]
```

### 5. `sort(reverse=True)` - Sort in Descending Order
```python
list = [2, 1, 3]
list.sort(reverse=True)
print(list)  # Output: [3, 2, 1]
```

### 6. `remove()` - Remove First Occurrence of Element
```python
list = [2, 1, 3, 1]
list.remove(1)  # Removes first occurrence of 1
print(list)  # Output: [2, 3, 1]
```

### 7. `pop()` - Remove Element at Specific Index
```python
list = [2, 1, 3, 1]
list.pop(1)  # Removes element at index 1
print(list)  # Output: [2, 3, 1]
```

## Tuples in Python

A **tuple** is a built-in data type that lets us create **immutable** sequences of values.

### Tuple Creation
```python
tup = (87, 64, 33, 95, 76)
# Access: tup[0], tup[1], tup[2]...
```

### Tuple Properties
- **Immutable**: Cannot change elements after creation
- **Indexed**: Access elements using index
- **Ordered**: Maintains the order of elements

### Important Notes
```python
tup[0] = 43  # NOT ALLOWED in Python - Tuples are immutable
```

### Different Types of Tuples
```python
tup1 = ()           # Empty tuple
tup2 = (1,)         # Single element tuple (note the comma)
tup3 = (1, 2, 3)    # Multiple elements tuple
```

## Tuple Methods

Tuples have limited methods due to their immutable nature:

### 1. `index()` - Find Index of First Occurrence
```python
tup = (2, 1, 3, 1)
print(tup.index(1))  # Output: 1 (index of first occurrence)
```

### 2. `count()` - Count Total Occurrences
```python
tup = (2, 1, 3, 1)
print(tup.count(1))  # Output: 2 (1 appears twice)
```

## Practice Problems

### 1. Store 3 Favorite Movies
Write a program to ask the user to enter names of their 3 favorite movies and store them in a list.

```python
movies = []
for i in range(3):
    movie = input(f"Enter your favorite movie {i+1}: ")
    movies.append(movie)

print("Your favorite movies are:", movies)
```

### 2. Check if List Contains Palindrome Elements
Write a program to check if a list contains a palindrome of elements.
Examples: `[1, 2, 3, 2, 1]` or `[1, "abc", "abc", 1]`

```python
def is_palindrome(lst):
    # Create a copy and reverse it
    reversed_list = lst.copy()
    reversed_list.reverse()
    
    # Check if original equals reversed
    return lst == reversed_list

# Test examples
list1 = [1, 2, 3, 2, 1]
list2 = [1, "abc", "abc", 1]
list3 = [1, 2, 3, 4, 5]

print(is_palindrome(list1))  # True
print(is_palindrome(list2))  # True
print(is_palindrome(list3))  # False
```

### 3. Count Students with "A" Grade
Write a program to count the number of students with "A" grade in the following tuple:
`["C", "D", "A", "A", "B", "B", "A"]`

```python
grades = ("C", "D", "A", "A", "B", "B", "A")
count_A = grades.count("A")
print(f"Number of students with A grade: {count_A}")
```

### 4. Store Grades in List and Sort from "A" to "D"
Store the above values in a list and sort them from "A" to "D".

```python
# Convert tuple to list
grades_list = ["C", "D", "A", "A", "B", "B", "A"]

# Sort the list
grades_list.sort()
print("Sorted grades:", grades_list)
# Output: ['A', 'A', 'A', 'B', 'B', 'C', 'D']
```

## Summary

### Lists vs Tuples

| Feature | Lists | Tuples |
|---------|-------|---------|
| Mutability | Mutable (can change) | Immutable (cannot change) |
| Syntax | `[1, 2, 3]` | `(1, 2, 3)` |
| Methods | Many methods available | Limited methods |
| Use Case | When data needs to change | When data should remain constant |

---

*These notes cover Python lists and tuples, their properties, methods, slicing operations, and practical applications with examples.*
