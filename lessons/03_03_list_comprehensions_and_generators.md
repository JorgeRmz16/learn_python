# **3.3. List Comprehensions and Generators in Python**  

List comprehensions and generators are **powerful tools** in Python that allow you to create and manipulate sequences in a **concise, efficient, and readable way**.  

- **List comprehensions** create lists using a **single-line syntax**.  
- **Generators** allow iteration over large datasets **without storing all elements in memory**.  

These techniques improve **performance, readability, and maintainability** of Python code.

---

## **3.3.1. List Comprehensions**  

Is a concise way to create lists from existing iterables like lists, tuples, ranges, or dictionaries.  

### **Basic Syntax**
```python
new_list = [expression for item in iterable if condition]
```
- **expression** - The value to store in the new list.  
- **item** - Each element in the iterable.  
- **iterable** - The data source (list, range, tuple, etc.).  
- **condition (optional)** - Filters which elements to include.  

---

### **3.3.1.1. Creating Lists Using Comprehensions**

```python
# Generating a List of Squares
squares = [x**2 for x in range(10)]
print(squares)
#  Output: `[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]`  
```

```python
# Filtering Even Numbers
evens = [x for x in range(10) if x % 2 == 0]
print(evens)
# Output: `[0, 2, 4, 6, 8]`  
```

```python
# Removing unwanted characters
raw_data = ["  apple ", "banana\t", " cherry\n"]
cleaned_data = [item.strip() for item in raw_data]
print(cleaned_data)  # Output: ['apple', 'banana', 'cherry']
```
```python
# Filtering out empty strings
data = ["hello", "", "world", ""]
filtered_data = [item for item in data if item]
print(filtered_data)  # Output: ['hello', 'world']
```
```python
# Converting strings to uppercase
words = ["apple", "banana", "cherry"]
uppercase_words = [word.upper() for word in words]
print(uppercase_words)  # Output: ['APPLE', 'BANANA', 'CHERRY']
```
```python
# Converting a list of strings to a list of integers
string_numbers = ["1", "2", "3", "4"]
int_numbers = [int(x) for x in string_numbers]
print(int_numbers)  # Output: [1, 2, 3, 4]
```
---

### **3.3.1.2. Nested List Comprehensions**
List comprehensions can be **nested** to handle complex data structures.

```python
# Creating a Multiplication Table
table = [[x * y for x in range(1, 6)] for y in range(1, 6)]
print(table)
""" Output:
[[1, 2, 3, 4, 5],  
 [2, 4, 6, 8, 10],  
 [3, 6, 9, 12, 15],  
 [4, 8, 12, 16, 20],  
 [5, 10, 15, 20, 25]]
 """
```

---

### **3.3.1.3. Dictionary and Set Comprehensions**
Python also supports **dictionary** and **set comprehensions** for concise syntax.

#### **Example: Dictionary Comprehension**
```python
squared_dict = {x: x**2 for x in range(5)}
print(squared_dict)
# Output: `{0: 0, 1: 1, 2: 4, 3: 9, 4: 16}` 
```
 

#### **Example: Set Comprehension**
```python
unique_numbers = {x % 3 for x in range(10)}
print(unique_numbers)
# Output: `{0, 1, 2}` 
```
 
---

## **3.3.2. Generators**
A generator is an iterable that generates values **lazily**, meaning it does not store all elements in memory but **produces them one by one**.

- **Memory efficient** - Ideal for handling large datasets.  
- Uses `yield` instead of `return` - Allows execution to be paused and resumed.  

### **3.3.2.1. Creating a Generator**
A generator function uses **`yield`** instead of `return`.

**Example: Simple Generator Function**
```python
def count_up_to(n):
    count = 0
    while count < n:
        yield count
        count += 1

gen = count_up_to(5)
print(next(gen))  # 0
print(next(gen))  # 1
print(next(gen))  # 2
```

**Key Takeaways:**  
- The function **remembers** its state when `yield` is used.  
- Unlike lists, it does not store values in memory.  

---

### **3.3.2.2. Generator Expressions**
Similar to list comprehensions but using `()` instead of `[]`.

```python
gen_exp = (x**2 for x in range(5))
print(next(gen_exp))  # 0
print(next(gen_exp))  # 1
print(next(gen_exp))  # 4
```
**Key Takeaways:**  
- Saves memory compared to list comprehensions.  
- Ideal for **processing large data** without memory overhead.  

---

## **3.4.3. Comparing List Comprehensions and Generators**
| Feature | List Comprehension | Generator |
|---------|------------------|-----------|
| Syntax | Uses `[]` | Uses `()` |
| Memory Usage | Stores all elements in memory | Generates values lazily |
| Performance | Faster for small data | Better for large datasets |
| Iteration | Returns entire list | Returns one value at a time |
| Use Case | When all elements are needed | When handling large or infinite sequences |

---

# **Summary**
| Concept | Key Features |
|---------|-------------|
| **List Comprehension** | Short syntax for creating lists |
| **Set Comprehension** | Creates a unique set of values |
| **Dictionary Comprehension** | Creates a dictionary dynamically |
| **Generator Function** | Uses `yield` for lazy evaluation |
| **Generator Expression** | Uses `()` instead of `[]` |
