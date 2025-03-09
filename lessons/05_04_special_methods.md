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

### 5.4.5. `__len__` (Getting the Length of an Object)
The `__len__` method allows an object to work with the built-in `len()` function.

```python
class Playlist:
    def __init__(self, songs):
        self.songs = songs

    def __len__(self):
        return len(self.songs)

my_playlist = Playlist(["Song1", "Song2", "Song3"])
print(len(my_playlist))  # Output: 3
```
- This makes `Playlist` objects behave like built-in sequences.

---

### 5.4.6. `__getitem__`, `__setitem__`, `__delitem__` (Indexing & Slicing)
These methods allow objects to behave like lists or dictionaries.

```python
class Bookshelf:
    def __init__(self):
        self.books = {}

    def __setitem__(self, index, book):
        self.books[index] = book

    def __getitem__(self, index):
        return self.books.get(index, "Not found")

    def __delitem__(self, index):
        if index in self.books:
            del self.books[index]

shelf = Bookshelf()
shelf[0] = "Python Crash Course"
shelf[1] = "Automate the Boring Stuff"

print(shelf[0])  # Output: Python Crash Course
del shelf[1]
print(shelf[1])  # Output: Not found
```
- `__getitem__` lets objects be accessed with `obj[index]`.
- `__setitem__` allows assignment (`obj[index] = value`).
- `__delitem__` enables deletion (`del obj[index]`).

---

### 5.4.7. `__iter__` and `__next__` (Making an Object Iterable)
These methods allow objects to be used in loops.

```python
class Counter:
    def __init__(self, max_count):
        self.max_count = max_count
        self.current = 0

    def __iter__(self):
        return self  # Returns an iterator

    def __next__(self):
        if self.current >= self.max_count:
            raise StopIteration  # Stops the loop
        self.current += 1
        return self.current

counter = Counter(5)
for num in counter:
    print(num)  # Output: 1 2 3 4 5
```
- `__iter__` returns the iterator (usually `self`).
- `__next__` defines how iteration progresses.

---

### 5.4.8. `__eq__`, `__lt__`, `__gt__` (Comparison Operators)
These methods define custom comparison behavior.

```python
class Box:
    def __init__(self, volume):
        self.volume = volume

    def __eq__(self, other):
        return self.volume == other.volume

    def __lt__(self, other):
        return self.volume < other.volume

    def __gt__(self, other):
        return self.volume > other.volume

box1 = Box(30)
box2 = Box(40)

print(box1 == box2)  # Output: False
print(box1 < box2)   # Output: True
print(box1 > box2)   # Output: False
```
- `__eq__` (`==`) checks equality.
- `__lt__` (`<`) checks if an object is smaller.
- `__gt__` (`>`) checks if an object is greater.

---

### 5.4.9. `__add__`, `__sub__`, `__mul__`, etc. (Operator Overloading)
These methods allow objects to use arithmetic operators.

```python
class Money:
    def __init__(self, amount):
        self.amount = amount

    def __add__(self, other):
        return Money(self.amount + other.amount)

    def __sub__(self, other):
        return Money(self.amount - other.amount)

wallet1 = Money(50)
wallet2 = Money(30)

wallet3 = wallet1 + wallet2  # Calls __add__
print(wallet3.amount)  # Output: 80

wallet4 = wallet1 - wallet2  # Calls __sub__
print(wallet4.amount)  # Output: 20
```
- `__add__` enables `+` for objects.
- `__sub__` enables `-` for objects.

---

### 5.4.10. `__enter__` and `__exit__` (Context Managers)
These methods allow objects to be used in `with` statements.

```python
class FileManager:
    def __init__(self, filename):
        self.filename = filename

    def __enter__(self):
        self.file = open(self.filename, "w")
        return self.file

    def __exit__(self, exc_type, exc_value, traceback):
        self.file.close()

with FileManager("test.txt") as f:
    f.write("Hello, world!")
```
- `__enter__` is called when entering `with`.
- `__exit__` is called when exiting (even if an error occurs).

---

### **Summary of Additional Special Methods**
| Special Method | Purpose |
|---------------|---------|
| `__init__` | Initializes an object |
| `__str__` | Returns a human-readable string representation |
| `__repr__` | Returns a developer-friendly string representation |
| `__call__` | Makes an object callable like a function |
| `__len__` | Defines `len(obj)` |
| `__getitem__` | Enables `obj[key]` access |
| `__setitem__` | Enables `obj[key] = value` |
| `__delitem__` | Enables `del obj[key]` |
| `__iter__`, `__next__` | Makes an object iterable |
| `__eq__`, `__lt__`, `__gt__`, etc. | Enables comparison (`==`, `<`, `>`, etc.) |
| `__add__`, `__sub__`, etc. | Enables arithmetic operations (`+`, `-`, etc.) |
| `__enter__`, `__exit__` | Enables `with` statement support |

