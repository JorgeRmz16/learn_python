# **6.3. Defining Custom Exceptions**   

In Python, built-in exceptions like `ValueError`, `TypeError`, and `IndexError` help handle common errors. However, for complex applications, **defining custom exceptions** provides more clarity, better debugging, and modular error handling.  


### Why Define Custom Exceptions?  

- **More meaningful error messages**: Instead of a generic `ValueError`, a `NegativeNumberError` clearly indicates the issue.  
- **Better debugging and maintenance**: Custom exceptions help categorize errors logically.  
- **Allows structured error handling**: Developers can catch specific issues more effectively.  

---

## 6.3.1 Creating a Custom Exception Class  

A custom exception is a **subclass of Python’s built-in `Exception` class**.  

### **Basic Structure**  
```python
class CustomError(Exception):
    """Custom Exception Example"""
    pass
```
This defines `CustomError`, which behaves like any other Python exception but is **specific to our application**.

**Example: Raising a Custom Exception**  
```python
class NegativeNumberError(Exception):
    """Exception raised when a negative number is encountered."""
    pass

def check_positive_number(n):
    if n < 0:
        raise NegativeNumberError("Negative numbers are not allowed!")
    return n

try:
    check_positive_number(-5)
except NegativeNumberError as e:
    print(f"Error: {e}")

""" Output:  
Error: Negative numbers are not allowed!
"""
```

---

## 6.3.2 Adding More Information to a Custom Exception  

We can customize the exception further by **overriding the `__init__` method** to accept additional arguments.  

```python
class InvalidAgeError(Exception):
    """Raised when age is below the required minimum."""
    def __init__(self, age, message="Age must be 18 or older."):
        self.age = age
        self.message = message
        super().__init__(f"{message} Provided: {age}")

def validate_age(age):
    if age < 18:
        raise InvalidAgeError(age)

try:
    validate_age(16)
except InvalidAgeError as e:
    print(e)

""" Output:  
Age must be 18 or older. Provided: 16
"""
```
Here, `InvalidAgeError` stores the invalid age and provides a **detailed message**.

---

## 6.3.3. Creating a Hierarchy of Custom Exceptions1  

For large applications, **grouping related exceptions** into a hierarchy improves organization.  

```python
class AccountError(Exception):
    """Base class for account-related errors."""
    pass

class InsufficientFundsError(AccountError):
    """Raised when withdrawal exceeds balance."""
    def __init__(self, balance, amount):
        super().__init__(f"Insufficient funds! Balance: ${balance}, Withdrawal: ${amount}")

class InvalidTransactionError(AccountError):
    """Raised for an invalid transaction."""
    pass

def withdraw(balance, amount):
    if amount > balance:
        raise InsufficientFundsError(balance, amount)
    return balance - amount

try:
    withdraw(100, 200)  # Trying to withdraw more than balance
except AccountError as e:
    print(e)

""" Output:  
Insufficient funds! Balance: $100, Withdrawal: $200
"""
```
**Why use hierarchy?**  
- `AccountError` serves as a **base class**, allowing us to catch **all account-related errors** with `except AccountError`.  
- **More specialized exceptions (`InsufficientFundsError`, `InvalidTransactionError`) allow fine-grained handling.**  

---

## 6.3.4. Raising Custom Exceptions in Real-World Scenarios  

### 6.3.4.1. Validating User Input  
```python
class EmptyInputError(Exception):
    """Raised when user input is empty."""
    pass

def get_username(name):
    if not name.strip():
        raise EmptyInputError("Username cannot be empty!")
    return name

try:
    get_username("   ")
except EmptyInputError as e:
    print(e)

""" Output:  
Username cannot be empty!
"""
```

### 6.3.4.2. Handling API Response Errors  
```python
class APIError(Exception):
    """Raised when API returns an error response."""
    def __init__(self, status_code, message="API request failed"):
        self.status_code = status_code
        super().__init__(f"{message}. Status Code: {status_code}")

def fetch_data():
    response_code = 500  # Simulating an error
    if response_code != 200:
        raise APIError(response_code)

try:
    fetch_data()
except APIError as e:
    print(e)

""" Output:  
API request failed. Status Code: 500
"""
```

---

# **Key Takeaways**
- **Custom exceptions** improve error clarity and debugging.  
- **Extend `Exception`** when creating custom exceptions.  
- **Add attributes (`__init__`)** to store extra information.  
- **Use exception hierarchies** for structured error handling.  
- **Raise exceptions in real-world scenarios** like input validation and API handling.  

