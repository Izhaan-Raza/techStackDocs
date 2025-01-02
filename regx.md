# Python Regular Expressions (RegEx): Comprehensive Guide

Regular Expressions (RegEx) are sequences of characters defining search patterns. They are powerful tools for string matching and manipulation in Python, provided by the `re` module.

---
## Importing the `re` Module
```python
import re
```

---
## Common Functions in the `re` Module

### 1. `re.match()`
Matches a pattern at the beginning of the string.
```python
match = re.match(pattern, string)
```
#### Example:
```python
import re
result = re.match(r"hello", "hello world")
print(result.group())  # Output: hello
```

### 2. `re.search()`
Searches for the first occurrence of a pattern anywhere in the string.
```python
search = re.search(pattern, string)
```
#### Example:
```python
import re
result = re.search(r"world", "hello world")
print(result.group())  # Output: world
```

### 3. `re.findall()`
Finds all occurrences of a pattern in the string.
```python
all_matches = re.findall(pattern, string)
```
#### Example:
```python
import re
matches = re.findall(r"\d+", "Order numbers: 123, 456, 789")
print(matches)  # Output: ['123', '456', '789']
```

### 4. `re.finditer()`
Returns an iterator yielding match objects for all occurrences of a pattern.
```python
iterator = re.finditer(pattern, string)
```
#### Example:
```python
import re
iterator = re.finditer(r"\d+", "Order numbers: 123, 456, 789")
for match in iterator:
    print(match.group())
# Output:
# 123
# 456
# 789
```

### 5. `re.sub()`
Replaces occurrences of a pattern with a specified string.
```python
replaced_string = re.sub(pattern, replacement, string)
```
#### Example:
```python
import re
result = re.sub(r"\d+", "###", "Order numbers: 123, 456, 789")
print(result)  # Output: Order numbers: ###, ###, ###
```

### 6. `re.split()`
Splits the string by occurrences of the pattern.
```python
split_list = re.split(pattern, string)
```
#### Example:
```python
import re
result = re.split(r",", "apple,banana,cherry")
print(result)  # Output: ['apple', 'banana', 'cherry']
```

---
## Commonly Used Patterns

| Pattern  | Description                         |
|----------|-------------------------------------|
| `.`      | Matches any character (except \n).  |
| `\w`     | Matches any word character (alphanumeric + `_`). |
| `\W`     | Matches any non-word character.    |
| `\d`     | Matches any digit (0-9).           |
| `\D`     | Matches any non-digit.             |
| `\s`     | Matches any whitespace character.  |
| `\S`     | Matches any non-whitespace character. |
| `^`      | Matches the start of the string.    |
| `$`      | Matches the end of the string.      |
| `*`      | Matches 0 or more occurrences.      |
| `+`      | Matches 1 or more occurrences.      |
| `?`      | Matches 0 or 1 occurrence.          |
| `{n}`    | Matches exactly n occurrences.      |
| `{n,}`   | Matches n or more occurrences.      |
| `{n,m}`  | Matches between n and m occurrences.|
| `|`      | Matches either the left or right pattern. |
| `(...)`  | Groups patterns for capturing.      |

---
## Flags in Regular Expressions

| Flag          | Description                                      |
|---------------|--------------------------------------------------|
| `re.IGNORECASE` or `re.I` | Makes the pattern case-insensitive.       |
| `re.MULTILINE` or `re.M`  | Allows `^` and `$` to match start and end of each line. |
| `re.DOTALL` or `re.S`     | Makes `.` match newline characters as well. |
| `re.VERBOSE` or `re.X`    | Allows for comments and whitespace in the pattern for readability. |

#### Example:
```python
import re
pattern = r"hello world"
result = re.search(pattern, "Hello World", re.IGNORECASE)
print(result.group())  # Output: Hello World
```

---
## Advanced Examples

### Validate an Email Address
```python
import re
pattern = r"^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$"
email = "example@domain.com"
if re.match(pattern, email):
    print("Valid email")
else:
    print("Invalid email")
```

### Extract URLs from Text
```python
import re
text = "Visit https://example.com and http://domain.org for details."
pattern = r"https?://[\w.-]+"
urls = re.findall(pattern, text)
print(urls)  # Output: ['https://example.com', 'http://domain.org']
```

### Find and Replace Words with a Pattern
```python
import re
text = "The color is red."
pattern = r"color"
replacement = "colour"
result = re.sub(pattern, replacement, text)
print(result)  # Output: The colour is red.
```

---
## Best Practices

1. Always test your patterns with multiple test cases.
2. Use raw strings (`r""`) for patterns to avoid escaping backslashes unnecessarily.
3. Leverage flags to simplify your patterns and improve readability.
4. Use named groups for clarity in complex patterns.

#### Example with Named Groups:
```python
import re
pattern = r"(?P<area_code>\d{3})-(?P<number>\d{7})"
match = re.match(pattern, "123-4567890")
if match:
    print(match.group("area_code"))  # Output: 123
    print(match.group("number"))     # Output: 4567890
```

This guide covers essential aspects of working with regular expressions in Python. Feel free to experiment and tailor patterns to your specific needs!

