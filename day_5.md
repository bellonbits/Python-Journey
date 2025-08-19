# Python Programming - Lecture 5 Notes

## Loops in Python

**Loops** are used to repeat instructions.

### Common Use Cases:
- Print "hello" 5 times
- Print numbers from 1 to 5
- Show infinite iterations
- Process each element in a collection

## While Loops

A **while loop** repeats a block of code as long as a condition is true.

### Syntax:
```python
while condition:
    # some work
```

### Basic Examples:
```python
# Print hello 5 times
count = 1
while count <= 5:
    print("hello")
    count += 1

# Print numbers from 1 to 5
i = 1
while i <= 5:
    print(i)
    i += 1
```

## While Loop Practice Problems

### 1. Print Numbers from 1 to 100
```python
i = 1
while i <= 100:
    print(i)
    i += 1
```

### 2. Print Elements of a List Using Loop
```python
numbers = [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
i = 0
while i < len(numbers):
    print(numbers[i])
    i += 1
```

### 3. Print Numbers from 100 to 1
```python
i = 100
while i >= 1:
    print(i)
    i -= 1
```

### 4. Print Multiplication Table of a Number n
```python
n = int(input("Enter a number: "))
i = 1
while i <= 10:
    print(f"{n} x {i} = {n * i}")
    i += 1
```

### 5. Search for a Number x in Tuple Using Loop
```python
numbers = (1, 4, 9, 16, 25, 36, 49, 64, 81, 100)
x = int(input("Enter number to search: "))
i = 0
found = False

while i < len(numbers):
    if numbers[i] == x:
        print(f"Number {x} found at index {i}")
        found = True
        break
    i += 1

if not found:
    print(f"Number {x} not found")
```

## Break & Continue Statements

### Break Statement
**Break** is used to terminate the loop when encountered.

#### Example: Stop Search When Found
```python
numbers = [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
x = 25

for num in numbers:
    if num == x:
        print(f"Found {x}!")
        break  # Exit the loop immediately
    print(f"Checking {num}")
```

### Continue Statement
**Continue** terminates execution in the current iteration and continues execution of the loop with the next iteration.

#### Example: Print All Numbers but Not Multiples of 3
```python
for i in range(1, 11):
    if i % 3 == 0:
        continue  # Skip this iteration
    print(i)
# Output: 1, 2, 4, 5, 7, 8, 10
```

## For Loops

**For loops** are used for sequential traversal of lists, strings, tuples, etc.

### Basic Syntax:
```python
for el in list:
    # some work
```

### Examples:
```python
# Traverse a list
fruits = ["apple", "banana", "orange"]
for fruit in fruits:
    print(fruit)

# Traverse a string
name = "Python"
for char in name:
    print(char)

# Traverse a tuple
numbers = (1, 2, 3, 4, 5)
for num in numbers:
    print(num)
```

## For Loop with Else

The `else` clause executes when the loop completes normally (not terminated by break).

### Syntax:
```python
for el in list:
    # some work
else:
    # work when loop ends normally
```

### Example:
```python
numbers = [1, 2, 3, 4, 5]
target = 10

for num in numbers:
    if num == target:
        print("Found!")
        break
else:
    print("Not found!")  # This executes if break is never called
```

## For Loop Practice Problems

### 1. Print Elements of a List
```python
numbers = [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
for num in numbers:
    print(num)
```

### 2. Search for a Number x in Tuple Using For Loop
```python
numbers = (1, 4, 9, 16, 25, 36, 49, 64, 81, 100)
x = int(input("Enter number to search: "))

for i, num in enumerate(numbers):
    if num == x:
        print(f"Number {x} found at index {i}")
        break
else:
    print(f"Number {x} not found")
```

## range() Function

The **range()** function returns a sequence of numbers.

### Syntax:
```python
range(start?, stop, step?)
```

- **start**: Starting number (default: 0)
- **stop**: Stopping number (not included)
- **step**: Step size (default: 1)

### Examples:
```python
# range(stop)
for i in range(5):
    print(i)  # Output: 0, 1, 2, 3, 4

# range(start, stop)
for i in range(2, 8):
    print(i)  # Output: 2, 3, 4, 5, 6, 7

# range(start, stop, step)
for i in range(0, 10, 2):
    print(i)  # Output: 0, 2, 4, 6, 8
```

## Range() Practice Problems

### 1. Print Numbers from 1 to 100 (Using For & Range)
```python
for i in range(1, 101):
    print(i)
```

### 2. Print Numbers from 100 to 1 (Using For & Range)
```python
for i in range(100, 0, -1):
    print(i)
```

### 3. Print Multiplication Table of Number n (Using For & Range)
```python
n = int(input("Enter a number: "))
for i in range(1, 11):
    print(f"{n} x {i} = {n * i}")
```

## pass Statement

**pass** is a null statement that does nothing. It is used as a placeholder for future code.

### Uses:
- Placeholder for future implementation
- Exception handling
- Creating empty functions or classes

### Examples:
```python
# Placeholder in loop
for el in range(10):
    pass  # Do nothing, placeholder

# Empty function
def future_function():
    pass  # Will implement later

# Conditional placeholder
x = 10
if x > 5:
    pass  # TODO: implement logic
else:
    print("x is small")
```

## Additional Practice Problems

### 1. Find Sum of First n Numbers (Using While)
```python
n = int(input("Enter n: "))
i = 1
sum = 0

while i <= n:
    sum += i
    i += 1

print(f"Sum of first {n} numbers: {sum}")
```

### 2. Find Factorial of First n Numbers (Using For)
```python
n = int(input("Enter n: "))
factorial = 1

for i in range(1, n + 1):
    factorial *= i

print(f"Factorial of {n}: {factorial}")
```

## Summary

### Loop Types Comparison

| Feature | While Loop | For Loop |
|---------|------------|----------|
| Use Case | Condition-based repetition | Sequential traversal |
| Syntax | `while condition:` | `for item in sequence:` |
| Control | Manual counter management | Automatic iteration |
| Best For | Unknown iterations | Known collections/ranges |

### Control Statements

| Statement | Purpose | Effect |
|-----------|---------|--------|
| `break` | Exit loop | Terminates loop immediately |
| `continue` | Skip iteration | Jumps to next iteration |
| `pass` | Do nothing | Placeholder, no operation |

---

*These notes cover Python loops (while, for), control statements (break, continue, pass), range() function, and practical programming exercises.*
