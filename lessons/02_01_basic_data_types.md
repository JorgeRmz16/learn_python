# **2.1. Basic Data Types (`int`, `float`, `str`, `bool`)**  

Python provides several built-in data types to store different kinds of values. The most fundamental ones are:  

1. **Integers (`int`)** → Whole numbers (e.g., `-10`, `0`, `42`)  
2. **Floating-point numbers (`float`)** → Numbers with decimals (e.g., `3.14`, `-2.5`)  
3. **Strings (`str`)** → Text (e.g., `"Hello, World!"`)  
4. **Booleans (`bool`)** → True/False values (`True`, `False`)  

Understanding these types is crucial because Python is **dynamically typed**, meaning it automatically assigns types to variables.  

---

In this lesson we need to known the `type()` function, is used to determine the type of an object:

```python
print(type(10))  # <class 'int'>
print(type(3.14))  # <class 'float'>
print(type("hello"))  # <class 'str'>
print(type([]))  # <class 'list'>
```

---

## **2.1.1. Integer Type (`int`)**  
 
An integer is a whole number, positive or negative, without a decimal point.  

### Creating and Using Integers
```python
x = 10  # Positive integer
y = -5  # Negative integer
z = 0   # Zero

print(type(x))  # Output: <class 'int'>
```

## **2.1.2. Floating-Point Type (`float`)**  

A `float` represents numbers with decimals.  

### Creating and Using Floats
```python
pi = 3.14159
negative_float = -2.5
scientific_notation = 1.2e3  # 1.2 × 10³ = 1200.0

print(type(pi))  # Output: <class 'float'>
```

### Rounding Floats
Use `round()` to control decimal places:  
```python
print(round(3.14159, 2))  # Output: 3.14
```

_round(number, digits)_
- `number`:Required. The number to be rounded
- `digits`:Optional. The number of decimals to use when rounding the number. Default is 0

---

## **2.1.3. String Type (`str`)**  
 
A string is a **sequence of characters** enclosed in single (`'`), double (`"`) or triple quotes (`'''` or `"""`).  

```python
text1 = 'Hello, World!'
text2 = "Python is awesome"
multi_line = """This is 
a multi-line string."""

print(type(name))  # Output: <class 'str'>
```

### String Operations
| Operation | Example | Result | Explanation |
|-----------|---------|--------|-------------|
| Concatenation (`+`) | `"Hello " + "World!"` | `"Hello World!"` | Joins two strings together to form a single string. |
| Repetition (`*`) | `"Hi" * 3` | `"HiHiHi"` | Repeats the string a specified number of times. |
| Indexing (`[]`) | `"Python"[0]` | `'P'` | Retrieves a character at the given index (0-based). |
| Slicing (`[:]`) | `"Python"[1:4]` | `'yth'` | Extracts a substring from the start index (inclusive) to the end index (exclusive). |
| Length (`len()`) | `len("Hello")` | `5` | Returns the number of characters in the string. |

A string is essentially a sequence of characters, like a list of characters. Example:  
```python
text = "Python"
print(text[0])    # 'P'
print(text[-1])   # 'n'
print(text[:3])   # 'Pyt'
print(len(text))  # 6
```

### String Methods
Python provides useful methods for working with strings:  

```python
message = "hello world"
print(message.upper())   # "HELLO WORLD"
print(message.lower()) # "hello world"
print(message.capitalize())  # "Hello world"
print(message.replace("world", "Python"))  # "hello Python"
print(message.split())   # ['hello', 'world']
message = " hello, world "
print(message.strip()) # "hello, world" (delete whitespaces)
print(message.replace("h", "j")) # jello, world!
```

---

## **2.1.4. Boolean Type (`bool`)**   
A boolean represents **True** or **False** values.  

```python
is_python_fun = True
is_sky_green = False

print(type(is_python_fun))  # Output: <class 'bool'>
```

Booleans commonly result from comparisons.  
Example:  
```python
x = 10
y = 5
print(x > y)  # True
print(x == y)  # False
print(bool("")) #False (An empty string is considered False)
print(bool("Python")) #True (A non-empty string is considered True)
```

### **2.1.5. Summary**  

| Feature | Integer (`int`) | Float (`float`) | String (`str`) | Boolean (`bool`) |  
|---------|----------------|----------------|----------------|----------------|  
| Example | `10, -5, 0` | `3.14, -2.5, 1.2e3` | `"hello", 'Python'` | `True, False` |  
| Created With | Direct assignment | Direct assignment | Quotes (`'`, `"`, `''' """`) | `True` / `False` or comparisons |  
| Supports Arithmetic | yes| yes | `+`, `*` | Not |  
| Supports Indexing | Not | Not | Yes | Not |  
| Mutable | Not | Not | Not | Not |  
| Conversion | `int(x)` | `float(x)` | `str(x)` | `bool(x)` |