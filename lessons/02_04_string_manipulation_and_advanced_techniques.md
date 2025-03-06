# **2.. String Manipulation and Advanced Techniques**  

Strings in Python are **immutable** sequences of characters. String manipulation is crucial for handling text-based data efficiently. 

---
## 2.4.1. String Indexing and Slicing
### 2.4.1.1. Indexing (Accessing Individual Characters)
Each character in a string has an **index**:  

| Character | H | e | l | l | o | , |   | W | o | r | l | d | ! |
|-----------|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Index | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
| Negative Index | -13 | -12 | -11 | -10 | -9 | -8 | -7 | -6 | -5 | -4 | -3 | -2 | -1 |

```python
word = "Hello, World!"

print(word[0])   # Output: H
print(word[-1])  # Output: !
print(word[7])   # Output: W
```

---

### 2.4.1.2. Slicing (Extracting Substrings)  
Syntax: `string[start:end:step]`  

```python
text = "PythonProgramming"

print(text[0:6])   # Output: Python
print(text[:6])    # Output: Python (start is 0 by default)
print(text[6:])    # Output: Programming (end is last index by default)
print(text[::2])   # Output: PtoPormig (every second character)
print(text[::-1])  # Output: gnimmargorPnohtyP (reversed string)
```

---

## 2.4.2. String Methods
Python provides **built-in methods** for working with strings.

### 2.4.2.1. Case Conversion
```python
text = "Python is FUN!"

print(text.upper())    # Output: PYTHON IS FUN!
print(text.lower())    # Output: python is fun!
print(text.capitalize())  # Output: Python is fun!
print(text.title())    # Output: Python Is Fun!
print(text.swapcase()) # Output: pYTHON IS fun!
```

---

### **2.4.2.2. String Validation Methods**
Checking string properties:  
```python
s = "Python123"

print(s.isalpha())   # False (contains numbers)
print(s.isdigit())   # False (contains letters)
print(s.isalnum())   # True (only letters & numbers)
print(s.isspace())   # False (no spaces)
print("hello".islower())  # True
print("HELLO".isupper())  # True
```

---

### **2.4.2.3. Finding and Replacing Text**
```python
text = "Python is fun and Python is easy."

print(text.find("fun"))   # Output: 10 (index of first occurrence)
print(text.count("Python"))  # Output: 2 (number of times "Python" appears)
print(text.replace("Python", "JavaScript"))  # Output: JavaScript is fun and JavaScript is easy (Replace all occurrences).
```

---

### **2.4.2.4. Splitting and Joining Strings**
```python
sentence = "Python is great for automation"
words = sentence.split()  # Default separator is space
print(words)  # Output: ['Python', 'is', 'great', 'for', 'automation']

joined_text = "-".join(words)
print(joined_text)  # Output: Python-is-great-for-automation
```

---

### **2.4.2.5. Stripping Whitespace**
```python
text = "  hello world  "
print(text.strip())   # Output: "hello world"
print(text.lstrip())  # Output: "hello world  "
print(text.rstrip())  # Output: "  hello world"
```

---

## 2.4.3. String Formatting
There are multiple ways to format strings.

### 2.4.3.1. Using f-strings
```python
name = "Alice"
age = 25
print(f"My name is {name} and I am {age} years old.")  
# Output: My name is Alice and I am 25 years old.
```

**Expressions inside f-strings**
```python
print(f"The sum of 5 and 3 is {5 + 3}")  # Output: The sum of 5 and 3 is 8
```

**Formatting numbers**
```python
pi = 3.14159
print(f"Pi rounded to 2 decimal places: {pi:.2f}")  
# Output: Pi rounded to 2 decimal places: 3.14
```

---

### 2.4.3.2. Using `.format()` Method
```python
print("Hello, my name is {} and I am {} years old.".format("Alice", 25))
```

**Positional and Keyword Arguments**
```python
print("Hello, {1}! My name is {0}.".format("Alice", "Bob"))
print("Name: {name}, Age: {age}".format(name="Alice", age=25))
```

---

## **2.4.4. Escape Characters**
Escape characters allow inserting **special characters** inside strings.

| Escape Sequence | Description | Example | Output |
|----------------|-------------|---------|--------|
| `\n` | Newline | `"Hello\nWorld"` | Hello <br> World |
| `\t` | Tab | `"Hello\tWorld"` | Hello   World |
| `\\` | Backslash | `"C:\\Users\\Alice"` | C:\Users\Alice |
| `\'` | Single Quote | `'It\'s raining'` | It's raining |
| `\"` | Double Quote | `"She said \"hello\""` | She said "hello" |

---

## **2.4.5. Raw Strings (Avoid Escape Interpretation)**
```python
path = r"C:\Users\Alice\Documents"
print(path)  # Output: C:\Users\Alice\Documents
```

---

## 2.4.6. Advanced String Techniques
### 2.4.6.1. Reversing a String
```python
text = "Python"
reversed_text = text[::-1]
print(reversed_text)  # Output: nohtyP
```

---

### **2.4.6.2. Checking for Palindromes**
```python
def is_palindrome(s):
    s = s.lower().replace(" ", "")  # Convert to lowercase and remove spaces
    return s == s[::-1]

print(is_palindrome("racecar"))  # Output: True
print(is_palindrome("hello"))    # Output: False
```