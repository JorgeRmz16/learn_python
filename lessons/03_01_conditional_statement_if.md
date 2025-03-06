# 3.1 **Conditional Statements in Python (`if`, `elif`, `else`)**  

Conditional statements are fundamental to programming, allowing a program to make decisions based on conditions.  

---

## **3.1.1. Basic Syntax of Conditional Statements**  

A **conditional statement** executes a block of code only if a specified condition is `True`.  

### **Basic `if` Statement**  
```python
age = 18
if age >= 18:
    print("You are an adult.")
```
**Key Points:**  
- The **condition (`age >= 18`)** is evaluated.  
- If **True**, the indented block runs.  
- If **False**, nothing happens.

---

### **`if-else` Statement**  
```python
age = 16
if age >= 18:
    print("You are an adult.")
else:
    print("You are a minor.")
```
**Key Points:**  
- The **`else` block** runs only if the condition in `if` is `False`.  
- Ensures there is always an **outcome**.

---

### **`if-elif-else` (Multiple Conditions)**  
```python
score = 85

if score >= 90:
    print("Grade: A")
elif score >= 80:
    print("Grade: B")
elif score >= 70:
    print("Grade: C")
else:
    print("Grade: F")
```
**Key Points:**  
- The first `True` condition executes.  
- The remaining conditions are skipped once a match is found.  
- Conditions must be arranged logically.

---

## **3.1.2. Comparison Operators in Conditions**  
Conditional statements use **comparison operators** to evaluate conditions.

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `==` | Equal to | `5 == 5` | `True` |
| `!=` | Not equal to | `5 != 3` | `True` |
| `>` | Greater than | `10 > 3` | `True` |
| `<` | Less than | `4 < 8` | `True` |
| `>=` | Greater than or equal to | `7 >= 7` | `True` |
| `<=` | Less than or equal to | `2 <= 5` | `True` |

---

## **3.1.3. Logical Operators in Conditions**  
Logical operators **combine multiple conditions**.

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `and` | Both conditions must be `True` | `x > 5 and x < 10` | `True` if `x = 7` |
| `or` | At least one condition must be `True` | `x < 5 or x > 15` | `True` if `x = 2` |
| `not` | Negates a condition | `not(x > 5)` | `True` if `x = 3` |

---

## **3.1.4. Nested Conditionals**  
### **Using an `if` Inside Another `if`**
```python
age = 20
has_ID = True

if age >= 18:
    if has_ID:
        print("You can enter.")
    else:
        print("You need an ID.")
else:
    print("You are underage.")
```
- **When to Use?** : When checking **multiple dependent conditions**.  
- Too many nested `if` statements can reduce **readability**.  
- **Alternative:** Use `and` to simplify conditions.
```python
if age >= 18 and has_ID:
    print("You can enter.")
else:
    print("You cannot enter.")
```

---

## **3.1.5. Conditional Expressions (Ternary Operator)**
Python provides a **shorter syntax** for simple `if-else` statements.

**Assigning a Value Conditionally**
```python
age = 20
status = "Adult" if age >= 18 else "Minor"
print(status)  # Output: Adult
```

**Printing Based on Condition**
```python
score = 75
print("Pass" if score >= 60 else "Fail")  # Output: Pass
```

- **When to Use?** : When assigning a value based on a condition.  
- **When Not to Use?** : When conditions involve **complex logic** (prefer full `if-else` blocks).

---

## **3.1.6. Using `match-case` (Python 3.10+)**
Python 3.10 introduced **`match-case`**, which acts like a **switch statement**.

```python
status_code = 404

match status_code:
    case 200:
        print("OK")
    case 404:
        print("Not Found")
    case 500:
        print("Server Error")
    case _:
        print("Unknown Status")
```
**Benefits of `match-case`**:  
- More readable than multiple `if-elif-else` chains.  
- **Faster execution** in some cases.  

---

## **3.1.7. Best Practices for Mastering Conditional Statements**
- Use `elif` instead of multiple `if` statements to improve efficiency.  
- Keep conditions simple and readable (avoid deep nesting).  
- Use logical operators (`and`, `or`, `not`) instead of multiple `if` statements.  
- Use ternary expressions (`x if condition else y`) for simple conditions.  
- Use `match-case` when checking multiple specific values (Python 3.10+).
- Always consider edge cases when writing conditions.  

---

# **3.1.8. Summary Table**
| Concept | Syntax Example | Use Case |
|---------|---------------|----------|
| Basic `if` | `if x > 0: print("Positive")` | Single condition check |
| `if-else` | `if x > 0: print("Positive") else: print("Negative")` | Two possible outcomes |
| `if-elif-else` | `if x > 0: print("A") elif x == 0: print("B") else: print("C")` | Multiple conditions |
| Logical `and` | `if x > 0 and y > 0:` | Both must be `True` |
| Logical `or` | `if x > 0 or y > 0:` | At least one `True` |
| Logical `not` | `if not x < 5:` | Negates the condition |
| Nested `if` | `if x > 0: if y > 0:` | Dependent conditions |
| Ternary Operator | `status = "Adult" if age >= 18 else "Minor"` | Short `if-else` expression |
| `match-case` | `match x: case 1: print("One")` | Multiple fixed-value conditions |
