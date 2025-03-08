# **5.2. Instance and Class Methods & Attributes**  

In Python **Object-Oriented Programming (OOP)**, **methods** define behavior, while **attributes** store data. There are two primary types:  

1. **Instance Methods & Attributes** → Specific to each object (instance).  
2. **Class Methods & Attributes** → Shared across all instances of the class.  

---

## 5.2.1. Instance Methods & Attributes  
Instance methods and attributes are **tied to an object**.  

### Instance Attributes  
- Defined inside the **`__init__`** constructor.  
- Each instance gets **its own copy**.  

```python
class Person:
    def __init__(self, name, age):
        self.name = name  # Instance attribute
        self.age = age    # Instance attribute

# Creating instances
p1 = Person("Alice", 30)
p2 = Person("Bob", 25)

# Each instance has unique attribute values
print(p1.name, p1.age)  # Output: Alice 30
print(p2.name, p2.age)  # Output: Bob 25
```
- `self.name` and `self.age` are **instance attributes.**  
- **Each object (`p1`, `p2`)** has its own values.  

---

### Instance Methods  
- Defined inside the class, using `self` as the first parameter.  
- Can access and modify **instance attributes**.  

```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    def display_info(self):  # Instance method
        print(f"This is a {self.brand} {self.model}.")

# Creating objects
car1 = Car("Toyota", "Corolla")
car2 = Car("Tesla", "Model S")

# Calling instance methods
car1.display_info()  # Output: This is a Toyota Corolla.
car2.display_info()  # Output: This is a Tesla Model S.
```
- `self.brand` and `self.model` **are accessed using `self`.**  
- Instance methods operate on **an instance’s data.**  

---

## 5.2.2. Class Attributes & Methods  
Apply to the whole class, not just a single object.  

### Class Attributes  
- Defined **outside `__init__`** (directly inside the class).  
- Shared among **all instances** of the class.  

**Class Attributes**
```python
class Dog:
    species = "Canis familiaris"  # Class attribute (shared by all instances)

    def __init__(self, name, age):
        self.name = name  # Instance attribute
        self.age = age    # Instance attribute

# Creating objects
dog1 = Dog("Buddy", 3)
dog2 = Dog("Max", 5)

# Accessing class attribute
print(dog1.species)  # Output: Canis familiaris
print(dog2.species)  # Output: Canis familiaris

# Modifying an instance attribute does NOT affect other instances
dog1.age = 4
print(dog1.age)  # Output: 4
print(dog2.age)  # Output: 5

# Modifying a class attribute affects all instances
Dog.species = "Wolf"
print(dog1.species)  # Output: Wolf
print(dog2.species)  # Output: Wolf
```
- `species` is a **class attribute** (same for all dogs).  
- **Instance attributes** (`name`, `age`) are unique to each object.  

---

### Class Methods (`@classmethod`)  
- Use **`@classmethod`** decorator.  
- First parameter is **`cls` (class itself, not an instance)**.  
- Can **modify class attributes**, but not instance attributes.  

```python
class Employee:
    company_name = "TechCorp"  # Class attribute

    def __init__(self, name, salary):
        self.name = name
        self.salary = salary

    @classmethod
    def set_company(cls, new_name):
        cls.company_name = new_name  # Modifying class attribute

# Creating an object
e1 = Employee("Alice", 50000)

# Before modifying class attribute
print(e1.company_name)  # Output: TechCorp

# Using class method to modify class attribute
Employee.set_company("NextGenTech")

# After modification, all instances see the updated value
print(e1.company_name)  # Output: NextGenTech
```
- `@classmethod` can change **class attributes.**  
- **All instances reflect the modified value.**  

---

## 5.2.3. Class Methods vs. Instance Methods  
| Feature | Instance Method | Class Method |
|---------|---------------|-------------|
| **Decorator** | No decorator | `@classmethod` |
| **First Parameter** | `self` (instance) | `cls` (class) |
| **Can Modify** | Instance attributes | Class attributes |
| **Called By** | Object | Class or Object |
| **Example** | `self.name = "Alice"` | `cls.company_name = "NewName"` |

---

## 5.2.4. Using Class and Instance Methods Together
Sometimes, you need **both instance and class methods**.

```python
class Library:
    library_name = "City Library"  # Class attribute

    def __init__(self, book, author):
        self.book = book  # Instance attribute
        self.author = author  # Instance attribute

    def display_book(self):  # Instance method
        print(f"Book: {self.book}, Author: {self.author}")

    @classmethod
    def change_library_name(cls, new_name):  # Class method
        cls.library_name = new_name

# Creating instances
book1 = Library("1984", "George Orwell")
book2 = Library("Brave New World", "Aldous Huxley")

# Using instance method
book1.display_book()  # Output: Book: 1984, Author: George Orwell

# Changing class attribute using class method
Library.change_library_name("National Library")

# All instances see the updated class attribute
print(book1.library_name)  # Output: National Library
print(book2.library_name)  # Output: National Library
```
- `display_book()` is an **instance method** operating on an object.  
- `change_library_name()` is a **class method** modifying a class attribute.  

---

## 5.2.5. Using `@classmethod` for Alternative Constructors
Class methods can be used to **create alternative constructors**.

```python
class User:
    def __init__(self, username, age):
        self.username = username
        self.age = age

    @classmethod
    def from_string(cls, user_info):  # Alternative constructor
        username, age = user_info.split("-")
        return cls(username, int(age))

# Creating an instance using an alternative constructor
user1 = User.from_string("john_doe-25")

print(user1.username)  # Output: john_doe
print(user1.age)       # Output: 25
```
- **Allows creating objects from custom formatted strings.**  
- **Great for parsing data from files or databases.**  

---

## Key Takeaways
| Concept | Explanation |
|---------|-------------|
| **Instance Attributes** | Unique to each object (`self.attribute`). |
| **Class Attributes** | Shared across all instances (`ClassName.attribute`). |
| **Instance Methods** | Operate on an object (`self`). |
| **Class Methods** | Operate on the class (`cls`). |
| **`@classmethod`** | Used to modify class attributes and define alternative constructors. |
