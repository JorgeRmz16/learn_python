# **8. Functional Programming in Python**  

Python supports **functional programming**, a paradigm where functions are treated as first-class citizens, emphasizing **pure functions**, **immutability**, and **higher-order functions**.

---

# 8.1. Pure Functions and Immutability  
**Pure functions** always produce the same output for the same input and have no side effects. **Immutability** ensures that data remains unchanged after it is created.

### Characteristics of Pure Functions  
A function is **pure** if:
1. It **always returns the same result** for the same input.
2. It **does not modify global variables or external states**.
3. It **has no side effects** (e.g., modifying a list, printing output, or changing a database).

#### Example of a Pure Function  
```python
# Pure function: No side effects, same output for the same input

def add(a, b):
    return a + b

print(add(3, 5))  # Output: 8
print(add(3, 5))  # Output: 8 (Same input, same output)
```
- The function **only depends on its input arguments**.
- It does **not modify any external variables**.

#### Example of an Impure Function  
```python
# Impure function: Modifies external variable (side effect)

total = 0

def add_impure(a):
    global total
    total += a  # Modifies global state
    return total

print(add_impure(5))  # Output: 5
print(add_impure(5))  # Output: 10 (Different result for the same input)
```
- The function modifies the **global variable `total`**, making it impure.
- The output **depends on external state**, so it is **not predictable**.

---

## Immutability in Python  
**Immutability** means that **data cannot be changed after it is created**.

### Immutable Data Types in Python  
| Data Type | Immutable? |
|-----------|------------|
| `int` | Yes |
| `float` | Yes |
| `str` | Yes |
| `tuple` | Yes |
| `list` | No |
| `dict` | No |
| `set` | No |

#### Example: Immutable Strings  
```python
name = "Alice"
name[0] = "M"  # Error: Strings are immutable
```
- Strings **cannot be modified** after creation.

#### Example: Immutable Tuples  
```python
tuple_data = (1, 2, 3)
tuple_data[0] = 10  # Error: Tuples are immutable
```
- **Tuples cannot be changed**, unlike lists.

#### Example: Avoiding Mutation with Lists  
```python
def add_element(lst, element):
    return lst + [element]  # Returns a new list instead of modifying original

my_list = [1, 2, 3]
new_list = add_element(my_list, 4)
print(my_list)   # Output: [1, 2, 3] (Original list unchanged)
print(new_list)  # Output: [1, 2, 3, 4] (New list created)
```
- Instead of modifying the original list, **a new list is created**.

---

## Key Takeaways  
| Concept | Explanation |
|---------|-------------|
| **Pure Functions** | Always return the same output for the same input, without side effects. |
| **Impure Functions** | Depend on or modify external state, making them unpredictable. |
| **Immutability** | Data structures cannot be changed after creation. |
| **Benefits** | Easier debugging, better concurrency, and predictable behavior. |

