# 8.3. List, Set, and Dict Comprehensions  
Comprehensions provide a concise way to create collections such as **lists, sets, and dictionaries**. They enhance readability and performance by reducing the need for explicit loops.

---

### 8.3.1. List Comprehensions 
A **list comprehension** generates a new list by applying an expression to each item in an iterable.

**Basic Syntax:**
```python
[expression for item in iterable if condition]
```

**Example: Creating a List of Squares**  
```python
numbers = [1, 2, 3, 4, 5]
squares = [x ** 2 for x in numbers]
print(squares)  # Output: [1, 4, 9, 16, 25]
```
- The expression `x ** 2` is applied to each `x` in `numbers`.

**Example: Filtering Even Numbers**  
```python
numbers = [1, 2, 3, 4, 5, 6]
even_numbers = [x for x in numbers if x % 2 == 0]
print(even_numbers)  # Output: [2, 4, 6]
```
- The condition `if x % 2 == 0` filters out odd numbers.

---

### 8.3.2. Set Comprehensions  
A **set comprehension** creates a set using a similar syntax to list comprehensions but with `{}` brackets.

#### **Example: Unique Squares in a Set**  
```python
numbers = [1, 2, 2, 3, 3, 4]
squares = {x ** 2 for x in numbers}
print(squares)  # Output: {16, 1, 4, 9}
```
- The result contains unique squared values.

#### **Example: Filtering Vowels from a String**  
```python
text = "functional programming"
vowels = {char for char in text if char in "aeiou"}
print(vowels)  # Output: {'a', 'o', 'i', 'u', 'e'}
```
- Extracts unique vowels from `text`.

---

### **Dictionary Comprehensions**  
A **dictionary comprehension** allows constructing dictionaries dynamically using `{key: value}` pairs.

#### **Example: Squaring Numbers in a Dictionary**  
```python
numbers = [1, 2, 3, 4, 5]
squares_dict = {x: x ** 2 for x in numbers}
print(squares_dict)  # Output: {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```
- Each number becomes a key, and its square is the corresponding value.

#### **Example: Swapping Keys and Values**  
```python
original = {'a': 1, 'b': 2, 'c': 3}
swapped = {v: k for k, v in original.items()}
print(swapped)  # Output: {1: 'a', 2: 'b', 3: 'c'}
```
- Flips dictionary keys and values.

---

## **Key Takeaways**  
| Type | Syntax | Use Case |
|------|--------|----------|
| **List Comprehension** | `[expression for item in iterable if condition]` | Create and transform lists efficiently. |
| **Set Comprehension** | `{expression for item in iterable if condition}` | Generate unique sets based on conditions. |
| **Dict Comprehension** | `{key: value for item in iterable if condition}` | Construct and modify dictionaries dynamically. |

