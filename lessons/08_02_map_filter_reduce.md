# 8.2. Using `map()`, `filter()`, and `reduce()`

Python provides built-in functions for functional programming: **`map()`**, **`filter()`**, and **`reduce()`** (from `functools`). These functions enable efficient data transformation and selection in a functional style.

### `map()` – Applying a Function to Each Element  
`map()` applies a function to each item in an iterable and returns a new iterable.  

```python
# Function to square a number
def square(x):
    return x * x

numbers = [1, 2, 3, 4]
squared_numbers = list(map(square, numbers))  # Applying square() to each number

print(squared_numbers)  # Output: [1, 4, 9, 16]
```
- `map(square, numbers)` applies `square()` to each element in `numbers`.
- The result is converted to a list for display.

---

### `filter()` – Selecting Elements Based on a Condition  
`filter()` keeps only the elements that satisfy a given condition.  

```python
# Function to check if a number is even
def is_even(x):
    return x % 2 == 0

numbers = [1, 2, 3, 4, 5, 6]
even_numbers = list(filter(is_even, numbers))  # Keeps only even numbers

print(even_numbers)  # Output: [2, 4, 6]
```
- `filter(is_even, numbers)` retains elements for which `is_even(x)` returns `True`.

---

### `reduce()` – Cumulative Computation  
`reduce()` from the `functools` module **reduces** an iterable to a single value by applying a function cumulatively.  

```python
from functools import reduce

# Function to multiply two numbers
def multiply(a, b):
    return a * b

numbers = [1, 2, 3, 4]
product = reduce(multiply, numbers)  # Multiplies all numbers together

print(product)  # Output: 24
```
- `reduce(multiply, numbers)` applies `multiply()` cumulatively: `((1*2)*3)*4 = 24`.
- Useful for **aggregation operations** like sum, product, or finding the maximum value.

---

## Key Takeaways  
| Function | Purpose |
|----------|---------|
| **`map()`** | Transforms elements using a function. |
| **`filter()`** | Selects elements based on a condition. |
| **`reduce()`** | Reduces elements to a single value using a function. |

