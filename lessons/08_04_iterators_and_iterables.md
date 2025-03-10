# **8.4. Iterators and Iterables**  

Are fundamental concepts in Python that enable efficient looping over data structures. Understanding these concepts is crucial for writing clean, Pythonic code.

---

## 8.4.1. Iterables
An iterable is any Python object capable of returning its elements one at a time. Common iterables include lists, tuples, sets, dictionaries, and strings.

#### **Basic Syntax:**
```python
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    print(num)
```
Here, `numbers` is an iterable, and the `for` loop implicitly retrieves its elements.

#### **Checking if an Object is Iterable:**
```python
from collections.abc import Iterable
print(isinstance(numbers, Iterable))  # Output: True
```
The `Iterable` class helps verify if an object supports iteration.

---

## 8.4.2. Iterators
An iterator is an object that represents a stream of data. It implements two special methods:
- `__iter__()`: Returns the iterator object itself.
- `__next__()`: Returns the next element or raises `StopIteration` if no elements remain.

**Creating an Iterator from an Iterable:**
```python
numbers = [1, 2, 3]
iterator = iter(numbers)
print(next(iterator))  # Output: 1
print(next(iterator))  # Output: 2
print(next(iterator))  # Output: 3
# next(iterator)  # Raises StopIteration
```
Using `iter()`, we obtain an iterator that we can manually iterate using `next()`.

#### **Building a Custom Iterator:**
```python
class Counter:
    def __init__(self, start, end):
        self.current = start
        self.end = end
    
    def __iter__(self):
        return self  # The iterator itself
    
    def __next__(self):
        if self.current > self.end:
            raise StopIteration
        self.current += 1
        return self.current - 1

counter = Counter(1, 3)
for num in counter:
    print(num)
# Output: 1, 2, 3
```
This class behaves like a range generator.

---

### Generator Functions (Lazy Iterators)
Generators simplify iterator creation using `yield`. Unlike lists, generators produce values lazily, conserving memory.

**Simple Generator**
```python
def count_up_to(n):
    count = 1
    while count <= n:
        yield count
        count += 1

for num in count_up_to(3):
    print(num)
```
`yield` suspends execution and resumes when `next()` is called.

**Infinite Generator**
```python
def infinite_counter():
    num = 1
    while True:
        yield num
        num += 1

counter = infinite_counter()
print(next(counter))  # Output: 1
print(next(counter))  # Output: 2
```
This generator runs indefinitely unless explicitly stopped.

---

### **Key Takeaways**
| Concept | Description |
|---------|-------------|
| **Iterable** | An object capable of returning its elements one at a time. |
| **Iterator** | An object that implements `__iter__()` and `__next__()`. |
| **Generators** | Functions using `yield` to produce values lazily. |
| **StopIteration** | Exception raised when an iterator runs out of elements. |

