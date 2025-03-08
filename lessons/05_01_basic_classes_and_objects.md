# **5.1. Basics: Classes and Objects**  

**Object-Oriented Programming (OOP)** is a programming paradigm that allows structuring code into reusable, modular, and scalable components.  

- **Class** → A blueprint for creating objects.  
- **Object** → An instance of a class with unique data and behavior.  

---

## 5.1.1. Class  
A **class** is a **template** for creating objects.  
- It defines **attributes (data)** and **methods (behavior)**.  
- Objects created from a class **share its structure but have independent values**.

**Syntax of a Class**
```python
class ClassName:
    # Class body
    pass
```
---

## 5.1.2. Creating a Simple Class and Object

```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand  # Attribute
        self.model = model  # Attribute

    def display_info(self):  # Method
        print(f"This is a {self.brand} {self.model}.")

# Creating objects (instances)
car1 = Car("Toyota", "Corolla")
car2 = Car("Tesla", "Model S")

# Calling a method
car1.display_info()  # Output: This is a Toyota Corolla.
car2.display_info()  # Output: This is a Tesla Model S.
```
- `self` represents **the instance** (object) of the class.  
- `__init__` **is the constructor**, called when an object is created.  

---

## **5.1.3. The `self` Parameter**
- `self` **represents the instance** of the class.  
- It must be **the first parameter** in every instance method.  

### `self` in Methods**
```python
class Laptop:
    def __init__(self, brand):
        self.brand = brand

    def show_brand(self):
        print(f"This laptop is a {self.brand}.")

# Creating an object
laptop1 = Laptop("Dell")
laptop1.show_brand()  # Output: This laptop is a Dell.
```
- **`self.brand` accesses the `brand` attribute of the instance.**  

### Common Mistake: Forgetting `self`
```python
class Example:
    def print_message():
        print("Hello!")

obj = Example()
obj.print_message()  #  TypeError: print_message() takes 0 arguments but 1 was given
```
- **Fix:** Add `self` as the first parameter.
```python
class Example:
    def print_message(self):
        print("Hello!")

obj = Example()
obj.print_message()  # Output: Hello!
```

---

## **5.1.4. Modifying and Deleting Attributes**
### Modifying Attributes
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

p1 = Person("Alice", 30)
p1.age = 31  # Modifying an attribute
print(p1.age)  # Output: 31
```

### Deleting Attributes
```python
del p1.age  # Removes the 'age' attribute
# print(p1.age)  #  AttributeError: 'Person' object has no attribute 'age'
```
- **Use `del` to remove attributes dynamically.**  

---

## 5.1.5. Deleting an Object
An object can be deleted using `del`.

```python
p2 = Person("Bob", 40)
del p2  # Deletes the object
# print(p2.name)  # ❌ NameError: name 'p2' is not defined
```
- **Objects are deleted when no references exist.**  
- Python's **Garbage Collector (GC) automatically frees memory.**

---

## 5.1.6. Checking Object Type (`isinstance()`)
The `isinstance()` function checks if an object belongs to a class.

```python
print(isinstance(car1, Car))  # Output: True
print(isinstance(car1, int))  # Output: False
```

---

## **5.1.7. Class vs. Instance Variables**
| Feature | Instance Variables | Class Variables |
|---------|-------------------|---------------|
| **Scope** | Specific to each object | Shared across all instances |
| **Defined In** | `__init__` method | Inside the class (outside `__init__`) |
| **Example** | `self.name = "Alice"` | `class_variable = "shared_value"` |

---

## **5.1.10. Best Practices for Using Classes and Objects**
**Follow these best practices for clean, maintainable code.**  

- **Use meaningful class names** → `Car`, `Person`, `Employee` instead of `C1`, `Obj`.  
- **Use `self` to access instance variables.**  
- **Keep methods short and focused** on a single responsibility.  
- **Avoid hardcoding values** → Use `__init__` to initialize attributes.  
- **Use `isinstance()` to check object types safely.**  

---

## Summary Table
| Concept | Explanation |
|---------|-------------|
| **Class** | A blueprint for creating objects. |
| **Object** | An instance of a class with unique attributes. |
| **`__init__`** | The constructor method, initializes object attributes. |
| **Instance Variable** | Belongs to an individual object (`self.name`). |
| **Class Variable** | Shared among all instances. |
| **Methods** | Functions inside a class that operate on instance data. |
| **`self`** | Represents the current object instance. |
| **`isinstance()`** | Checks if an object belongs to a class. |

