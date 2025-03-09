# **2.6. Input and Output (I/O) Operations in Python**  

Python provides various methods for reading from and writing to the console, files, and other data streams.

---
## 2.6.1. Standard Input (User Input)
Python allows you to capture user input through the **`input()` function**.

### 2.6.1.1. Reading Input from the User
```python
name = input("Enter your name: ")
print(f"Hello, {name}!")
```
**Key Points**:
- The input is always returned as a **string**.  
- You need to convert it to **int** or **float** if needed.

### 2.6.1.2. Type Conversion for Input
```python
age = int(input("Enter your age: "))  # Converts to integer
height = float(input("Enter your height in meters: "))  # Converts to float
```

**Error Handling with `try-except`**
```python
try:
    number = int(input("Enter a number: "))
except ValueError:
    print("Invalid input! Please enter an integer.")
```

---

## 2.6.2. Standard Output (Printing Data)
Python provides several ways to display data using the **`print()` function**.

### 2.6.2.1. Basic Printing
```python
print("Hello, World!")
```

### 2.6.2.2. Printing Multiple Values
```python
name = "Alice"
age = 30
print("Name:", name, "Age:", age)  # Using commas
print(f"Name: {name}, Age: {age}")  # Using f-strings
print("Name: {} Age: {}".format(name, age))  # Using `.format()`
```

**Output Formatting Options**
```python
# String alignment
print(f"{'Left':<10} {'Center':^10} {'Right':>10}")  
# Output: Left       Center     Right

# Number formatting
pi = 3.1415926535
print(f"Pi: {pi:.2f}")  # Output: Pi: 3.14
```

**Suppressing Newline (`end` Parameter)**
```python
print("Hello", end=" ")
print("World")  # Output: Hello World
```

---

## 2.6.3. File Handling (Reading & Writing)
Python provides **file handling** functions to read from and write to files.

### 2.6.3.1. Opening Files
```python
file = open("data.txt", "r")  # Opens file in read mode
file.close()  # Always close files after use
```

**Using `with open()` (Recommended)**
```python
with open("data.txt", "r") as file:
    content = file.read()
```
*Advantage*: No need to manually close the file.

---

### 2.6.3.2. Reading Files
**Read the Entire File**
```python
with open("data.txt", "r") as file:
    content = file.read()
    print(content)
```

**Reading Line by Line**
```python
with open("data.txt", "r") as file:
    for line in file:
        print(line.strip())  # `.strip()` removes newline characters
```

**Using `.readlines()`**
```python
with open("data.txt", "r") as file:
    lines = file.readlines()
    print(lines)  # Returns a list of lines
```

---
### 2.6.3.3. Writing to Files
**Writing Mode (`'w'`)**
```python
with open("output.txt", "w") as file:
    file.write("This is a new file.\n")
```
*Caution:* This mode **overwrites** the file if it already exists.

**Appending Mode (`'a'`)**
```python
with open("output.txt", "a") as file:
    file.write("Appending a new line.\n")
```
Keeps the existing content and **adds** new data.

---

### 2.6.3.4. Working with Different File Types
### 2.6.3.4.1 **Handling CSV Files**  

CSV (*Comma-Separated Values*) files store tabular data in a simple text format where each row represents a record, and fields are separated by commas. 

**Reading to a CSV File**
```python
import csv

with open("data.csv", "r") as file:  # Open the file in read mode
    reader = csv.reader(file)  # Create a CSV reader object
    for row in reader:  # Loop through each row
        print(row)  # Print the row as a list
# Output
['Name', 'Age', 'City']
['Alice', '30', 'New York']
['Bob', '25', 'Los Angeles']
```
**Writing to a CSV File**

```python
with open("output.csv", "w", newline="") as file:  # Open file in write mode
    writer = csv.writer(file)  # Create a CSV writer object
    writer.writerow(["Name", "Age"])  # Write header row
    writer.writerow(["Alice", 30])  # Write data row
# In output.csv
Name,Age
Alice,30
```

