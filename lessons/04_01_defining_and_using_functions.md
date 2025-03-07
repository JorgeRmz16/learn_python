# **4.1. Defining and Using Functions**  

A function is a **block of reusable code** that performs a specific task. Functions improve code organization by allowing you to divide a program into smaller, manageable parts.

### Key Benefits of Functions
- **Code Reusability** → Write once, use multiple times.  
- **Modularity** → Break large programs into smaller, manageable pieces.  
- **Readability** → Improve code clarity and structure.  
- **Scalability** → Makes it easier to modify and extend code.  

---

## **4.1.1. Defining a Function**  
Functions in Python are defined using the `def` keyword.

```python
def function_name(parameters):
    """Docstring (optional): Describes the function"""
    # Function body
    return value  # (Optional)
```

**Example:**
```python
def greet():
    """Prints a greeting message"""
    print("Hello, World!")

greet()  # Calling the function
# Output: `Hello, World!`  
```

**Key Takeaways:**  
- Functions must be defined before they are called.  
- `()` is required when calling a function, even if no parameters are passed.  
- A function can have an **optional docstring** to describe its purpose.

---

## 4.1.2. Return Statement  
The `return` statement **sends back** a value from a function.  

```python
def square(x):
    return x * x # Use the reserver word return

result = square(5)
print(result)  # Output: 25
```
**Key Takeaways:**  
- `return` exits the function and passes back a value.  
- Functions without `return` return `None` by default.  

---

## 4.1.3. Nested Functions
Functions **can be defined** inside other functions.

```python
def outer():
    def inner():
        print("Inner function")
    inner()  # Calling the inner function

outer()
# Output: `Inner function`
```

**Key Takeaways:**  
- Nested functions **help encapsulate logic** within another function.  
- Useful for **creating helper functions**.

---

## **Summary**
| Concept | Key Takeaways |
|---------|-------------|
| **Defining Functions** | Use `def` to create a function |
| **Arguments** | Can be positional, default, keyword, `*args`, or `**kwargs` |
| **Return Values** | Use `return` to send data back |
| **Nested Functions** | Functions within functions |

---
