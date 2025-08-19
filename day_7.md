# Python Programming - Lecture 7 Notes

## File I/O in Python

**File I/O (Input/Output)** allows Python to perform operations on files, such as reading and writing data.

## Types of Files

### 1. Text Files
Files that contain human-readable text:
- `.txt` - Plain text files
- `.docx` - Microsoft Word documents
- `.log` - Log files
- `.csv` - Comma-separated values
- `.json` - JavaScript Object Notation

### 2. Binary Files
Files that contain binary data (not human-readable):
- `.mp4` - Video files
- `.mov` - Movie files
- `.png` - Image files
- `.jpeg` / `.jpg` - Image files
- `.pdf` - Portable Document Format
- `.exe` - Executable files

## Open, Read & Close File

### Basic File Operations
We must open a file before reading or writing to it.

### Opening a File
```python
f = open("file_name", "mode")
```

### File Modes
- **`r`** - Read mode (default)
- **`w`** - Write mode (overwrites existing content)
- **`a`** - Append mode (adds to existing content)
- **`x`** - Exclusive creation mode
- **`r+`** - Read and write mode

### Basic File Handling Example
```python
# Open file
f = open("sample.txt", "r")

# Read file content
data = f.read()

# Close file
f.close()
```

## Reading a File

### 1. `read()` - Read Entire File
```python
f = open("sample.txt", "r")
data = f.read()  # Reads entire file content
print(data)
f.close()
```

### 2. `readline()` - Read One Line at a Time
```python
f = open("sample.txt", "r")
data = f.readline()  # Reads only one line
print(data)
f.close()
```

### 3. `readlines()` - Read All Lines into a List
```python
f = open("sample.txt", "r")
lines = f.readlines()  # Returns list of all lines
for line in lines:
    print(line.strip())  # strip() removes newline characters
f.close()
```

## Writing to a File

### Write Mode (`w`) - Overwrites Entire File
```python
f = open("demo.txt", "w")
f.write("this is a new line")  # Overwrites the entire file
f.close()
```

### Append Mode (`a`) - Adds to Existing File
```python
f = open("demo.txt", "a")
f.write("this is a new line")  # Adds to the end of file
f.close()
```

### Multiple Write Operations
```python
f = open("demo.txt", "w")
f.write("Line 1\n")
f.write("Line 2\n")
f.write("Line 3\n")
f.close()
```

## with Statement (Recommended)

The **`with`** statement automatically handles file closing, even if an error occurs.

### Syntax
```python
with open("filename", "mode") as f:
    # file operations
```

### Examples
```python
# Reading with 'with' statement
with open("demo.txt", "r") as f:
    data = f.read()
    print(data)
# File automatically closed after the block

# Writing with 'with' statement
with open("demo.txt", "w") as f:
    f.write("Hello World!")

# Appending with 'with' statement
with open("demo.txt", "a") as f:
    f.write("\nNew line added")
```

## Deleting a File

To delete a file, we use the **`os`** module.

### Import and Delete
```python
import os

# Delete a file
os.remove("filename.txt")

# Check if file exists before deleting
if os.path.exists("filename.txt"):
    os.remove("filename.txt")
    print("File deleted successfully")
else:
    print("File does not exist")
```

### About Modules
A **module** is like a code library - a file written by another programmer that contains functions we can use.

## Practice Problems

### Problem 1: Create and Populate a File
Create a new file "practice.txt" using Python. Add the following data in it:
```
Hi everyone
we are learning File I/O
using Java.
I like programming in Java.
```

**Solution:**
```python
# Create and write to file
with open("practice.txt", "w") as f:
    f.write("Hi everyone\n")
    f.write("we are learning File I/O\n")
    f.write("using Java.\n")
    f.write("I like programming in Java.")

print("File created successfully!")
```

### Problem 2: Replace All Occurrences of "java" with "python"
Write a function that replaces all occurrences of "java" with "python" in the above file.

**Solution:**
```python
def replace_java_with_python(filename):
    # Read the file content
    with open(filename, "r") as f:
        content = f.read()
    
    # Replace "java" with "python" (case-insensitive)
    updated_content = content.replace("Java", "Python")
    updated_content = updated_content.replace("java", "python")
    
    # Write back to file
    with open(filename, "w") as f:
        f.write(updated_content)
    
    print("Replacement completed!")

# Call the function
replace_java_with_python("practice.txt")
```

