# **6.2 Using `try`, `except`, `finally`, and `else` in Python** 🚀  

This allows you to **gracefully handle errors** instead of letting your program crash.  

## 6.2.1. `try` and `except`: Catching Errors  
  
- Code inside the `try` block **executes normally**.  
- If an error occurs, the program **jumps to the `except` block** instead of crashing.  

```python
try:
    result = 10 / 0  # ZeroDivisionError
except ZeroDivisionError:
    print("Cannot divide by zero!")

"""Output  
Cannot divide by zero!
"""
```

**Catching Multiple Errors**:  
```python
try:
    num = int("hello")  # ValueError
except ValueError:
    print("Invalid input! Please enter a number.")
"""Output:  
Invalid input! Please enter a number.
"""
```

---

## 6.2.2. Catching Multiple Exception Types  

**Handling different exceptions separately**:  
```python
try:
    my_list = [1, 2, 3]
    print(my_list[5])  # IndexError
except IndexError:
    print("Index out of range!")
except ZeroDivisionError:
    print("Cannot divide by zero!")

"""Output:  
Index out of range
"""
```

**Handling multiple errors in one `except` block**:  
```python
try:
    num = int("hello")
except (ValueError, TypeError):
    print("Something went wrong with the input.")

"""Output:  
Something went wrong with the input.
"""
```

---

## 6.2.3. `else`: Running Code When No Error Occurs  

The `else` block runs **only if no error occurs** in the `try` block.  
  
```python
try:
    num = int(input("Enter a number: "))  # No error if user enters a number
except ValueError:
    print("Invalid input! Please enter a number.")
else:
    print(f"Success! You entered {num}.")

"""
Scenario 1 (User inputs `42`):  
Enter a number: 42
Success! You entered 42.

Scenario 2 (User inputs `"hello"`):  
Enter a number: hello
Invalid input! Please enter a number.
"""
```

---

## 6.2.4. `finally`: Always Executes (Cleanup Code) 

The `finally` block runs **no matter what**—even if an error occurs.   
Useful for **cleanup operations** (e.g., closing files, releasing resources).  
 
```python
try:
    file = open("data.txt", "r")
    content = file.read()
except FileNotFoundError:
    print("File not found!")
finally:
    print("Closing the file...")
    file.close()  # Always executes

""" 
Output (if file exists): 
Closing the file...

Output (if file is missing):  
File not found!
Closing the file...
"""
```

---

## 6.2.5. Raising Exceptions with `raise`   

You can **manually raise errors** using `raise`:  
```python
def check_age(age):
    if age < 18:
        raise ValueError("Age must be 18 or older!")
    print("Access granted!")

try:
    check_age(15)  # ValueError
except ValueError as e:
    print(f"Error: {e}")

""" Output:  
Error: Age must be 18 or older!
"""
```

---

# **Key Takeaways**
- **`try-except` prevents crashes by handling errors gracefully.**  
- **`except` can handle multiple error types separately or together.**  
- **`else` runs only if no error occurs.**  
- **`finally` always runs—use it for cleanup.**  
- **Use `raise` to create custom errors.**  

