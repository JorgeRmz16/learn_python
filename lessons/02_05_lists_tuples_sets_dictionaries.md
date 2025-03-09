# **2.5. Lists, Tuples, Sets, and Dictionaries**  

Python provides four powerful built-in collection types:  
- **Lists**: Ordered, mutable collections.  
- **Tuples**: Ordered, immutable collections.  
- **Sets**: Unordered collections with unique elements.  
- **Dictionaries**: Key-value mappings.  

These structures is essential for efficient data handling in Python. Let’s dive deep!  

---

## 2.5.1. Lists (Ordered, Mutable)
A **list** is an ordered collection that can store multiple data types and allows modification.

### Creating Lists
```python
# Empty list
empty_list = []

# List with elements
numbers = [1, 2, 3, 4, 5]
mixed = [10, "Python", True, 3.14]

# Nested lists
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

---

### 2.5.1.1. Accessing Elements (Indexing & Slicing)
```python
fruits = ["apple", "banana", "cherry", "date"]

print(fruits[0])    # Output: apple
print(fruits[-1])   # Output: date
print(fruits[1:3])  # Output: ['banana', 'cherry']
print(fruits[::-1]) # Reverse the list
```

---

### 2.5.1.2. Modifying Lists
```python
fruits[1] = "blueberry"
print(fruits)  # Output: ['apple', 'blueberry', 'cherry', 'date']
```

 **Adding elements**
```python
fruits.append("elderberry")  # Adds at the end
fruits.insert(2, "kiwi")     # Inserts at index 2
```

 **Removing elements**
```python
fruits.remove("banana")  # Removes first occurrence
last = fruits.pop()      # Removes last element and returns it
del fruits[1]           # Removes element at index 1
```

---

### 2.5.1.3. List Operations
```python
numbers = [1, 2, 3] + [4, 5]  # Concatenation
print(numbers * 2)  # Output: [1, 2, 3, 4, 5, 1, 2, 3, 4, 5]

# Checking membership
print("apple" in fruits)  # Output: True
```

---

### 2.5.1.4. List Methods
```python
nums = [3, 1, 4, 1, 5]
nums.sort()    # Sorts list in ascending order
nums.reverse() # Reverses the list
```

---

### 2.5.1.5. List Comprehensions (Advanced)
[expression **for** item **in** iterable **if** condition]
- **expression**: Is the value that will be included in the new list. It can be any valid Python expression.
- **item**: This is a variable representing each element in the iterable.
- **iterable**: This is the sequence (list, tuple, range, string, etc.) you're iterating over.
- **if condition (optional)**: This is a filter that determines whether an item should be included in the new list.
```python
even_numbers = [x for x in range(20) if x % 2 == 0]
print(even_numbers)  # Output: [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

squares = [x**2 for x in range(10)]
print(squares)  # Output: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

words = ["apple", "banana", "cherry"]
uppercase_words = [word.upper() for word in words]
print(uppercase_words)  # Output: ['APPLE', 'BANANA', 'CHERRY']

numbers = [1, 2, 3, 4, 5]
result = ["even" if x % 2 == 0 else "odd" for x in numbers]
print(result) #output: ['odd', 'even', 'odd', 'even', 'odd']
```

---

## 2.5.2. Tuples (Ordered, Immutable)
A **tuple** is like a list, but immutable (not changing, or unable to be changed).

### 2.5.2.1. Creating Tuples
```python
my_tuple = (1, 2, 3)
single_element = (5,)  # Comma is required for a single-element tuple
```

---

### 2.5.2.2. Accessing and Slicing Tuples
```python
print(my_tuple[0])   # Output: 1
print(my_tuple[-1])  # Output: 3
print(my_tuple[1:3]) # Output: (2, 3)
```

**Unpacking tuples**
```python
a, b, c = my_tuple
print(a, b, c)  # Output: 1 2 3
```

---

### 2.5.2.3. Tuple Methods
```python
print(my_tuple.count(2))  # Output: 1 (eturns the number of times a specified value occurs)
print(my_tuple.index(3))  # Output: 2 (returns the index of the first occurrence of the specified valuev)
```

**Use cases of tuples:**  
- Faster than lists  
- Can be dictionary keys  
- Used in function returns  

---

## 2.5.3. Sets (Unordered, Unique Elements)
A **set** is an unordered collection that does not allow duplicate values (sets do not maintain any specific order of their elements. This means you cannot access elements by index.).

### 2.5.3.1. Creating Sets
```python
my_set = {1, 2, 3, 4, 5}
empty_set = set()  # Empty set
```

**Duplicate removal**
```python
unique_nums = {1, 2, 2, 3, 4, 4}
print(unique_nums)  # Output: {1, 2, 3, 4}
```

---

### 2.5.3.2. Set Operations
```python
A = {1, 2, 3}
B = {3, 4, 5}

