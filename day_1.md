# Python Programming - Lecture 1 Notes

## Programming Overview

**Programming → Translator (Compiler/Interpreter) → Machine Code**

Programming languages need translators to convert human-readable code into machine code that computers can execute.

## What is Python?

Python is a programming language with the following characteristics:

- **Simple & Easy**: Python has a clean, readable syntax
- **Free & Open Source**: Available for everyone to use and modify
- **High Level Language**: Abstracts away complex system details
- **Developed by Guido van Rossum**: Created in the late 1980s
- **Portable**: Runs on multiple platforms (Windows, Mac, Linux, etc.)

## Our First Program

```python
print("Hello World")
```

This simple program outputs "Hello World" to the screen.

## Python Character Set

Python can work with various types of characters:

- **Letters**: A to Z, a to z
- **Digits**: 0 to 9
- **Special Symbols**: +, -, *, /, etc.
- **Whitespaces**: Blank space, tab, carriage return, newline, formfeed
- **Other Characters**: Python can process all ASCII and Unicode characters as part of data or literals

## Variables

A **variable** is a name given to a memory location in a program.

### Example:
```python
name = "Shradha"
age = 23
price = 25.99
```

### Memory Representation:
```
Memory Location → Value
name           → "Shradha"
age            → 23
price          → 25.99
```

## Rules for Identifiers

- Must start with a letter (a-z, A-Z) or underscore (_)
- Can contain letters, digits, and underscores
- Cannot contain spaces or special characters
- Cannot be a Python keyword
- Case-sensitive (e.g., `name` and `Name` are different)

## Data Types

Python has several built-in data types:

1. **Integers**: Whole numbers (e.g., 23, -5, 0)
2. **String**: Text data (e.g., "Hello", "Python")
3. **Float**: Decimal numbers (e.g., 25.99, 3.14)
4. **Boolean**: True or False values
5. **None**: Represents absence of value

### Data Type Examples:
```python
# Integer
age = 25

# String
name = "Python"

# Float
price = 99.99

# Boolean
is_student = True

# None
value = None
```

## Keywords

Keywords are **reserved words** in Python that have special meaning and cannot be used as variable names.

**Note**: `False` should be uppercase in Python (it's actually `False`, not `false`)

Common Python keywords include: `and`, `or`, `not`, `if`, `else`, `for`, `while`, `def`, `class`, `import`, `from`, `as`, `True`, `False`, `None`, etc.

## Comments in Python

```python
# Single Line Comment

"""
Multi Line
Comment
"""
```

Comments are used to explain code and are ignored by the Python interpreter.

## Types of Operators

An **operator** is a symbol that performs a certain operation between operands.

### 1. Arithmetic Operators
- `+` (Addition)
- `-` (Subtraction)
- `*` (Multiplication)
- `/` (Division)
- `%` (Modulus)
- `**` (Exponentiation)

### 2. Relational/Comparison Operators
- `==` (Equal to)
- `!=` (Not equal to)
- `>` (Greater than)
- `<` (Less than)
- `>=` (Greater than or equal to)
- `<=` (Less than or equal to)

### 3. Assignment Operators
- `=` (Assignment)
- `+=` (Add and assign)
- `-=` (Subtract and assign)
- `*=` (Multiply and assign)
- `/=` (Divide and assign)
- `%=` (Modulus and assign)
- `**=` (Exponent and assign)

### 4. Logical Operators
- `not` (Logical NOT)
- `and` (Logical AND)
- `or` (Logical OR)

## Type Conversion

Python automatically converts data types in certain operations:

```python
a, b = 1, 2.0
sum = a + b  # Result: 3.0 (int converted to float)

a, b = 1, "2"
sum = a + b  # Error! Cannot add int and string
```

## Type Casting

Explicit conversion of one data type to another:

```python
a, b = 1, "2"
c = int(b)    # Convert string "2" to integer 2
sum = a + c   # Result: 3
```

### Type Casting Functions:
- `int()` - Convert to integer
- `float()` - Convert to float
- `str()` - Convert to string
- `bool()` - Convert to boolean

## Input in Python

The `input()` statement is used to accept values from the user via keyboard.

**Important**: The result of `input()` is always a string!

```python
# String input (default)
name = input()

# Integer input
age = int(input())

# Float input
price = float(input())
```

### Examples:
```python
# String input
name = input("Enter your name: ")

# Integer input
age = int(input("Enter your age: "))

# Float input
height = float(input("Enter your height: "))
```

## Practice Problems

### 1. Sum of Two Numbers
Write a program to input 2 numbers and print their sum.

```python
a = int(input("Enter first number: "))
b = int(input("Enter second number: "))
sum = a + b
print("Sum:", sum)
```

### 2. Area of a Square
Write a program to input the side of a square and print its area.

```python
side = float(input("Enter side of square: "))
area = side ** 2
print("Area of square:", area)
```

### 3. Average of Two Floating Point Numbers
Write a program to input 2 floating point numbers and print their average.

```python
num1 = float(input("Enter first number: "))
num2 = float(input("Enter second number: "))
average = (num1 + num2) / 2
print("Average:", average)
```

### 4. Comparison of Two Numbers
Write a program to input 2 int numbers, a and b. Print True if a is greater than or equal to b, otherwise print False.

```python
a = int(input("Enter first number: "))
b = int(input("Enter second number: "))
result = a >= b
print(result)
```

---

*These notes cover the fundamental concepts of Python programming including variables, data types, operators, type conversion, input/output, and basic problem-solving.*
