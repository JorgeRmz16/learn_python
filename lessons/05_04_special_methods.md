# **5.4. Special Methods (`__init__`, `__str__`, `__repr__`, `__call__`)**  

Special methods (also called **dunder methods**, short for “double underscore”) allow Python classes to behave like built-in types. These methods **customize object behavior** and make objects **more intuitive and Pythonic**.  


---

## 5.4.1. `__init__` (Constructor Method)
The `__init__` method is called when an object is created. It **initializes** the object's attributes.  

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

# Creating an object
p1 = Person("Alice", 25)
print(p1.name)  # Output: Alice
print(p1.age)   # Output: 25
```
- `__init__` sets up initial values for an object.  
- **Called automatically** when an object is created.  

---

## 5.4.2. `__str__` (Human-Readable Representation)
`__str__` is called when `print(object)` is used. It provides a **user-friendly string representation** of the object.  

### Defining `__str__`
```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    def __str__(self):
        return f"{self.brand} {self.model}"

car1 = Car("Tesla", "Model S")
print(car1)  # Output: Tesla Model S
```
- **Without `__str__`**, `print(car1)` would display something like `<__main__.Car object at 0x...>`  
- **With `__str__`**, we get a clean, readable output.  

---

## 5.4.3. `__repr__` (Developer Representation)
`__repr__` returns a **precise representation of an object**, useful for debugging.  

If `__str__` is not defined, `__repr__` is used as a fallback for `print()`.  

### Defining `__repr__`
```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    def __repr__(self):
        return f"Car('{self.brand}', '{self.model}')"

car1 = Car("Tesla", "Model S")
print(car1)  # Output: Car('Tesla', 'Model S')
```
- **Gives a detailed, exact representation.**  
- **Helps in debugging (`repr(object)`).**  

---

###  `__str__` vs `__repr__`
| Method | Purpose | Example Output |
|--------|---------|----------------|
| `__str__` | User-friendly representation | `"Tesla Model S"` |
| `__repr__` | Debug-friendly representation | `"Car('Tesla', 'Model S')"` |

**Best Practice:**  
- **Use `__repr__` for debugging** (should ideally be unambiguous and allow recreation of the object).  
- **Use `__str__` for user-friendly output** (descriptive, but not necessarily unambiguous).  

---

## 5.4.4. `__call__` (Making an Object Callable)
`__call__` allows an instance to be **called like a function**.  

### Using `__call__`
```python
class Multiplier:
    def __init__(self, factor):
        self.factor = factor

    def __call__(self, number):
        return number * self.factor

times3 = Multiplier(3)
print(times3(10))  # Output: 30
print(times3(5))   # Output: 15
```
- `times3(10)` acts like a function but **is actually an object**  
- Useful for decorators and function-like objects.  

---

## Advanced Example: Combining Special Methods
```python
class Temperature:
    def __init__(self, celsius):
        self.celsius = celsius

    def __str__(self):
        return f"{self.celsius}°C"

    def __repr__(self):
        return f"Temperature({self.celsius})"

    def __call__(self, scale="C"):
        if scale == "C":
            return self.celsius
        elif scale == "F":
            return (self.celsius * 9/5) + 32
        else:
            return "Invalid scale"

temp = Temperature(25)

print(temp)       # Uses __str__ → Output: 25°C
print(repr(temp)) # Uses __repr__ → Output: Temperature(25)
print(temp("F"))  # Uses __call__ → Output: 77.0
print(temp("C"))  # Uses __call__ → Output: 25
```
- `__str__` makes output user-friendly.  
- `__repr__` helps with debugging.  
- `__call__` allows the object to be used like a function.  

---

## Key Takeaways
| Special Method | Purpose |
|---------------|---------|
| `__init__` | Initializes an object |
| `__str__` | Returns a human-readable string representation |
| `__repr__` | Returns a developer-friendly string representation |
| `__call__` | Makes an object callable like a function |