print(A | B)  # Union → {1, 2, 3, 4, 5}
print(A & B)  # Intersection → {3}
print(A - B)  # Difference → {1, 2}
print(A ^ B)  # Symmetric Difference → {1, 2, 4, 5}
```

---

### 2.5.3.3. Set Methods
```python
my_set.add(6)     # Add an element
my_set.remove(3)  # Remove an element (error if missing)
my_set.discard(10) # Removes safely (no error if missing)
```

**Why use sets?**  
- Fast lookups  
- Removing duplicates  
- Set operations (union, intersection, etc.)  

---

## 2.5.4. Dictionaries (Key-Value Pairs)
A **dictionary** stores data in key-value pairs.

### **2.5.4.1. Creating Dictionaries**
```python
person = {"name": "Alice", "age": 25, "city": "New York"}
empty_dict = {}  # Empty dictionary
constructor_dict = dict(name = "John", age = 36, country = "Norway")
```

---

### **2.5.4.2. Accessing and Modifying Data**
```python
print(person["name"])  # Output: Alice

person["age"] = 26  # Update value
person["job"] = "Engineer"  # Add new key-value pair
```

**Access safely using `.get()`**
```python
print(person.get("country", "Unknown"))  # Output: Unknown (expcted, if_not)
```

---

### 2.5.4.3. Dictionary Methods
```python
print(person.keys())   # Get all keys
print(person.values()) # Get all values
print(person.items())  # Get all key-value pairs
```

**Iterating through a dictionary**
```python
for key, value in person.items():
    print(f"{key}: {value}")
```

---

### **2.5.4.4. Removing Elements**
```python
person.pop("age")    # Remove key and return value
del person["city"]   # Remove key
person.clear()       # Empty the dictionary
```

---

## 2.5.5. Best Practices for Collections
- Use lists for ordered, modifiable data
- Use tuples when immutability is required
- Use sets for uniqueness and fast lookups
- Use dictionaries for key-value relationships

---

## 2.5.6. Summary Table
| Feature | List | Tuple | Set | Dictionary |
|---------|------|-------|-----|------------|
| Ordered | o | o | x | o |
| Mutable | o | x | o | o |
| Allows Duplicates | o | o | x | Keys: x, Values: o |
| Indexing | o | o | x | Keys instead of index |

---

## 2.5.7. Advanced Techniques

**List of dictionaries**
```python
people = [{"name": "Alice", "age": 25}, {"name": "Bob", "age": 30}]
print(people[0]["name"])  # Output: Alice
```

**Dictionary with default values**
```python
from collections import defaultdict
inventory = defaultdict(int)
inventory["apple"] += 1
print(inventory)  # Output: {'apple': 1}
```

**Sorted a List of dictionaries**
```python
data = [
    {"temperature": 12},
    {"temperature": 18},
    {"temperature": 25},
    {"temperature": 22},
    {"temperature": 15},
]
sorted_data = sorted(data, key=lambda x: x["temperature"])

```

## 2.5.8 Summary

| Feature         | List []          | Tuple ()         | Set {}           | Dictionary {}      |
|----------------|---------------|---------------|---------------|-----------------|
| **Ordered**    | Yes         | Yes        | No        | Yes (keys)  |
| **Mutable**    | Yes         | No        | Yes        | Yes         |
| **Allows Duplicates** | Yes | Yes        | No        | Keys: No, Values: Yes |
| **Indexing & Slicing** | Yes | Yes       | No        | No (Keys instead) |
| **Use Case**   | Dynamic collections | Fixed data | Unique values | Key-value mapping |
| **Common Methods** | `append()`, `insert()`, `remove()`, `sort()` | `count()`, `index()` | `add()`, `remove()`, `union()` | `keys()`, `values()`, `items()` |

**List Comprehencions** -> [expression for item in iterable if condition]