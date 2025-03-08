# **5.6. Metaclasses and `type()`**  

Metaclasses are one of Python’s most **powerful and advanced** features. Understanding them will take your Python mastery to the **next level**.  

---
## What is a Metaclass?  
- Is a class that defines how other **classes are created**.  
- In Python, **everything is an object**, including classes themselves.  
- A **metaclass controls the creation and behavior of classes** (just like a class controls object creation).  

### Simple Analogy  
- **Objects** are **instances of classes**.  
- **Classes** are **instances of metaclasses**.  
- The **default metaclass** in Python is `type()`.  

**Understanding Class and Object Relationships**  
```python
class MyClass:
    pass

obj = MyClass()

# Checking types
print(type(obj))      # Output: <class '__main__.MyClass'>
print(type(MyClass))  # Output: <class 'type'>  → MyClass is created by "type"
```
- The object `obj` is an instance of `MyClass`.  
- The class `MyClass` is an **instance of `type`**, meaning `type` is the **metaclass**.  

---

## The `type()` Function as a Metaclass  

The `type()` function has **two different uses**:  
1. **Checking** the type of an object  
2. Dynamically **creating** a class  

**Checking an Object’s Type**  
```python
print(type(42))      # Output: <class 'int'>
print(type("hello")) # Output: <class 'str'>
print(type([]))      # Output: <class 'list'>
```

**Dynamically Creating a Class**  
Instead of using `class MyClass: ...`, we can create a class on the fly using `type()`.  
```python
# Creating a class dynamically
MyDynamicClass = type("MyDynamicClass", (object,), {"attr": 42})

# Using the dynamically created class
obj = MyDynamicClass()
print(obj.attr)  # Output: 42

# Equivalent to:
class MyDynamicClass:
    attr = 42
```
`type()` takes **3 arguments**:
1. Class **name** -> `"MyDynamicClass"`
2. Parent **class(es)** -> `(object,)`
3. **Attributes/Methods** (dictionary) -> `{"attr": 42}`  

---

## 5.6.1 Creating Custom Metaclasses  

A metaclass is a class whose instances are classes.  
Instead of letting `type()` create a class, we can define a **custom metaclass** to modify how classes are built.  

**Custom Metaclass**
```python
class MyMeta(type):  # Inheriting from "type"
    def __new__(cls, name, bases, class_dict):
        print(f"Creating class: {name}")
        return super().__new__(cls, name, bases, class_dict)

# Using MyMeta as a metaclass
class MyClass(metaclass=MyMeta):
    pass

# Output:
# Creating class: MyClass
```
- **`__new__` is called when a class is created.**  
- `MyMeta` modifies how `MyClass` is constructed.  

---

## 5.6.2 Advanced Metaclass Customization  
###  Enforcing Class Attribute Rules 

We can use a metaclass to **enforce coding rules** inside a class.  

```python
class UpperCaseAttributesMeta(type):
    def __new__(cls, name, bases, class_dict):
        # Check if attributes are uppercase
        for attr, value in class_dict.items():
            if not attr.startswith("__") and not attr.isupper():
                raise ValueError(f"Attribute '{attr}' must be uppercase")
        return super().__new__(cls, name, bases, class_dict)

# Applying the metaclass
class MyClass(metaclass=UpperCaseAttributesMeta):
    MY_CONSTANT = 42  # Valid

# Uncommenting the following will cause an error:
# class MyWrongClass(metaclass=UpperCaseAttributesMeta):
#     my_constant = 42  #  ValueError: Attribute 'my_constant' must be uppercase
```
- **Prevents incorrect class attributes** from being created.  

---

## Metaclasses vs. Class Decorators  

| Feature | Metaclass | Class Decorator |
|---------|-----------|----------------|
| Controls class creation? | Yes | No |
| Works on methods/attributes? | Yes | Yes |
| Affects instances? | Yes | No |
| Applied to multiple classes? | Yes | Yes |
| Complexity | High | Low |

If you only need to modify methods, **use a class decorator**. If you want **deep control over class creation**, **use a metaclass**.

---

## Key Takeaways  

- **Metaclasses define how classes are created.**  
- **`type()` is the default metaclass.**  
- **You can dynamically create classes using `type()`.**  
- **Custom metaclasses can enforce rules and modify class behavior.**  
- **Use metaclasses only when necessary – they add complexity.**  
