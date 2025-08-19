# Python Programming - Lecture 8 Notes

## Object-Oriented Programming (OOP) in Python

**Object-Oriented Programming** is a programming paradigm that uses objects and classes to map with real-world scenarios. This approach makes code more organized, reusable, and easier to understand.

### Why OOP?
- Models real-world entities as objects
- Improves code organization and structure
- Promotes code reusability
- Makes complex systems easier to manage

## Class & Object in Python

### Class
A **class** is a blueprint for creating objects. It defines the structure and behavior that objects will have.

### Object
An **object** (or instance) is a specific implementation of a class.

### Basic Class Example
```python
class Student:
    name = "karan kumar"  # Class attribute

# Creating object (instance)
s1 = Student()
print(s1.name)  # Output: karan kumar
```

### Real-World Analogy
- **Class**: Car blueprint (defines what a car should have)
- **Object**: Specific car (Toyota Camry, Honda Civic, etc.)

## Class & Instance Attributes

### Class Attributes
- Belong to the class itself
- Shared by all instances of the class
- Accessed using `Class.attr`

### Instance Attributes
- Belong to specific objects
- Different for each instance
- Accessed using `obj.attr`

### Example
```python
class Student:
    school = "ABC School"  # Class attribute
    
    def __init__(self, name):
        self.name = name  # Instance attribute

# Creating objects
s1 = Student("Alice")
s2 = Student("Bob")

# Class attribute (same for all)
print(Student.school)  # ABC School
print(s1.school)       # ABC School
print(s2.school)       # ABC School

# Instance attributes (different for each)
print(s1.name)  # Alice
print(s2.name)  # Bob
```

## __init__ Function (Constructor)

The **`__init__()`** function is a special method called a **constructor**. It is automatically executed when an object is created.

### Purpose:
- Initialize object attributes
- Set up the object's initial state
- Perform any setup required when creating an object

### Basic Constructor Example
```python
class Student:
    def __init__(self, fullname):
        self.name = fullname  # Initialize instance attribute

# Creating object
s1 = Student("karan")
print(s1.name)  # Output: karan
```

### The `self` Parameter
- **`self`** is a reference to the current instance of the class
- Used to access variables and methods that belong to the class
- Must be the first parameter in all instance methods
- Automatically passed when calling methods

### Multiple Parameter Constructor
```python
class Student:
    def __init__(self, name, age, grade):
        self.name = name
        self.age = age
        self.grade = grade

# Creating object with multiple parameters
s1 = Student("Alice", 18, "A")
print(f"Name: {s1.name}, Age: {s1.age}, Grade: {s1.grade}")
```

## Methods

**Methods** are functions that belong to objects. They define the behavior of objects.

### Basic Method Example
```python
class Student:
    def __init__(self, fullname):
        self.name = fullname
    
    def hello(self):
        print("hello", self.name)

# Creating object and calling method
s1 = Student("karan")
s1.hello()  # Output: hello karan
```

### Methods with Parameters
```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def introduce(self, greeting="Hello"):
        print(f"{greeting}, I'm {self.name} and I'm {self.age} years old")
    
    def celebrate_birthday(self):
        self.age += 1
        print(f"Happy Birthday! Now I'm {self.age} years old")

# Usage
s1 = Student("Alice", 17)
s1.introduce()              # Hello, I'm Alice and I'm 17 years old
s1.introduce("Hi there")    # Hi there, I'm Alice and I'm 17 years old
s1.celebrate_birthday()     # Happy Birthday! Now I'm 18 years old
```

## Practice Problem 1: Student Average Calculator

Create a student class that takes name & marks of 3 subjects as arguments in constructor. Then create a method to print the average.

### Solution:
```python
class Student:
    def __init__(self, name, marks1, marks2, marks3):
        self.name = name
        self.marks1 = marks1
        self.marks2 = marks2
        self.marks3 = marks3
    
    def get_average(self):
        average = (self.marks1 + self.marks2 + self.marks3) / 3
        return average
    
    def print_average(self):
        avg = self.get_average()
        print(f"{self.name}'s average marks: {avg:.2f}")
        return avg

# Test the class
s1 = Student("Alice", 85, 92, 78)
s1.print_average()  # Alice's average marks: 85.00

s2 = Student("Bob", 95, 88, 91)
s2.print_average()  # Bob's average marks: 91.33
```

## Static Methods

**Static methods** are methods that don't use the `self` parameter. They work at the class level rather than the instance level.

### Characteristics:
- Don't access instance attributes
- Don't modify object state
- Can be called without creating an object
- Use `@staticmethod` decorator

### Example:
```python
class Student:
    def __init__(self, name):
        self.name = name
    
    @staticmethod
    def college():
        print("ABC College")
    
    @staticmethod
    def get_school_info():
        return "ABC College - Established 1995"

# Calling static method without creating object
Student.college()  # Output: ABC College
print(Student.get_school_info())  # ABC College - Established 1995

# Can also call with object (but not recommended)
s1 = Student("Alice")
s1.college()  # Output: ABC College
```

### About Decorators
**Decorators** allow us to wrap another function to extend the behavior of the wrapped function, without permanently modifying it.

## OOP Principles

### 1. Abstraction
**Hiding the implementation details** of a class and only showing the essential features to the user.

```python
class Car:
    def __init__(self, brand):
        self.brand = brand
        self.__engine_temp = 0  # Private attribute
    
    def start(self):
        self.__check_engine()  # Private method
        print(f"{self.brand} car started!")
    
    def __check_engine(self):  # Private method (abstracted)
        self.__engine_temp = 90
        print("Engine check complete")

# User only needs to know about start(), not internal details
car = Car("Toyota")
car.start()  # Toyota car started!
```

