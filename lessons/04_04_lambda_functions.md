# **4.4. Lambda Functions in Python** 🚀  

A **lambda function** is a **small, anonymous function** that can have any number of arguments but only one expression.  

**Syntax:**
```python
lambda arguments: expression, reverse=True
```
- **`lambda`** is the keyword.  
- **`arguments`** are input values (like function parameters).  
- **`expression`** is the computation performed (returns a value).  

```python
square = lambda x: x ** 2
print(square(5))  # Output: 25
```
**Equivalent to a normal function:**
```python
def square(x):
    return x ** 2
```
Lambda functions **remove the need** for `def` and `return`, making them concise.  

---

## 4.4.1. Why Use Lambda Functions? 
- **Concise and Readable**: Reduces code verbosity.  
- **Useful in Higher-Order Functions**: Works well with `map()`, `filter()`, and `sorted()`.  
- **No Need for Function Names**: Great for quick, one-time use functions.  

**Limitations:**  
- Can only contain a **single expression** (no multiple statements).  
- Harder to debug and read if too complex.  

---

## 4.4.2. Using Lambda Functions with Higher-Order Functions  
Lambda functions are **commonly used** with functions like `map()`, `filter()`, and `sorted()`.

### `map()` – Applying a Function to an Iterable  
The `map()` function **applies** a function to each item in an iterable (like a list).  
*filter(function, iterable)*
```python
numbers = [1, 2, 3, 4, 5]

squared = list(map(lambda x: x ** 2, numbers)) # Lambda
# Equivalent to:
squared = [x ** 2 for x in numbers]  # List comprehension

print(squared)  # Output: [1, 4, 9, 16, 25]
```

---

### `filter()` – Selecting Items That Meet a Condition 
The `filter()` function **keeps elements** that return `True` for a given condition.  
*filter(function, iterable)*
```python
numbers = [1, 2, 3, 4, 5, 6]

evens = list(filter(lambda x: x % 2 == 0, numbers))
# **Equivalent to:**
evens = [x for x in numbers if x % 2 == 0]

print(evens)  # Output: [2, 4, 6]
```

---

### **`sorted()` – Custom Sorting with `lambda`**  
The `sorted()` function can use **lambda expressions** for custom sorting.  
*sorted(iterable, key=key, reverse=reverse)*
```python
students = [("Alice", 25), ("Bob", 20), ("Charlie", 23)]
students_sorted = sorted(students, key=lambda student: student[1])  # Sort by age
print(students_sorted)  # Output: [('Bob', 20), ('Charlie', 23), ('Alice', 25)]
```
- **lambda student: student[1]** extracts the second element from each tuple.
```python
students = [
    {"name": "Alice", "age": 25},
    {"name": "Bob", "age": 20},
    {"name": "Charlie", "age": 23}
]
# Sort by age (ascending order)
students_sorted = sorted(students, key=lambda student: student["age"])
# Sort by name alphabetically
students_sorted = sorted(students, key=lambda student: student["name"])

print(students_sorted)
```
**Sorting a List of Single-Key Dictionaries**
```python
data = [
    {"Alice": 25},
    {"Bob": 20},
    {"Charlie": 23}
]

# Sorting by values (ages)
data_sorted = sorted(data, key=lambda d: list(d.values())[0])

print(data_sorted)
```
**list(d.values())[0]** extracts the first (and only) value from each dictionary.

---

## **4.4.3. Using Lambda Functions Inside Another Function**  
Lambda functions can be **defined inside another function** to create dynamic behavior.

```python
def multiplier(n):
    return lambda x: x * n

double = multiplier(2)
print(double(5))  # Output: 10
```
- **`multiplier(2)` returns a lambda function** that multiplies by 2.  
- **Equivalent to:**
```python
def double(x):
    return x * 2
```

---

## **4.4.4. Lambda vs Regular Functions: When to Use Each?**  
| Feature | Lambda Functions | Regular Functions |
|---------|-----------------|------------------|
| **Use case** | Small, one-liner functions | Complex logic, multiple statements |
| **Readability** | Less readable if complex | More readable |
| **Reusability** | Not reusable (anonymous) | Reusable (named) |
| **Performance** | Slightly faster for simple expressions | Best for complex logic |

### Use `lambda` when:  
- You need **quick, simple, one-line functions**.  
- You're using **higher-order functions** like `map()` and `filter()`.  

### Use `def` when:  
- You need a function with **multiple lines** or complex logic.  
- You want to **reuse the function multiple times**.

---

## **4.4.6. Best Practices for Lambda Functions**

✔ **Use lambda for short functions** (avoid making them too complex).  
✔ **Avoid using lambda for nested logic** (use regular `def` functions instead).  
✔ **Use meaningful variable names** to improve readability.  
✔ **Prefer list comprehensions** for simple `map()` and `filter()` use cases.  

---

## **Summary**
| Concept | Explanation |
|---------|-------------|
| **Lambda Function** | Anonymous, one-line function using `lambda` keyword. |
| **Syntax** | `lambda arguments: expression`, reverse=True |
| **Use Cases** | Works well with `map()`, `filter()`, `sorted()`, and inside functions. |
| **Limitations** | Single expression only (no multi-line logic). |
| **Alternatives** | Use `def` for complex functions. |

---
