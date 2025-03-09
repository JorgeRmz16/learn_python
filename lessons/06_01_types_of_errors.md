# **6.1 Types of Errors in Python** 

Errors in Python can be broadly categorized into **syntax errors** and **runtime errors**.  


## 6.1.1.Syntax Errors (Parsing Errors)   

- These occur when Python **cannot understand** your code due to incorrect syntax.  
- **Detected** before the program runs (during parsing).  
- **Example**:  
```python
print("Hello World"  # Missing closing parenthesis

# Error Message:
# SyntaxError: unexpected EOF while parsing
```
**Common Causes**:  
- **Missing colons** (`:`) in loops, functions, or conditionals.  
- **Mismatched parentheses**, brackets, or quotes.  
- **Incorrect indentation** (Python enforces indentation strictly).  

**How to Fix?**  
- Read the error message carefully—it **points to the problematic line**.  
- Check for missing or misplaced symbols.  

---

## 6.1.2. Name Errors (Undefined Variables)  

- Occurs when trying to use a variable or function that **hasn’t been defined**.   
```python
print(my_variable)  # my_variable is not defined
# Error Message**:
# NameError: name 'my_variable' is not defined
```
**Common Causes**:  
- Misspelled variable or function names.  
- Using a variable before assigning it a value.  
- Referencing an undefined function.  

**How to Fix?**  
- **Check spelling** and ensure variables/functions exist before use.  
- **Define variables** before accessing them.  

---

## 6.1.3 Type Errors (Incompatible Operations)  

- Occurs when an operation is performed on an **incompatible data type**.  

```python
print(5 + "hello")  # Cannot add int and str

# Error Message**:
# TypeError: unsupported operand type(s) for +: 'int' and 'str'
```
**Common Causes**:  
- Mixing strings and numbers without conversion.  
- Calling functions with incorrect argument types.  
- Using mutable objects where immutable ones are required.  

**How to Fix?**  
- Use **explicit type conversions** (`str()`, `int()`, `float()`).  
- **Check function arguments** before passing them.  

---

## 6.1.4. Index Errors (Out of Range Access)   

- Trying to access an **invalid index** in a list, tuple, or string.  
  
```python
numbers = [1, 2, 3]
print(numbers[5])  # Index out of range

# Error Message**:
# IndexError: list index out of range
```
**Common Causes**:  
- **Accessing indices beyond the length** of a list or string.  
- Forgetting that **Python indexing starts at `0`**.  

**How to Fix?**  
- Use `len()` to check the valid range.  
- Use `try-except` to catch the error gracefully.  

---

## 6.1.5. Key Errors (Invalid Dictionary Keys)   

Occurs when trying to access a **nonexistent key** in a dictionary.  
 
```python
data = {"name": "Alice"}
print(data["age"])  # 'age' key does not exist

# Error Message**:
# KeyError: 'age'
```
**Common Causes**:  
- Misspelled or missing dictionary keys.  
- Expecting a key to exist when it doesn’t.  

**How to Fix?**  
- Use `.get()` to avoid crashes:  
```python
print(data.get("age", "Key not found"))  # Returns 'Key not found'
```
- Check for key existence before accessing it:  
```python
if "age" in data:
    print(data["age"])
```

---

## 6.1.6. Attribute Errors (Nonexistent Attributes)   

Trying to access an attribute that doesn’t exist in an object.  
 
```python
class Car:
    def __init__(self, brand):
        self.brand = brand

my_car = Car("Toyota")
print(my_car.color)  # 'color' attribute does not exist

# Error Message
# AttributeError: 'Car' object has no attribute 'color'
```
**Common Causes**:  
- Misspelled attribute names.  
- Using attributes that **haven’t been defined**.  

**How to Fix?**  
- Ensure the attribute exists before accessing it.  
- Use `hasattr(object, "attribute")` to check:  
```python
if hasattr(my_car, "color"):
    print(my_car.color)
else:
    print("Attribute not found")
```

---

## 6.1.7. Value Errors (Wrong Values for Functions)   

The function **expects a different kind of value** than provided.  
 
```python
int("hello")  # Cannot convert a string to an integer

# Error Message
# ValueError: invalid literal for int() with base 10: 'hello'
```
**Common Causes**:  
- Providing incorrect values to functions.  
- Attempting to convert incompatible data types.  

**How to Fix?**  
- Validate input **before conversion**:  
```python
if "hello".isdigit():
    print(int("hello"))  # Won't execute
else:
    print("Invalid number")
```

---

## 6.1.8. Import Errors (Missing or Incorrect Modules)  

 Occurs when **Python cannot find a module**. 

```python
import nonexistent_module  # This module does not exist

# Error Message
# ModuleNotFoundError: No module named 'nonexistent_module'
```
**Common Causes**:  
- Misspelled module names.  
- Module not installed.  

**How to Fix?**  
- **Check if the module is installed**:  
```bash
pip install module_name
```
- **Verify spelling and case sensitivity**.  

---

## ZeroDivisionError (Division by Zero)   

Trying to divide a number by zero.  

```python
print(10 / 0)  # Division by zero

 # Error Message**:
# ZeroDivisionError: division by zero
```
**Common Causes**:  
- Performing division **without checking if the denominator is zero**.  

**How to Fix?**  
- Check denominator **before dividing**:  
```python
def safe_divide(a, b):
    return a / b if b != 0 else "Cannot divide by zero"

print(safe_divide(10, 0))  # Output: Cannot divide by zero
```

---

# Key Takeaways
- **Syntax errors** occur before execution; **runtime errors** occur during execution.  
- Common **runtime errors** include `NameError`, `TypeError`, `IndexError`, `KeyError`, `AttributeError`, and `ZeroDivisionError`.  
- Always **read the full error message**—it provides valuable debugging clues.  
- Use `try-except` to **gracefully handle errors** (covered in **6.2**).  

---
