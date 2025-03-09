# **2.3 Arithmetic, Logical, and Comparison Operators**  

Operators are special symbols in Python that **perform operations on variables and values**.  
Python supports different types of operators, including:  
- **Arithmetic Operators** - Perform mathematical calculations  
- **Comparison (Relational) Operators** - Compare values  
- **Logical Operators** - Combine conditions  

---

## 2.3.2. Arithmetic Operators 
These operators perform **basic mathematical operations**.  

| **Operator** | **Symbol** | **Example** | **Output** |
|-------------|-----------|-------------|------------|
| Addition | `+` | `5 + 3` | `8` |
| Subtraction | `-` | `10 - 4` | `6` |
| Multiplication | `*` | `7 * 3` | `21` |
| Division | `/` | `10 / 2` | `5.0` (always float) |
| Floor Division | `//` | `10 // 3` | `3` (integer division) |
| Modulus (Remainder) | `%` | `10 % 3` | `1` |
| Exponentiation | `**` | `2 ** 3` | `8` |

### **Examples**
```python
a = 10
b = 3

print(a + b)  # Output: 13
print(a - b)  # Output: 7
print(a * b)  # Output: 30
print(a / b)  # Output: 3.333...
print(a // b) # Output: 3
print(a % b)  # Output: 1
print(a ** b) # Output: 1000
```
---
## 2.3.3. Comparison (Relational) Operators
Comparison operators **compare two values** and return a **Boolean (True/False)**.

| **Operator** | **Symbol** | **Example** | **Output** |
|-------------|-----------|-------------|------------|
| Equal to | `==` | `5 == 5` | `True` |
| Not equal to | `!=` | `5 != 3` | `True` |
| Greater than | `>` | `10 > 3` | `True` |
| Less than | `<` | `2 < 5` | `True` |
| Greater than or equal to | `>=` | `10 >= 10` | `True` |
| Less than or equal to | `<=` | `4 <= 6` | `True` |


### Examples
```python
x = 7
y = 10

print(x == y)  # Output: False
print(x != y)  # Output: True
print(x > y)   # Output: False
print(x < y)   # Output: True
print(x >= y)  # Output: False
print(x <= y)  # Output: True
print("hello" == "Hello") #False (String comparison is case-sensitive)
```
---
## 2.3.4. Logical Operators
Logical operators are used to **combine multiple conditions**.

| **Operator** | **Symbol** | **Description** |
|-------------|-----------|----------------|
| Logical AND | `and` | Returns `True` if both conditions are `True` |
| Logical OR | `or` | Returns `True` if at least one condition is `True` |
| Logical NOT | `not` | Reverses the boolean value |

### Examples
```python
a = True
b = False

print(a and b)  # Output: False
print(a or b)   # Output: True
print(not a)    # Output: False
```

### **Combining Logical and Comparison Operators**
```python
x = 10
y = 20

print(x > 5 and y < 30)  # Output: True
print(x > 15 or y < 30)  # Output: True
print(not (x > 5))       # Output: False
```

---

## 2.3.5. Operator Precedence
Operator precedence determines the **order of operations**.  

| **Operator** | **Description** | **Precedence** |
|-------------|----------------|---------------|
| `**` | Exponentiation | Highest |
| `*`, `/`, `//`, `%` | Multiplication, Division, Modulus | High |
| `+`, `-` | Addition, Subtraction | Medium |
| `<, >, <=, >=, ==, !=` | Comparison Operators | Lower |
| `not` | Logical NOT | Lower |
| `and` | Logical AND | Very Low |
| `or` | Logical OR | Lowest |

Example:
```python
result = 5 + 2 * 3 ** 2  # 5 + (2 * (3 ** 2)) = 5 + 18 = 23
print(result)  # Output: 23
```

Use **parentheses** to control precedence:
```python
result = (5 + 2) * 3 ** 2  # (7 * 9) = 63
print(result)  # Output: 63
```

---

## 2.3.6. Augmented Assignment Operators
These **combine an arithmetic operation with assignment**.

| **Operator** | **Example** | **Equivalent to** |
|-------------|------------|----------------|
| `+=` | `x += 2` | `x = x + 2` |
| `-=` | `x -= 2` | `x = x - 2` |
| `*=` | `x *= 2` | `x = x * 2` |
| `/=` | `x /= 2` | `x = x / 2` |
| `//=` | `x //= 2` | `x = x // 2` |
| `%=` | `x %= 2` | `x = x % 2` |
| `**=` | `x **= 2` | `x = x ** 2` |

Example:
```python
x = 10
x += 5  # Equivalent to x = x + 5
print(x)  # Output: 15
```

---

Here’s a summary table covering all the key points from your content:  

### 5.3.7. Summary  

| **Category** | **Operators** | **Description** | **Example** | **Output** |
|-------------|-------------|----------------|-------------|------------|
| **Arithmetic** | `+`, `-`, `*`, `/` | Basic math operations | `5 + 3` | `8` |
|  | `//` | Floor division (integer result) | `10 // 3` | `3` |
|  | `%` | Modulus (remainder) | `10 % 3` | `1` |
|  | `**` | Exponentiation | `2 ** 3` | `8` |
| **Comparison** | `==` | Equal to | `5 == 5` | `True` |
|  | `!=` | Not equal to | `5 != 3` | `True` |
|  | `>` | Greater than | `10 > 3` | `True` |
|  | `<` | Less than | `2 < 5` | `True` |
|  | `>=` | Greater than or equal to | `10 >= 10` | `True` |
|  | `<=` | Less than or equal to | `4 <= 6` | `True` |
| **Logical** | `and` | True if both conditions are True | `True and False` | `False` |
|  | `or` | True if at least one condition is True | `True or False` | `True` |
|  | `not` | Reverses Boolean value | `not True` | `False` |
| **Operator Precedence** | `**` | Highest precedence | `2 ** 3 * 2` | `16` |
|  | `*`, `/`, `//`, `%` | High precedence | `10 / 2 + 3` | `8.0` |
|  | `+`, `-` | Medium precedence | `5 + 2 * 3` | `11` |
|  | Comparison (`==, <, >, <=, >=`) | Lower precedence | `3 > 2 and 5 < 10` | `True` |
|  | `not` | Lower precedence | `not (5 > 3)` | `False` |
|  | `and` | Very low precedence | `True and False or True` | `True` |
|  | `or` | Lowest precedence | `False or True` | `True` |
| **Augmented Assignment** | `+=` | `x += 2` → `x = x + 2` | `x = 5; x += 3` | `8` |
|  | `-=` | `x -= 2` → `x = x - 2` | `x = 5; x -= 3` | `2` |
|  | `*=` | `x *= 2` → `x = x * 2` | `x = 5; x *= 3` | `15` |
|  | `/=` | `x /= 2` → `x = x / 2` | `x = 10; x /= 2` | `5.0` |
|  | `//=` | `x //= 2` → `x = x // 2` | `x = 10; x //= 3` | `3` |
|  | `%=` | `x %= 2` → `x = x % 2` | `x = 10; x %= 3` | `1` |
|  | `**=` | `x **= 2` → `x = x ** 2` | `x = 3; x **= 2` | `9` |
