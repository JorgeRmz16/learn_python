# **4.5. Decorators and Higher-Order Functions**  

**Decorators and Higher-Order Functions** are **advanced concepts** in Python that allow modifying functions dynamically and writing cleaner, reusable, and efficient code. 

---

## 4.5.1. Higher-Order Functions  
Is a function that **takes another function as an argument or returns a function**.

**Passing a Function as an Argument**
```python
def apply_twice(func, value):
    return func(func(value))

def square(x):
    return x ** 2

print(apply_twice(square, 2))  # Output: 16 (2² = 4, then 4² = 16)
```
- `apply_twice()` **accepts** a function (`func`) as an argument.  
- The function is **executed twice**, applying it to the `value`.  


**Returning a Function**
```python
def multiplier(n):
    def multiply(x):
        return x * n
    return multiply  # Returns a function

double = multiplier(2)  # Now double(x) = x * 2
print(double(5))  # Output: 10
print(type(double)) # <class 'function'>
```
- **`multiplier(2)` returns a function** that multiplies by 2.  
- **Closure:** `multiply()` remembers `n` even after `multiplier()` has finished executing.

---

## 4.5.2. Decorators  
Is a function that **modifies another function without changing its code**.  
- **Used for:** Logging, authentication, performance measurement, access control, etc.  
- **Implemented using** `@decorator_name` syntax.  

---

### 4.5.2.1. Creating and Using a Simple Decorator  


```python
def my_decorator(func):
    """
    It takes another function as input and returns a modified version of it.
    """
    def wrapper():
        """
        It adds extra functionality before and after the original function is called.
        """
        print("Before function execution")
        func()  # Call the original function that was passed in.
        print("After function execution") 
    return wrapper  # Return the wrapper function, which now replaces the original function.

@my_decorator
def say_hello():
    print("Hello, World!")
    
say_hello()
suma(5, 2)

"""Output
Before function execution  
Hello, World!  
After function execution  
"""
```
 **How It Works:**  
- `@my_decorator` **wraps** `say_hello()` inside `wrapper()`.  
- `wrapper()` executes extra logic **before and after** calling `say_hello()`. 

---

### **4.5.2.2. Decorators with Arguments**  
To make decorators **flexible**, they should accept **arbitrary arguments**.

```python
def my_decorator(func):
    def wrapper(*args, **kwargs):
        print("Before function execution")
        result = func(*args, **kwargs)  # Call the original function with params
        print("After function execution")
        return result  # Return the function's result (if any)
    return wrapper  # Return the modified function

@my_decorator
def one_param_function(x):
    print(f"One number: {x}")

@my_decorator
def two_params_function(x, y):
    print(f"Two numbers: {x}, {y}")

one_param_function(10)
two_params_function(20, 30)

""" 
Expected Output:
Before function execution  
One number: 10  
After function execution  
Before function execution  
Two numbers: 20, 30  
After function execution  
"""
 
"""
```
```python
def repeat(n): # Define a decorator that repeats function execution 'n' times
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(n):
                func(*args, **kwargs)  # Execute the decorated function
        return wrapper  # Return the modified function
    return decorator  # Return the decorator function

# Apply the decorator to repeat function execution 3 times
@repeat(3)
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")

"""
Expected Output:
Hello, Alice!  
Hello, Alice!  
Hello, Alice!  
"""
 
"""
```

---

### 4.5.2.3. Using `functools.wraps` to Preserve Function Metadata 
Using a decorator **changes the original function’s metadata**.  
To **preserve metadata**, use `functools.wraps()`.

```python
import functools  # Import functools module for function utilities

# Define a decorator function
def my_decorator(func):
    @functools.wraps(func)  # Preserve original function metadata
    def wrapper(*args, **kwargs):
        print("Executing function...")
        return func(*args, **kwargs)  # Call the original function and return the result
    return wrapper  # Return the modified function

@my_decorator
def add(a, b):
    return a + b

# Print function metadata
print(add.__name__)  # Output: add (preserved by functools.wraps)
print(add.__doc__)   # Output: "Returns the sum of a and b."
```

---

**Explanation of Metadata (`functools.wraps`)**
- In Python, **function metadata** includes attributes like:  

