# **04.03. Variable Scope(global, nonlocal)**  

Scope defines **where a variable can be accessed** within a program.

| Scope Type | Description |
|------------|-------------|
| **Local** | Exists **only inside a function**. |
| **Global** | Defined **outside any function**, accessible everywhere. |
| **Nonlocal** | Used in **nested functions** to modify a variable in the enclosing scope. |

---

## 4.3.1. Local Scope (Function-Level Scope)  
Is **declared inside a function** and can only be accessed within that function.

```python
def greet():
    message = "Hello, World!"  # Local variable
    print(message)

greet()
print(message)  # Error: 'message' is not defined outside the function
```
**Key Takeaways:**  
- Local variables **cannot** be accessed outside their function.  
- Each function creates a **new** local scope.  

---

## 4.3.2. Global Scope (Accessible Everywhere)  
Is declared **outside any function** and can be accessed anywhere in the script.

```python
message = "Hello from global scope!"  # Global variable

def greet():
    print(message)  # Accessible inside the function

greet()
print(message)  # Accessible outside the function
```
**Key Takeaways:**  
- Global variables can be accessed **inside and outside** functions.  
- Use global variables **sparingly** to avoid unexpected modifications.  

---

## 4.3.3. Modifying Global Variables Inside Functions (`global`)  
By default, functions cannot modify global variables unless explicitly declared using `global`.

```python
counter = 0  # Global variable

def increment():
    global counter  # Declare 'counter' as global
    counter += 1  # Modify global variable

increment()
print(counter)  # Output: 1
```
**Key Takeaways:**  
- Use `global` **only when necessary**, as modifying global variables inside functions reduces readability and maintainability.  
- Instead of modifying global variables, **return values** and use function parameters.  

**Better Alternative: Avoid `global`**
```python
def increment(counter):
    return counter + 1

counter = 0
counter = increment(counter)
print(counter)  # Output: 1
```

---

## 4.3.4. Nonlocal Scope (`nonlocal`) – Modifying Variables in Nested Functions  
In **nested functions**, an inner function can modify a variable from the outer function using `nonlocal`.

```python
def outer():
    message = "Hello"

    def inner():
        nonlocal message  # Modify the variable in the outer function
        message = "Hello, World!"
    
    inner()
    print(message)  # Output: Hello, World!

outer()
```
**Key Takeaways:**  
- `nonlocal` allows modification of **variables from the enclosing function** (not global).  
- Useful in **closures and decorators**.  

---

## 4.3.5. LEGB Rule (Scope Resolution in Python)  
Python follows the **LEGB** (Local - Enclosing - Global - Built-in) rule to **resolve variable names**.

| Scope | Example |
|--------|-------------|
| **Local** | Variables inside a function (`x` in a function). |
| **Enclosing** | Variables in the **outer function** of a nested function. |
| **Global** | Variables declared at the **top level** of a script. |
| **Built-in** | Python’s built-in names (`print`, `len`, etc.). |

### **Example: LEGB Rule in Action**
```python
x = "global"  # Global scope

def outer():
    x = "enclosing"  # Enclosing scope
    
    def inner():
        x = "local"  # Local scope
        print(x)  # Prints: local
    
    inner()
    print(x)  # Prints: enclosing

outer()
print(x)  # Prints: global
```
1- Python first looks in Local Scope (`inner()`),  
2- If not found, it checks Enclosing Scope (`outer()`),  
3- If not found, it checks Global Scope,  
4- Finally, it looks in Built-in Scope (if applicable). 

---

## 4.3.6. Best Practices for Managing Scope 

✔ **Use local variables whenever possible** to prevent unintended side effects.  
✔ **Avoid using `global`** unless absolutely necessary.  
✔ **Use `nonlocal`** only when working with nested functions.  
✔ **Follow the LEGB rule** to understand how Python resolves variable names.  
✔ **Pass values as function arguments** instead of modifying global variables.  

---

## **Summary**
| Scope Type | Description |
|------------|-------------|
| **Local** | Exists **only inside a function** and cannot be accessed elsewhere. |
| **Global** | Defined **outside functions**, accessible everywhere. |
| **Nonlocal** | Used in **nested functions** to modify a variable in the enclosing function. |
| **LEGB Rule** | Python searches variables in **Local → Enclosing → Global → Built-in** order. |
| **Best Practice** | Prefer **local variables**, avoid `global`, use `nonlocal` cautiously. |