**Reading CSV Files with a Header**  
If your CSV file has a **header**, use `csv.DictReader()` to access data by column names.

```python
with open("data.csv", "r") as file:
    reader = csv.DictReader(file)  # Reads CSV as dictionaries
    for row in reader:
        print(row["Name"], row["Age"])
# Output:
Alice 30
Bob 25
```

**Writing CSV Files with a Header**  
Use `csv.DictWriter()` to write rows as dictionaries.

```python
with open("output.csv", "w", newline="") as file:
    fieldnames = ["Name", "Age"]
    writer = csv.DictWriter(file, fieldnames=fieldnames)

    writer.writeheader()  # Writes the header row
    writer.writerow({"Name": "Alice", "Age": 30})
    writer.writerow({"Name": "Bob", "Age": 25})
# In output.csv
Name,Age
Alice,30
Bob,25
```

**Handling Different Delimiters**  
Not all CSV files use commas (``,``) as separators. Some use **semicolons** (`;`) or **tabs** (`\t`). You can specify the delimiter:

```python
with open("data.csv", "r") as file:
    reader = csv.reader(file, delimiter=";")  # Change delimiter
    for row in reader:
        print(row)
```

**Summary of CSV Operations**
| Operation | Method | Notes |
|------------|-------------|----------------------------------|
| **Read CSV (list format)** | `csv.reader(file)` | Returns rows as lists |
| **Read CSV (dictionary format)** | `csv.DictReader(file)` | Access columns by name |
| **Write CSV (list format)** | `csv.writer(file).writerow()` | Writes rows as lists |
| **Write CSV (dictionary format)** | `csv.DictWriter(file).writerow()` | Writes rows as dictionaries |
| **Append to CSV** | `open("file.csv", "a")` | Adds rows without overwriting |
| **Custom delimiter** | `csv.reader(file, delimiter=";")` | Use `;` or `\t` instead of `,` |
| **Handling quotes** | `quotechar='"'` | Correctly reads quoted fields |

---

### **2.6.3.5. JSON File Handling**
**Reading JSON Data**
```python
import json

with open("data.json", "r") as file:  # Open JSON file in read mode
    data = json.load(file)  # Load JSON data into a Python dictionary
    print(data)  # Print the parsed JSON data
```

### **Writing JSON Data**
```python
data = {"name": "Alice", "age": 30}  # Define a dictionary

with open("output.json", "w") as file:  # Open file in write mode
    json.dump(data, file, indent=4)  # Convert dictionary to JSON and write4)
# Output
{
    "name": "Alice",
    "age": 30
}
```

---

## 2.6.4. Advanced I/O Techniques
### 2.6.4.1. Redirecting Output
```python
import sys

with open("output.txt", "w") as file:
    sys.stdout = file
    print("This will be written to the file instead of the console.")
```

---

## **2.6.4.2. Handling Large Files Efficiently**
**Reading Large Files Line by Line**
```python
with open("large_file.txt", "r") as file:
    for line in file:
        process(line)  # Process each line one by one
```
**Using `file.readline()` to Read One Line at a Time**
```python
with open("large_file.txt", "r") as file:
    while (line := file.readline()):  # Read one line at a time until EOF
        print(line.strip())  # Remove leading/trailing whitespace and print
```

---

### 2.6.5. Best Practices for Mastering I/O Operations
- **Always close files** or use `with open()` to manage resources.  
- **Use exception handling (`try-except`)** to handle errors in file operations.  
- **Use** `json` for structured data storage and `csv` for tabular data.  
- **Avoid loading large files into memory at once**—read line by line instead.  

---

### 2.6.6. Summary
| Feature | Console I/O | File I/O | CSV | JSON |
|---------|------------|---------|-----|------|
| Input  | `input()` | `file.read()` | `csv.reader()` | `json.load()` |
| Output | `print()` | `file.write()` | `csv.writer()` | `json.dump()` |
| Read Line-by-Line | `input()` | `file.readline()` | o | o |
| Structured Format | x | o | o | o |