| Attribute         | Description |
|------------------|-------------|
| `__name__`       | Name of the function (`add`, `wrapper`, etc.). |
| `__doc__`        | Docstring of the function. |
| `__module__`     | The module where the function is defined. |
| `__annotations__` | Type hints (if specified). |
| `__dict__`       | A dictionary of function attributes (if modified). |
| `__defaults__`   | Default values for function arguments. |
| `__code__`       | The compiled code object for the function. |
| `__globals__`    | Global variables accessible in the function. |
| `__closure__`    | Closure variables used in a nested function. |

**What Happens Without `functools.wraps`?**
- If we **don't use `functools.wraps(func)`**, the `wrapper` function replaces `func`, meaning:
  - `add.__name__` would return `"wrapper"` instead of `"add"`.
  - `add.__doc__` would be `None` instead of the original docstring.
- `functools.wraps(func)` ensures that the **original function's metadata is preserved**.


---

**Example: Using Function Metadata**
```python
def example(x: int, y: int = 10) -> int:
    """Returns x multiplied by y."""
    return x * y

print(example.__name__)         # Output: example
print(example.__doc__)          # Output: Returns x multiplied by y.
print(example.__annotations__)  # Output: {'x': <class 'int'>, 'y': <class 'int'>, 'return': <class 'int'>}
print(example.__defaults__)     # Output: (10,)
```

---

## 4.5.3. Common Built-in Decorators
Python provides several **built-in decorators** to enhance functions.

### `@staticmethod` – Defining Static Methods in Classes  
Static methods **don’t access class attributes** and behave like regular functions inside classes.

```python
class Math:
    @staticmethod
    def add(a, b):
        return a + b

print(Math.add(2, 3))  # Output: 5
```

---

### `@classmethod` – Defining Class Methods  
Class methods **operate on the class itself** instead of instance attributes.

```python
class Person:
    count = 0

    def __init__(self, name):
        self.name = name
        Person.count += 1

    @classmethod
    def get_count(cls):
        return cls.count

print(Person.get_count())  # Output: 0
p1 = Person("Alice")
print(Person.get_count())  # Output: 1
```

---

### `@property` – Creating Read-Only Properties  
The `@property` decorator **creates getter methods**.

```python
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def area(self):
        return 3.1416 * self._radius ** 2

c = Circle(5)
print(c.area)  # Output: 78.54 (No parentheses needed)
```

- The `area` method **behaves like an attribute** (`c.area` instead of `c.area()`).  

---

## 4.5.4. Chaining Multiple Decorators
Multiple decorators can be applied to a function.

```python
def uppercase(func):
    def wrapper():
        return func().upper()
    return wrapper

def exclamation(func):
    def wrapper():
        return func() + "!!!"
    return wrapper

@uppercase
@exclamation
def greet():
    return "hello"

print(greet())  # Output: HELLO!!!
```
- **Execution Order:** `exclamation` -> `uppercase` -> `greet()`.

---

## 4.5.5. Practical Use Cases for Decorators
**Logging Execution Time**
```python
import time

def timing_decorator(func):
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        print(f"Executed {func.__name__} in {end_time - start_time:.4f} seconds")
        return result
    return wrapper

@timing_decorator
def slow_function():
    time.sleep(2)
    return "Done"

print(slow_function())  
# Output: Executed slow_function in 2.0001 seconds
```

---

**Authentication Example**
```python
def authenticate(func):
    def wrapper(user):
        if user != "admin":
            print("Access denied")
            return
        return func(user)
    return wrapper

@authenticate
def secure_data(user):
    print("Access granted: Sensitive data")

secure_data("guest")  # Output: Access denied
secure_data("admin")  # Output: Access granted: Sensitive data
```

---

## 4.5.6. Summary Table
| Concept | Explanation |
|---------|-------------|
| **Higher-Order Function** | A function that takes/returns another function. |
| **Decorator** | A function that modifies another function without changing its code. |
| **`@staticmethod`** | Defines static methods inside a class. |
| **`@classmethod`** | Defines class methods operating on the class itself. |
| **`@property`** | Creates a method that acts like a read-only attribute. |
| **`functools.wraps`** | Preserves original function metadata in decorators. |
| **Chaining Decorators** | Multiple decorators can be applied to a function. |
