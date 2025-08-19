# Python Programming - Lecture 2 Notes

## Strings

A **string** is a data type that stores a sequence of characters.

### String Creation
```python
name = "hello"
greeting = "world"
```

## Basic String Operations

### 1. Concatenation
Joining two or more strings together:

```python
str1 = "hello"
str2 = "world"
result = str1 + str2  # "helloworld"

# With space
result = str1 + " " + str2  # "hello world"
```

### 2. Length of String
Get the number of characters in a string:

```python
str = "hello"
length = len(str)  # Result: 5
```

## Indexing

Strings are indexed starting from 0. Each character has a position number.

```python
str = "Apna_College"
#      0123456789...
```

### Index Positions:
```
A p n a _ C o l l e g  e
0 1 2 3 4 5 6 7 8 9 10 11
```

### Accessing Characters:
```python
str = "Apna_College"
print(str[0])   # Output: 'A'
print(str[1])   # Output: 'p'
print(str[4])   # Output: '_'
```

### Important Note:
```python
str[0] = 'B'  # NOT ALLOWED - Strings are immutable in Python
```

## Slicing

Slicing allows you to access parts of a string using the syntax:
**`str[starting_idx : ending_idx]`** (ending index is not included)

### Basic Slicing Examples:
```python
str = "ApnaCollege"

# Get characters from index 1 to 3 (4 is excluded)
print(str[1:4])   # Output: "pna"

# From beginning to index 3
print(str[:4])    # Same as str[0:4] → "Apna"

# From index 1 to end
print(str[1:])    # Same as str[1:len(str)] → "pnaCollege"
```

## Negative Indexing

Python supports negative indexing, where -1 refers to the last character:

```python
str = "Apple"
```

### Negative Index Positions:
```
A  p  p  l  e
-5 -4 -3 -2 -1
```

### Negative Slicing Example:
```python
str = "Apple"
print(str[-3:-1])  # Output: "pl"
```

## String Functions (Methods)

Python provides many built-in string methods:

### 1. `endswith()`
```python
str = "I am a coder."
print(str.endswith("er."))  # Returns True if string ends with substring
```

### 2. `count()`
```python
str = "I am a coder."
print(str.count("am"))  # Counts occurrences of substring in string
```

### 3. `capitalize()`
```python
str = "hello world"
print(str.capitalize())  # Capitalizes first character → "Hello world"
```

### 4. `find()`
```python
str = "I am a coder."
print(str.find("coder"))  # Returns first index of first occurrence
```

### 5. `replace()`
```python
str = "I am a coder."
new_str = str.replace("coder", "programmer")  # Replaces all occurrences
```

## String Methods Practice Problems

### 1. Input User's First Name and Print Length
```python
name = input("Enter your first name: ")
print("Length of your name:", len(name))
```

### 2. Find Occurrence of '$' in a String
```python
text = input("Enter a string: ")
count = text.count('$')
print("Number of '$' symbols:", count)
```

## Conditional Statements

Conditional statements allow programs to make decisions based on conditions.

### if-elif-else Syntax:
```python
if(condition):
    Statement1
elif(condition):
    Statement2
else:
    StatementN
```

### Example: Student Grading System
```python
marks = float(input("Enter marks: "))

if marks >= 90:
    grade = "A"
elif marks >= 80:
    grade = "B"
elif marks >= 70:
    grade = "C"
else:
    grade = "D"

print("Grade:", grade)
```

### Grading Criteria:
- **marks >= 90**: grade = "A"
- **90 > marks >= 80**: grade = "B"
- **80 > marks >= 70**: grade = "C"
- **70 > marks**: grade = "D"

## Conditional Statements Practice Problems

### 1. Check if Number is Odd or Even
```python
number = int(input("Enter a number: "))

if number % 2 == 0:
    print("Even")
else:
    print("Odd")
```

### 2. Find Greatest of 3 Numbers
```python
a = int(input("Enter first number: "))
b = int(input("Enter second number: "))
c = int(input("Enter third number: "))

if a >= b and a >= c:
    print("Greatest number is:", a)
elif b >= c:
    print("Greatest number is:", b)
else:
    print("Greatest number is:", c)
```

### 3. Check if Number is Multiple of 7
```python
number = int(input("Enter a number: "))

if number % 7 == 0:
    print(f"{number} is a multiple of 7")
else:
    print(f"{number} is not a multiple of 7")
```

---

*These notes cover Python strings, string operations, indexing, slicing, string methods, and conditional statements with practical examples and exercises.*
