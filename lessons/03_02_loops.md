# **3.2. Loops Python (`for`, `while`)**  

Loops are a fundamental concept in programming that allow us to execute a block of code multiple times. Python provides two main loop types:  
- **`for` loops** – iterate over a sequence (list, tuple, dictionary, string, etc.).  
- **`while` loops** – execute as long as a condition remains `True`.  

---

## **3.2.1. The `for` Loop**
A `for` loop iterates over a sequence, executing a block of code for each item.  

**Basic Syntax**
```python
for variable in sequence:
    # Code block (executed for each item)
```

**Example 1: Iterating Over a List**
```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```
**Key Takeaways:**  
- The loop variable (`fruit`) takes each value from `fruits` in order.  
- The loop executes **once per item**.  

**Example 2: Using `range()`**  
*range(start, stop, step)*  - generates a sequence of numbers.

```python
for i in range(5):  # Default start is 0
    print(i)
# Output: `0 1 2 3 4` 
```
 

```python
for i in range(1, 10, 2):  # Start=1, Stop=10 (exclusive), Step=2
    print(i)
# Output: `1 3 5 7 9`
```
**Key Takeaways:**  
- `range(n)` generates numbers **from 0 to n-1**.  
- `range(start, stop, step)` customizes the sequence.  

---

## **3.2.2. The `while` Loop**
A `while` loop executes as long as a condition remains **`True`**.

**Basic Syntax**
```python
while condition:
    # Code block
```
**Example 1: Counting Down**
```python
count = 5
while count > 0:
    print(count)
    count -= 
# Output: `5 4 3 2 1`
```

**Example 2: User Input Validation**
```python
password = ""
while password != "Python123":
    password = input("Enter password: ")
print("Access Granted!")
```
**Key Takeaways:**  
- Be careful to modify the condition inside the loop to **avoid infinite loops**.  
- `while` loops are useful when **the number of iterations is unknown**.  

---

## **3.2.3. Loop Control Statements**
Python provides special keywords to **control** loop execution.

### **`break` (Exit the Loop)**  
Stops the loop **immediately**.

```python
for num in range(10):
    if num == 5:
        break
    print(num)
# Output: `0 1 2 3 4` (loop stops at 5).
```

### **`continue` (Skip an Iteration)**
Skips the **current iteration** and continues to the next one.

```python
for num in range(5):
    if num == 2:
        continue
    print(num)
# Output: `0 1 3 4` (skips 2).
```

### **`else` in Loops**
Runs **only if the loop completes normally** (without `break`).

```python
for num in range(5):
    print(num)
else:
    print("Loop completed successfully!")
# Output: `0 1 2 3 4 Loop completed successfully!`
```

```python
for num in range(5):
    if num == 2:
        break
    print(num)
else:
    print("Loop completed successfully!")  # This won’t execute
# Output: `0 1` (no `"Loop completed successfully!"` since `break` was used).
```

---

## **3.2.4. Nested Loops**
A loop inside another loop.

**Example 1: Multiplication Table**
```python
for i in range(1, 4):
    for j in range(1, 4):
        print(f"{i} x {j} = {i * j}")
```
**When to Use Nested Loops?**  
- Working with grids, matrices, tables. 
- Handling combinations of values.   

**Avoid unnecessary nesting** to improve performance.

---

## **3.2.5. Iterating Over Different Data Structures**
**1. Iterating Over a String**
```python
for char in "Python":
    print(char)
"""Output: 
P
y
t
h
o
n
"""
```

**2. Iterating Over a Dictionary**
```python
person = {"name": "Alice", "age": 25, "city": "New York"}
for key, value in person.items():
    print(f"{key}: {value}")
"""Output:
name: Alice
age: 25
city: New York
"""
```

**3. Iterating Over a List with `enumerate()`**
```python
fruits = ["apple", "banana", "cherry"]
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")
"""Output:
0: apple
1: banana
2: cherry
"""
```
-  The `enumerate()` function takes an iterable as input and returns an enumerate object. This object generates pairs of (index, value) for each element in the iterable.



---

## **3.2.6. Optimizations & Best Practices**
**Use `for` loops** when iterating over sequences (`list, tuple, dict, string`).  
**Use `while` loops** when the number of iterations is unknown.  
**Avoid infinite loops** (`while True:` must have a `break`).  
**Use `break*`** to exit loops early when necessary.  
**Use `continue`** to skip unnecessary iterations.  
**Use list comprehensions** for concise looping. 

---

## **3.2.8. Summary Table**
| Feature | `for` Loop | `while` Loop |
|---------|-----------|-------------|
| **Use Case** | When iterating over a sequence | When a condition controls execution |
| **Example** | `for x in range(5):` | `while x < 5:` |
| **Break Condition** | Runs for a known number of iterations | Runs until a condition becomes `False` |
| **Best For** | Lists, dictionaries, strings, ranges | User input validation, waiting for an event |
