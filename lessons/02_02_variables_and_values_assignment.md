# **2.2. Variables and Value Assignment**  
  
A **variable** in Python is a name that refers to a value stored in memory. Think of it as a **label** for data.  

### **Key Characteristics of Variables in Python**  
- **Dynamically typed** → No need to declare a variable type explicitly.  
- **Can change types** → A variable can hold different types of values over time.  
- **Stores values in memory** → References an object in memory, not a fixed location.  
- **Case-sensitive** → `myVar` and `myvar` are different variables.  

Example:  
```python
x = 10  # Assigns integer 10 to x
name = "Alice"  # Assigns a string to name
pi = 3.14159  # Assigns a float to pi
is_active = True  # Assigns a boolean to is_active
```

---

## 2.2.1 Variable Naming Rules
When naming variables, follow these rules:  

**Allowed:**  
- Letters (`a-z`, `A-Z`)  
- Digits (`0-9`)  
- Underscores (`_`)  

**Not Allowed:**  
- Cannot start with a number (`1var`)  
- Cannot contain spaces (`my var`)  
- Cannot use special characters (`@, $, %`)  
- Cannot be a **reserved keyword** ([Documentation](https://docs.python.org/2.5/ref/keywords.html))  

Example:  
```python
valid_name = "Python"  # Good
_invalid_name = "Oops"  # (Technically allowed, but underscores are for special cases)
2cool = "Nope"  # Error: Cannot start with a number
def = "Hello"  # Error: 'def' is a reserved keyword
```

---

## **2.2.2. Best Practices for Variable Naming (PEP 8)**  
Following **PEP 8** (Python's style guide) ensures readable and maintainable code.  

**Use descriptive names**  
```python
x = 10  # Bad (not descriptive)
age = 25  # Good
user_score = 100  # Good
```

**Use `snake_case` (lowercase with underscores)**  
```python
total_price = 50.75  # Good
totalPrice = 50.75  # Not recommended (CamelCase is for classes)
```

**Constants in uppercase** 

Unlike other languages, Python does not have built-in constant support, but by convention, constants are defined using uppercase variable names.
```python
PI = 3.14159  # Good
```

**Avoid using single-letter names (except for loop variables)**  
```python
a = 10  # Bad (not meaningful)
customer_age = 10  # Good
```

---

## **2.2.3. Assigning Values to Variables**  
Python allows several types of value assignments:  

### 2.2.3.1. Simple Assignment  
```python
name = "Alice"
age = 25
height = 5.9
```

### 2.2.3.2. Multiple Assignments  
You can assign multiple variables at once:  
```python
x, y, z = 1, 2, 3
print(x, y, z)  # Output: 1 2 3
```

### 2.2.3.3. Assigning the Same Value to Multiple Variables  
```python
a = b = c = 42
print(a, b, c)  # Output: 42 42 42
```

### 2.2.3.4. Swapping Values (Pythonic Way)  
```python
a, b = 10, 20
a, b = b, a  # Swap values
print(a, b)  # Output: 20 10
```

---

## **2.2.4. Data Type Identification**  
Use `type()` to check a variable's type:  
```python
x = 100
print(type(x))  # Output: <class 'int'>

y = 3.14
print(type(y))  # Output: <class 'float'>

z = "Hello"
print(type(z))  # Output: <class 'str'>
```

---

## **2.2.5. Changing Variable Types (Type Casting)**  
You can **convert** (cast) a variable to a different type using built-in functions:  

| Function | Converts to |
|----------|------------|
| `int()`  | Integer |
| `float()`| Floating-point |
| `str()`  | String |
| `bool()` | Boolean |

Example:  
```python
x = "100"
y = int(x)  # Convert string to integer
print(type(y))  # Output: <class 'int'>

pi = 3.14
pi_str = str(pi)  # Convert float to string
print(type(pi_str))  # Output: <class 'str'>
```
