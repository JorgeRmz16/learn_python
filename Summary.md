## Data Types  
| Feature | Integer (`int`) | Float (`float`) | String (`str`) | Boolean (`bool`) |  
|---------|----------------|----------------|----------------|----------------|  
| Example | `10, -5, 0` | `3.14, -2.5, 1.2e3` | `"hello", 'Python'` | `True, False` |  
| Created With | Direct assignment | Direct assignment | Quotes (`'`, `"`, `''' """`) | `True` / `False` or comparisons |  
| Supports Arithmetic | yes| yes | `+`, `*` | Not |  
| Supports Indexing | Not | Not | Yes | Not |  
| Mutable | Not | Not | Not | Not |  
| Conversion | `int(x)` | `float(x)` | `str(x)` | `bool(x)` |


## Variables
| Feature | Description | Example |  
|---------|-------------|---------|  
| **Dynamically Typed** | No need to declare a type explicitly | `x = 10`, `y = "Hello"` |  
| **Case-Sensitive** | Variables `name` and `Name` are different | `age = 25`, `Age = 30` |  
| **Valid Characters** | Letters, digits (not first), underscores | `user_score = 100` |  
| **Invalid Characters** | Cannot start with a digit, no spaces, no special characters | `2cool = "Nope"`, `my var = "error"` |  
| **Best Practice** | Use `snake_case`, meaningful names | `total_price = 50.75` |  
| **Constants Convention** | Uppercase variable names | `PI = 3.14159` |  
| **Simple Assignment** | Assigning a value to a variable | `x = 5` |  
| **Multiple Assignment** | Assign multiple values at once | `a, b, c = 1, 2, 3` |  
| **Same Value Assignment** | Assign the same value to multiple variables | `x = y = z = 42` |  
| **Swapping Values** | Pythonic way to swap variables | `a, b = b, a` |  
| **Type Checking** | Identify variable type using `type()` | `print(type(x))` → `<class 'int'>` |  
| **Type Casting** | Convert between types | `int("100")`, `str(3.14)` |  

## Operators
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
| **Augmented Assignment** | `+=` | `x += 2` - `x = x + 2` | `x = 5; x += 3` | `8` |
|  | `-=` | `x -= 2` - `x = x - 2` | `x = 5; x -= 3` | `2` |
|  | `*=` | `x *= 2` - `x = x * 2` | `x = 5; x *= 3` | `15` |
|  | `/=` | `x /= 2` - `x = x / 2` | `x = 10; x /= 2` | `5.0` |
|  | `//=` | `x //= 2` - `x = x // 2` | `x = 10; x //= 3` | `3` |
|  | `%=` | `x %= 2` - `x = x % 2` | `x = 10; x %= 3` | `1` |
|  | `**=` | `x **= 2` - `x = x ** 2` | `x = 3; x **= 2` | `9` |

## String manipulation
| Feature | Description | Example | 
|---------|-------------|---------| 
| **Indexing** | Accessing individual characters using index | `word[0]` | `H` |  
| **Negative Indexing** | Access characters from the end using negative indices | `word[-1]` |  
| **Slicing** | Extracting substrings with `start:end:step` | `text[:6]` |   
| **Reversing Strings** | Using slicing with `[::-1]` | `text[::-1]` |   
| **Uppercase Conversion** | Convert all characters to uppercase | `text.upper()` | 
| **Lowercase Conversion** | Convert all characters to lowercase | `text.lower()` |
| **Capitalization** | Capitalize the first letter | `text.capitalize()` |
| **Title Case** | Capitalize first letter of each word | `text.title()` | 
| **Swap Case** | Swap uppercase/lowercase | `text.swapcase()` |
| **Check Alphanumeric** | Check if all characters are letters/numbers | `s.isalnum()` | 
| **Find Substring** | Get index of first occurrence | `text.find("fun")` |  
| **Count Substring** | Count occurrences of a substring | `text.count("Python")` |
| **Replace Substring** | Replace text | `text.replace("Python", "JavaScript")` |
| **Split String** | Convert string into a list | `sentence.split()` |
| **Join Strings** | Join list of words into a string | `"-".join(words)` |
| **Strip Whitespace** | Remove leading/trailing spaces | `text.strip()` | 
| **f-strings** | Format strings using `{}` | `f"My name is {name}"` |  
| **`.format()` Method** | Format strings with placeholders | `"Hello {}".format("Alice")` |  
| **Escape Sequences** | Insert special characters | `"Hello\nWorld"` |  
| **Raw Strings** | Ignore escape sequences | `r"C:\Users\Alice"` |  

## Collections
| Feature         | List []          | Tuple ()         | Set {}           | Dictionary {}      |
|----------------|---------------|---------------|---------------|-----------------|
| **Ordered**    | Yes         | Yes        | No        | Yes (keys)  |
| **Mutable**    | Yes         | No        | Yes        | Yes         |
| **Allows Duplicates** | Yes | Yes        | No        | Keys: No, Values: Yes |
| **Indexing & Slicing** | Yes | Yes       | No        | No (Keys instead) |
| **Use Case**   | Dynamic collections | Fixed data | Unique values | Key-value mapping |
| **Common Methods** | `append()`, `insert()`, `remove()`, `sort()` | `count()`, `index()` | `add()`, `remove()`, `union()` | `keys()`, `values()`, `items()` |

**List Comprehencions** -> [expression for item in iterable if condition]