### 2. Encapsulation
**Wrapping data and functions into a single unit** (object). This bundles related data and methods together.

```python
class BankAccount:
    def __init__(self, account_number, initial_balance):
        self.account_number = account_number
        self.__balance = initial_balance  # Encapsulated data
    
    def deposit(self, amount):  # Method to interact with data
        if amount > 0:
            self.__balance += amount
            print(f"Deposited ${amount}. New balance: ${self.__balance}")
    
    def get_balance(self):  # Controlled access to data
        return self.__balance

# Data and methods are encapsulated together
account = BankAccount("12345", 1000)
account.deposit(500)  # Deposited $500. New balance: $1500
```

## Practice Problem 2: Account Class

Create an Account class with 2 attributes - balance & account no. Create methods for debit, credit & printing the balance.

### Solution:
```python
class Account:
    def __init__(self, account_no, initial_balance=0):
        self.account_no = account_no
        self.balance = initial_balance
        print(f"Account {self.account_no} created with balance: ${self.balance}")
    
    def credit(self, amount):
        """Add money to the account"""
        if amount > 0:
            self.balance += amount
            print(f"${amount} credited. New balance: ${self.balance}")
        else:
            print("Credit amount must be positive!")
    
    def debit(self, amount):
        """Remove money from the account"""
        if amount > 0:
            if amount <= self.balance:
                self.balance -= amount
                print(f"${amount} debited. New balance: ${self.balance}")
            else:
                print("Insufficient balance!")
        else:
            print("Debit amount must be positive!")
    
    def print_balance(self):
        """Display current balance"""
        print(f"Account {self.account_no} - Current Balance: ${self.balance}")
    
    def get_balance(self):
        """Return current balance"""
        return self.balance

# Test the Account class
acc1 = Account("12345", 1000)  # Account 12345 created with balance: $1000

acc1.print_balance()  # Account 12345 - Current Balance: $1000
acc1.credit(500)      # $500 credited. New balance: $1500
acc1.debit(200)       # $200 debited. New balance: $1300
acc1.debit(2000)      # Insufficient balance!
acc1.print_balance()  # Account 12345 - Current Balance: $1300

# Create another account
acc2 = Account("67890")  # Account 67890 created with balance: $0
acc2.credit(1000)        # $1000 credited. New balance: $1000
acc2.print_balance()     # Account 67890 - Current Balance: $1000
```

## Complete Example: Enhanced Student Management System

```python
class Student:
    # Class attribute
    school_name = "Python Programming School"
    total_students = 0
    
    def __init__(self, name, age, student_id):
        # Instance attributes
        self.name = name
        self.age = age
        self.student_id = student_id
        self.grades = []
        
        # Increment total students
        Student.total_students += 1
        print(f"Student {self.name} enrolled successfully!")
    
    def add_grade(self, subject, marks):
        """Add a grade for a subject"""
        self.grades.append({"subject": subject, "marks": marks})
        print(f"Grade added: {subject} - {marks}")
    
    def get_average(self):
        """Calculate average of all grades"""
        if not self.grades:
            return 0
        total_marks = sum(grade["marks"] for grade in self.grades)
        return total_marks / len(self.grades)
    
    def display_report_card(self):
        """Display complete student information"""
        print(f"\n--- Report Card ---")
        print(f"Name: {self.name}")
        print(f"Age: {self.age}")
        print(f"Student ID: {self.student_id}")
        print(f"School: {Student.school_name}")
        
        if self.grades:
            print("Grades:")
            for grade in self.grades:
                print(f"  {grade['subject']}: {grade['marks']}")
            print(f"Average: {self.get_average():.2f}")
        else:
            print("No grades recorded")
        print("-" * 20)
    
    @staticmethod
    def get_school_info():
        """Get school information"""
        return f"Welcome to {Student.school_name}! Total Students: {Student.total_students}"
    
    @staticmethod
    def compare_students(student1, student2):
        """Compare two students' averages"""
        avg1 = student1.get_average()
        avg2 = student2.get_average()
        
        if avg1 > avg2:
            return f"{student1.name} has higher average ({avg1:.2f}) than {student2.name} ({avg2:.2f})"
        elif avg2 > avg1:
            return f"{student2.name} has higher average ({avg2:.2f}) than {student1.name} ({avg1:.2f})"
        else:
            return f"{student1.name} and {student2.name} have the same average ({avg1:.2f})"

# Test the enhanced system
print(Student.get_school_info())  # Welcome to Python Programming School! Total Students: 0

# Create students
alice = Student("Alice Johnson", 16, "S001")
bob = Student("Bob Smith", 17, "S002")

print(Student.get_school_info())  # Total Students: 2

# Add grades
alice.add_grade("Math", 95)
alice.add_grade("Science", 88)
alice.add_grade("English", 92)

bob.add_grade("Math", 87)
bob.add_grade("Science", 94)
bob.add_grade("English", 89)

# Display report cards
alice.display_report_card()
bob.display_report_card()

# Compare students
print(Student.compare_students(alice, bob))
```

## Summary

### Key Concepts Covered:
1. **Classes and Objects**: Blueprint and instances
2. **Attributes**: Class vs instance attributes
3. **Constructor**: `__init__()` method for initialization
4. **Methods**: Functions that belong to objects
5. **Static Methods**: Class-level methods with `@staticmethod`
6. **Abstraction**: Hiding implementation details
7. **Encapsulation**: Bundling data and methods together

### Benefits of OOP:
- **Modularity**: Code is organized into classes
- **Reusability**: Classes can be used multiple times
- **Maintainability**: Easier to modify and extend
- **Real-world modeling**: Maps well to real-world entities

---

*These notes cover the fundamentals of Object-Oriented Programming in Python, including classes, objects, methods, and key OOP principles with practical examples.*
