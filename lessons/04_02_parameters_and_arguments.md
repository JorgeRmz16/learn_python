# **4.2 Parameters and Arguments in Functions**  


### Parameters vs. Arguments  

| Term        | Description |
|------------|-------------|
| **Parameter** | The variable listed inside the function definition. |
| **Argument**  | The actual value passed to a function when calling it. |

```python
def greet(name):  # 'name' is a parameter
    print(f"Hello, {name}!")

greet("Alice")  # 'Alice' is an argument
```
---

## **4.2.1. Positional Arguments**  
Arguments are **assigned to parameters based on their position**.

### **Example: Positional Arguments**
```python
def introduce(name, age):
    print(f"My name is {name} and I am {age} years old.")

introduce("Alice", 25) # Correct order
# Output: `My name is Alice and I am 25 years old.`

introduce(25, "Alice")  # Wrong order!
# Output: `My name is 25 and I am Alice years old.`
```
**Key Takeaway:**  
- **Order matters** when using positional arguments.

---

## **4.2.2. Keyword Arguments (Named Arguments)**  
You can explicitly assign values to parameters using **keyword arguments**, ignoring order.

```python
introduce(age=25, name="Alice")  # Order doesn't matter
# Output: `My name is Alice and I am 25 years old.` 
```

**Key Takeaway:**  
- Keyword arguments make function calls **clearer** and **order-independent**.

---

## **4.2.3. Default Parameters**  
You can provide a **default value** for parameters.

```python
def greet(name="Guest"):
    print(f"Hello, {name}!")

greet()        # Output: Hello, Guest!
greet("Bob")   # Output: Hello, Bob!
```
**Key Takeaway:**  
- Default values make functions **more flexible** by allowing calls with or without arguments.

---

## **4.2.4. Variable-Length Arguments (`*args`)**  
`*args` allows a function to accept **any number of positional arguments** as a **tuple**.

```python
def add_numbers(*numbers):
    return sum(numbers)

print(add_numbers(1, 2, 3, 4, 5))  # Output: 15
```
**Iterating Over `*args`**
```python
def display_items(*items):
    for item in items:
        print(f"- {item}")

display_items("Apple", "Banana", "Cherry")
"""Output:  
- Apple
- Banana
- Cherry
"""
```
**Key Takeaway:**  
- Use `*args` when a function needs to accept **multiple positional arguments**.

---

## 4.2.5. Variable-Length Keyword Arguments (`**kwargs`)  
`**kwargs` allows a function to accept **any number of keyword arguments** as a **dictionary**.

```python
def display_info(**info):
    for key, value in info.items():
        print(f"{key}: {value}")

display_info(name="Alice", age=25, country="USA")
"""Output:  
name: Alice  
age: 25  
country: USA
"""
```

**Key Takeaway:**  
- Use `**kwargs` when a function should accept **multiple keyword arguments**.

---

## 4.2.6. Combining Positional, `*args`, and `**kwargs`  
Functions can use **all argument types together**, following this order:  

**1- Positional parameters**  
**2- Default parameters**  
**3- `*args`** (Collects extra positional arguments)  
**4- `**kwargs`** (Collects extra keyword arguments)  

**Example: Mixing Arguments**
```python
def order_pizza(size, crust="thin", *toppings, **extras):
    print(f"Order: {size} pizza with {crust} crust")
    
    if toppings:
        print("Toppings:", ", ".join(toppings))
    
    if extras:
        print("Extras:")
        for key, value in extras.items():
            print(f"  {key}: {value}")

order_pizza("Large", "thick", "Pepperoni", "Mushrooms", cheese="Extra", sauce="BBQ")
"""Output:**  
Order: Large pizza with thick crust  
Toppings: Pepperoni, Mushrooms  
Extras:  
  cheese: Extra  
  sauce: BBQ 
""" 
```

**Key Takeaway:**  
- Mixing `*args` and `**kwargs` allows handling **complex function calls dynamically**.

---

## 4.2.7. Unpacking Arguments with `*` and `**`
`*` and `**` can be used to **unpack** arguments from lists and dictionaries.

**Unpacking Lists into `*args`**
```python
def multiply(a, b, c):
    return a * b * c

nums = [2, 3, 4]
result = multiply(*nums)  # Unpacks list into arguments
print(result)  # Output: 24
```

**Unpacking Dictionaries into `**kwargs`**
```python
def greet(name, age):
    print(f"Hello, {name}! You are {age} years old.")

info = {"name": "Alice", "age": 25}
greet(**info)  # Unpacks dictionary into arguments
# Output: `Hello, Alice! You are 25 years old.` 
```

**Key Takeaway:**  
- `*` unpacks a **list/tuple** into positional arguments.  
- `**` unpacks a **dictionary** into keyword arguments.

---

## **4.2.8. Best Practices for Function Arguments**

- **Use positional arguments** for required values.  
- **Use keyword arguments** for clarity and flexibility.  
- **Provide default values** where applicable.  
- **Use `*args`** for handling multiple positional arguments.  
- **Use `**kwargs`** for dynamic keyword arguments.  
- **Maintain a logical order:** positional > default > `*args` > `**kwargs`.  
- **Use argument unpacking (`*` and `**`)** for passing lists/dictionaries dynamically.  

---

## **Summary**
| Concept | Description |
|---------|-------------|
| **Positional Arguments** | Assigned based on order. |
| **Keyword Arguments** | Explicitly assign values using parameter names. |
| **Default Parameters** | Provide a default value if no argument is passed. |
| **`*args`** | Collect multiple positional arguments into a tuple. |
| **`**kwargs`** | Collect multiple keyword arguments into a dictionary. |
| **Mixing Arguments** | Use positional, default, `*args`, and `**kwargs` together. |
| **Unpacking (`*`, `**`)** | Convert lists/tuples to `*args` and dictionaries to `**kwargs`. |
