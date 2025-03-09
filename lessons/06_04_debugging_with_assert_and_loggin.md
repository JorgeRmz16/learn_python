# **6.4. Debugging with `assert` and `logging`**

Debugging is essential for developing robust applications. Python provides **`assert`** for quick checks and **`logging`** for detailed debugging and monitoring.  


## 6.4.1. Using `assert` for Debugging 

`assert` is a **debugging aid** that tests conditions and raises an `AssertionError` if the condition is `False`. It is useful for **early error detection** during development.

### Basic Syntax:
```python
assert condition, "Error message"
```
- If `condition` is `True`, execution continues.  
- If `condition` is `False`, Python raises an `AssertionError`.  

---

### Checking Input Values
```python
def divide(a, b):
    assert b != 0, "Division by zero is not allowed!"
    return a / b

print(divide(10, 2))  # Works fine
print(divide(5, 0))   # Raises AssertionError

""" Output:  
Traceback (most recent call last):
AssertionError: Division by zero is not allowed!
```

### Validating Function Arguments
```python
def set_age(age):
    assert age > 0, "Age must be positive!"
    return f"Age is {age}"

print(set_age(25))  # Works fine
print(set_age(-5))  # Raises AssertionError

""" Output:
AssertionError: Age must be positive!
"""
```

### Checking Data Integrity
```python
numbers = [1, 2, 3, 4, 5]
assert all(isinstance(i, int) for i in numbers), "All elements must be integers!"
```
If an element is not an integer, it raises an error immediately.

---

### Disabling `assert` in Production**
Python **ignores `assert` statements** when running code with optimizations enabled (`python -O script.py`).  
Use `assert` **only for debugging**, not for handling errors in production.

---

## 6.4.2. Using `logging` for Debugging and Monitoring  

### Why Use `logging` Instead of `print`?
- `print()` is temporary and lacks control.  
- `logging` allows **different levels of severity**, writing to files, and tracking timestamps.  

### Basic Syntax
```python
import logging

logging.basicConfig(level=logging.DEBUG)  # Set logging level
logging.debug("This is a debug message")
logging.info("This is an info message")
logging.warning("This is a warning")
logging.error("This is an error")
logging.critical("This is critical")

""" Output:
WARNING:root:This is a warning
ERROR:root:This is an error
CRITICAL:root:This is critical
"""
```
Messages with levels **lower than `WARNING` (like `DEBUG` and `INFO`) are not shown by default.**

---

### Setting Up Logging Configuration
```python
logging.basicConfig(
    filename="app.log",  # Log to a file
    level=logging.DEBUG,  # Capture all messages
    format="%(asctime)s - %(levelname)s - %(message)s"  # Customize log format
)
```
Now, all logs are stored in `app.log` instead of just printing to the console.

---

### Logging in a Function
```python
def divide(a, b):
    try:
        result = a / b
        logging.info(f"Successfully divided {a} by {b}. Result: {result}")
        return result
    except ZeroDivisionError:
        logging.error("Attempted to divide by zero!", exc_info=True)

divide(10, 2)
divide(5, 0)  # Logs an error

""" Output in `app.log`:
2025-03-07 12:00:00 - INFO - Successfully divided 10 by 2. Result: 5.0
2025-03-07 12:00:05 - ERROR - Attempted to divide by zero!
"""
```

---

### Logging Levels and Their Uses
| **Level**        | **Usage** |
|------------------|----------|
| `DEBUG`         | Detailed debugging information |
| `INFO`          | General events (e.g., function executed successfully) |
| `WARNING`       | Something unexpected, but the program still runs |
| `ERROR`         | A problem that prevents normal execution |
| `CRITICAL`      | A severe error that may require shutting down |

---

### Combining `assert` and `logging`
```python
import logging

logging.basicConfig(level=logging.DEBUG)

def process_value(value):
    assert isinstance(value, int), "Value must be an integer!"
    logging.info(f"Processing value: {value}")
    return value * 2

try:
    print(process_value(10))  # Works fine
    print(process_value("abc"))  # Raises AssertionError
except AssertionError as e:   
    logging.error(f"Assertion failed: {e}")

""" Output:
INFO:root:Processing value: 10
ERROR:root:Assertion failed: Value must be an integer!
"""
```

---

# **Key Takeaways**
- **Use `assert`** for quick checks during development.  
- **Use `logging`** for detailed debugging, tracking, and monitoring.  
- **Disable `assert` in production** (`python -O`).  
- **Log errors instead of printing them** for better debugging.  