### Problem 3: Search for a Word in File
Search if the word "learning" exists in the file or not.

**Solution:**
```python
def search_word_in_file(filename, word):
    with open(filename, "r") as f:
        content = f.read()
    
    if word.lower() in content.lower():
        print(f"'{word}' found in the file!")
        return True
    else:
        print(f"'{word}' not found in the file!")
        return False

# Search for "learning"
search_word_in_file("practice.txt", "learning")
```

### Problem 4: Count Even Numbers from CSV
From a file containing numbers separated by commas, print the count of even numbers.

**Solution:**
```python
def count_even_numbers(filename):
    try:
        with open(filename, "r") as f:
            content = f.read().strip()
        
        # Split by comma and convert to integers
        numbers = [int(x.strip()) for x in content.split(",")]
        
        # Count even numbers
        even_count = sum(1 for num in numbers if num % 2 == 0)
        
        print(f"Count of even numbers: {even_count}")
        return even_count
        
    except FileNotFoundError:
        print("File not found!")
    except ValueError:
        print("Invalid data in file!")

# Create a sample file with numbers
with open("numbers.txt", "w") as f:
    f.write("1,2,3,4,5,6,7,8,9,10")

# Count even numbers
count_even_numbers("numbers.txt")
```

### Problem 5: Find Line Number of a Word
Write a function to find in which line of the file the word "learning" occurs first. Print -1 if word not found.

**Solution:**
```python
def find_word_line_number(filename, word):
    try:
        with open(filename, "r") as f:
            lines = f.readlines()
        
        for line_num, line in enumerate(lines, 1):  # Start counting from 1
            if word.lower() in line.lower():
                print(f"'{word}' found on line {line_num}")
                return line_num
        
        print(f"'{word}' not found. Returning -1")
        return -1
        
    except FileNotFoundError:
        print("File not found!")
        return -1

# Find "learning" in the file
find_word_line_number("practice.txt", "learning")
```

## Complete Example: File Management System

```python
import os

def file_manager():
    while True:
        print("\n--- File Manager ---")
        print("1. Create file")
        print("2. Read file")
        print("3. Write to file")
        print("4. Append to file")
        print("5. Delete file")
        print("6. Exit")
        
        choice = input("Enter your choice (1-6): ")
        
        if choice == '1':
            filename = input("Enter filename: ")
            with open(filename, "w") as f:
                content = input("Enter content: ")
                f.write(content)
            print("File created successfully!")
            
        elif choice == '2':
            filename = input("Enter filename: ")
            try:
                with open(filename, "r") as f:
                    content = f.read()
                    print("File content:")
                    print(content)
            except FileNotFoundError:
                print("File not found!")
                
        elif choice == '3':
            filename = input("Enter filename: ")
            with open(filename, "w") as f:
                content = input("Enter content: ")
                f.write(content)
            print("Content written successfully!")
            
        elif choice == '4':
            filename = input("Enter filename: ")
            with open(filename, "a") as f:
                content = input("Enter content to append: ")
                f.write("\n" + content)
            print("Content appended successfully!")
            
        elif choice == '5':
            filename = input("Enter filename to delete: ")
            if os.path.exists(filename):
                os.remove(filename)
                print("File deleted successfully!")
            else:
                print("File not found!")
                
        elif choice == '6':
            print("Goodbye!")
            break
            
        else:
            print("Invalid choice!")

# Uncomment to run the file manager
# file_manager()
```

## Best Practices for File Handling

### 1. Always Use `with` Statement
```python
# Good practice
with open("file.txt", "r") as f:
    data = f.read()

# Avoid this
f = open("file.txt", "r")
data = f.read()
f.close()  # Easy to forget!
```

### 2. Handle Exceptions
```python
try:
    with open("file.txt", "r") as f:
        data = f.read()
except FileNotFoundError:
    print("File not found!")
except PermissionError:
    print("Permission denied!")
```

### 3. Use Appropriate File Modes
- Use `r` for reading only
- Use `w` for writing (overwrites)
- Use `a` for appending
- Use `x` for exclusive creation

### 4. Close Files Properly
The `with` statement automatically closes files, preventing resource leaks.

---

*These notes cover Python File I/O operations, including reading, writing, deleting files, and practical applications with complete examples.*
