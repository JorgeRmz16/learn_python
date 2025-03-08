# **5.3. Abstraction, Encapsulation, Inheritance, and Polymorphism**  

Python **Object-Oriented Programming (OOP)** is built on **four key principles**:  

1. **Abstraction** → Hides unnecessary details and shows only relevant information.  
2. **Encapsulation** → Restricts direct access to object data and methods.  
3. **Inheritance** → Allows a class to derive attributes and methods from another class.  
4. **Polymorphism** → Lets different classes have methods with the same name but different behaviors.  
---

## 5.3.1. Abstraction (Hiding Details)  
**Abstraction** means **hiding complex implementation details** and exposing only what’s necessary.  

### Abstract Classes and Methods  
- **Abstract classes** cannot be instantiated (you cannot create objects from them).  
- **Abstract methods** must be implemented in subclasses.  
- We use the **`ABC` (Abstract Base Class) module** in Python.  


```python
from abc import ABC, abstractmethod

class Animal(ABC):  # Abstract class
    @abstractmethod
    def make_sound(self):  # Abstract method
        pass

class Dog(Animal):
    def make_sound(self):
        return "Woof!"

class Cat(Animal):
    def make_sound(self):
        return "Meow!"

# Creating objects
dog = Dog()
cat = Cat()

print(dog.make_sound())  # Output: Woof!
print(cat.make_sound())  # Output: Meow!
```
- **`Animal` is an abstract class (cannot be instantiated directly).**  
- **Subclasses (`Dog`, `Cat`) must implement `make_sound()`.**  

---

## 5.3.2. Encapsulation (Data Protection)  
**Encapsulation** restricts **direct access** to object attributes and methods to prevent unintended modification.  

### Access Modifiers in Python
| Modifier | Example | Access |
|----------|---------|--------|
| **Public** | `self.name` | Accessible from anywhere |
| **Protected** | `self._age` | Should be used only within the class and subclasses |
| **Private** | `self.__salary` | Cannot be accessed directly from outside the class |

---

### Example: Public, Protected, and Private Attributes
```python
class Employee:
    def __init__(self, name, age, salary):
        self.name = name          # Public attribute
        self._age = age           # Protected attribute
        self.__salary = salary    # Private attribute

    def get_salary(self):  # Public method to access private attribute
        return self.__salary

# Creating object
emp = Employee("Alice", 30, 50000)

# Accessing attributes
print(emp.name)    # Output: Alice (Public attribute)
print(emp._age)    # Output: 30 (Protected, but still accessible)
# print(emp.__salary)  #  Error: AttributeError

# Accessing private attribute via public method
print(emp.get_salary())  # Output: 50000
```
✔ **Public attributes** (`name`) can be accessed directly.  
✔ **Protected attributes** (`_age`) should be used with caution.  
✔ **Private attributes** (`__salary`) are hidden but can be accessed via a method (`get_salary()`).  

---

## 5.3.3. Inheritance (Reusing Code)  
**Inheritance** allows a child class to inherit attributes and methods from a parent class.  

### Types of Inheritance
| Type | Description |
|------|-------------|
| **Single Inheritance** | One class inherits from another. |
| **Multiple Inheritance** | A class inherits from multiple classes. |
| **Multilevel Inheritance** | A class inherits from another class, which also inherits from another class. |
| **Hierarchical Inheritance** | Multiple classes inherit from a single parent class. |

---

### Single Inheritance
```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        return "I make a sound"

class Dog(Animal):  # Inheriting from Animal
    def speak(self):
        return "Woof!"

dog = Dog("Buddy")
print(dog.name)   # Output: Buddy (Inherited attribute)
print(dog.speak())  # Output: Woof! (Overridden method)
```
- **Dog class inherits from Animal.**  
- The `speak()` method **is overridden** in the child class.  

---

### Multiple Inheritance
```python
class Engine:
    def start(self):
        return "Engine started"

class Wheels:
    def roll(self):
        return "Wheels are rolling"

class Car(Engine, Wheels):  # Inheriting from multiple classes
    def drive(self):
        return "Car is moving"

car = Car()
print(car.start())  # Output: Engine started
print(car.roll())   # Output: Wheels are rolling
print(car.drive())  # Output: Car is moving
```
- **`Car` inherits from both `Engine` and `Wheels`.**  
- **It can access methods from both parent classes.**  

---

## 5.3.4. Polymorphism (Same Interface, Different Implementation)  
**Polymorphism** allows objects of different classes to be treated as if they belong to the same superclass.

### Method Overriding
```python
class Bird:
    def fly(self):
        return "Some birds can fly"

class Sparrow(Bird):
    def fly(self):
        return "Sparrow flies high"

class Penguin(Bird):
    def fly(self):
        return "Penguins cannot fly"

# Using polymorphism
birds = [Sparrow(), Penguin()]

for bird in birds:
    print(bird.fly())

# Output:
# Sparrow flies high
# Penguins cannot fly
```
- **Different bird types override `fly()` differently.**  
- **The same method name works for different classes.**  

---

### Operator Overloading
Python allows **overloading operators** using **special methods**.

**Example: Overloading `+` Operator**
```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):  # Overloading +
        return Vector(self.x + other.x, self.y + other.y)

    def __str__(self):
        return f"({self.x}, {self.y})"

v1 = Vector(2, 3)
v2 = Vector(4, 5)
v3 = v1 + v2  # Uses __add__()

print(v3)  # Output: (6, 8)
```
- **Overloading `+` allows adding `Vector` objects.**  
- **Python calls `__add__()` method.**  

---

## Key Takeaways
| Concept | Explanation |
|---------|-------------|
| **Abstraction** | Hides implementation details and enforces a structure using abstract classes. |
| **Encapsulation** | Restricts access to attributes using **public, protected, and private** access modifiers. |
| **Inheritance** | Allows a child class to inherit attributes and methods from a parent class. |
| **Polymorphism** | Allows the same method name to work differently for different objects. |
