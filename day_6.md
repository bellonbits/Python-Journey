# Python Programming - Lecture 6 Notes

## Functions in Python

A **function** is a block of statements that performs a specific task.

### Function Definition Syntax:
```python
def func_name(param1, param2...):
    # some work
    return val
```

### Function Call:
```python
func_name(arg1, arg2...)  # function call
```

### Basic Example:
```python
def greet(name):
    print(f"Hello, {name}!")
    return f"Greeting sent to {name}"

# Function call
message = greet("Alice")
print(message)
```

## Types of Functions

### 1. Built-in Functions
Python provides many pre-defined functions:

- `print()` - Display output
- `len()` - Get length of collection
- `type()` - Get data type
- `range()` - Generate sequence of numbers
- `input()` - Get user input
- `int()`, `float()`, `str()` - Type conversion

### 2. User-defined Functions
Functions created by programmers for specific tasks:

```python
def add_numbers(a, b):
    sum = a + b
    return sum

result = add_numbers(5, 3)
print(result)  # Output: 8
```

## Default Parameters

**Default parameters** allow assigning default values to parameters, which are used when no argument is passed.

### Syntax:
```python
def func_name(param1, param2=default_value):
    # some work
```

### Examples:
```python
def greet(name, greeting="Hello"):
    print(f"{greeting}, {name}!")

greet("Alice")                 # Uses default: "Hello, Alice!"
greet("Bob", "Hi")            # Custom greeting: "Hi, Bob!"
greet("Charlie", "Good morning")  # "Good morning, Charlie!"
```

```python
def calculate_power(base, exponent=2):
    return base ** exponent

print(calculate_power(5))      # Output: 25 (5^2)
print(calculate_power(5, 3))   # Output: 125 (5^3)
```

## Function Practice Problems

### 1. Function to Print List Elements in Single Line
Write a function to print the elements of a list in a single line (list is the parameter).

```python
def print_list_inline(lst):
    for element in lst:
        print(element, end=" ")
    print()  # New line at the end

# Test
numbers = [1, 2, 3, 4, 5]
print_list_inline(numbers)  # Output: 1 2 3 4 5 

# Alternative solution using join
def print_list_inline_v2(lst):
    print(" ".join(map(str, lst)))

print_list_inline_v2(numbers)  # Output: 1 2 3 4 5
```

### 2. Function to Find Factorial of n
Write a function to find the factorial of n (n is the parameter).

```python
def factorial(n):
    if n < 0:
        return "Factorial not defined for negative numbers"
    elif n == 0 or n == 1:
        return 1
    else:
        fact = 1
        for i in range(1, n + 1):
            fact *= i
        return fact

# Test
print(factorial(5))   # Output: 120
print(factorial(0))   # Output: 1
print(factorial(-1))  # Output: Factorial not defined for negative numbers
```

### 3. Function to Print Length of a List
Write a function to print the length of a list (list is the parameter).

```python
def print_list_length(lst):
    length = len(lst)
    print(f"The length of the list is: {length}")
    return length

# Test
fruits = ["apple", "banana", "orange", "mango"]
print_list_length(fruits)  # Output: The length of the list is: 4
```

### 4. Function to Convert USD to INR
Write a function to convert USD to INR.

```python
def usd_to_inr(usd_amount, exchange_rate=83.0):
    inr_amount = usd_amount * exchange_rate
    return inr_amount

def convert_currency():
    usd = float(input("Enter amount in USD: "))
    inr = usd_to_inr(usd)
    print(f"${usd} USD = ₹{inr:.2f} INR")

# Test
print(usd_to_inr(100))      # Output: 8300.0
print(usd_to_inr(50, 82.5)) # Output: 4125.0

# Interactive version
# convert_currency()
```

## Recursion

**Recursion** occurs when a function calls itself repeatedly.

### Key Components:
1. **Base Case**: Condition that stops the recursion
2. **Recursive Case**: Function calls itself with modified parameters

### Example 1: Print Numbers n to 1 Backwards
```python
def print_backwards(n):
    if n == 0:          # Base case
        return
    print(n)
    print_backwards(n - 1)  # Recursive call

print_backwards(5)
# Output:
# 5
# 4
# 3
# 2
# 1
```

### Example 2: Calculate Factorial Using Recursion
```python
def factorial_recursive(n):
    if n == 0 or n == 1:    # Base case
        return 1
    return n * factorial_recursive(n - 1)  # Recursive case

print(factorial_recursive(5))   # Output: 120
print(factorial_recursive(4))   # Output: 24
```

### How Recursion Works (Factorial Example):
```
factorial_recursive(5)
= 5 * factorial_recursive(4)
= 5 * (4 * factorial_recursive(3))
= 5 * (4 * (3 * factorial_recursive(2)))
= 5 * (4 * (3 * (2 * factorial_recursive(1))))
= 5 * (4 * (3 * (2 * 1)))
= 5 * (4 * (3 * 2))
= 5 * (4 * 6)
= 5 * 24
= 120
```

## Recursion Practice Problems

### 1. Recursive Function to Calculate Sum of First n Natural Numbers
```python
def sum_natural_recursive(n):
    if n == 1:              # Base case
        return 1
    return n + sum_natural_recursive(n - 1)  # Recursive case

# Test
print(sum_natural_recursive(5))  # Output: 15 (1+2+3+4+5)
print(sum_natural_recursive(10)) # Output: 55
```

### 2. Recursive Function to Print All Elements in a List
Hint: Use list & index as parameters.

```python
def print_list_recursive(lst, index=0):
    if index == len(lst):   # Base case: reached end of list
        return
    print(lst[index])
    print_list_recursive(lst, index + 1)  # Recursive call with next index

# Test
fruits = ["apple", "banana", "orange", "mango"]
print_list_recursive(fruits)
# Output:
# apple
# banana
# orange
# mango

# Alternative version that returns when list is empty
def print_list_recursive_v2(lst):
    if len(lst) == 0:       # Base case: empty list
        return
    print(lst[0])           # Print first element
    print_list_recursive_v2(lst[1:])  # Recursive call with remaining elements

print_list_recursive_v2(fruits)
```

## Function Types Summary

### Regular Functions
```python
def function_name(parameters):
    # statements
    return value  # optional
```

### Functions with Default Parameters
```python
def function_name(param1, param2=default_value):
    # statements
    return value
```

### Recursive Functions
```python
def recursive_function(parameters):
    if base_condition:      # Base case
        return base_value
    return recursive_function(modified_parameters)  # Recursive case
```

## Best Practices

### 1. Function Naming
- Use descriptive names
- Use snake_case (lowercase with underscores)
- Start with a verb for action functions

### 2. Parameters
- Use default parameters when appropriate
- Keep parameter lists manageable
- Use meaningful parameter names

### 3. Return Values
- Always return a value when the function should produce output
- Use consistent return types
- Document what the function returns

### 4. Recursion Guidelines
- Always define a clear base case
- Ensure the recursive calls move toward the base case
- Consider iterative alternatives for simple problems

---

*These notes cover Python functions, default parameters, recursion concepts, and practical programming exercises with complete solutions.*
