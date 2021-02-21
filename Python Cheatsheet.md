# Python Cheat Sheet

### Comments

`# this is a comment`

## Variables

### Names

- No declaration is required
- Case sensitive
- Allowed characters A-z, 0-9, and \_
- Cannot start with a number

Set multiple variables: `x = y = z = 3.14`  
Set multiple different variables: `x, y, z = 1.1, 2.2, 3.3`

### Scope

A variable will be global if created outside of functions. Inside a function it will be read-only.

```python
x = 3   # x is global
def myfunc():
  print(x)  # x is read only inside the function
```

If a variable of the same name is set/written inside the function, they will be two independent variables:

```python
x = 3   # This x is global
def myfunc():
  x = 5  # This x is a separate local variable
```

To write to a global variable from within a function, the `global` keyword must be used:

```python
x = 3   # x is global
def myfunc():
  global x
  x = 5  # Write to the same global x
```

### Types

Get variable type using `type(x)`. Returns a string of the form `"<class 'float'>"`  
Cast, convert, or initialize a variable to a specific type using `x = float(i)`, for example

|          | Types        | Examples                                        |
| -------- | ------------ | ----------------------------------------------- |
| Numeric  | `int`        | `i = 21`                                        |
|          | `float`      | `x = 3.24` or `x = -4.5e-19`                    |
|          | `complex`    | `z = 2.3+5.2j`                                  |
| String   | `str`        | `s = "Double quotes"` or `s = 'Single quotes'`  |
| Boolean  | `bool`       | `b = True`                                      |
| Sequence | `list`       | `L = [2,5,4] `                                  |
|          | `tuple`      | `t = ("a", "b", "c")`                           |
|          | `range`      | `r = range(6)`                                  |
| Map      | `dict`       | `d = {"name" : "John", "age" : 36}`             |
| Set      | `set`        | `s = {"apple", "banana", "cherry"}`             |
|          | `frozenset`  | `fs = frozenset({"apple", "banana", "cherry"})` |
| Binary   | `bytes`      | `c = b"Hello"`                                  |
|          | `bytearray`  | `ba = bytearray(6)`                             |
|          | `memoryview` | `mv = memoryview(bytes(6)) `                    |

## Operators

| Type           | Operator | Operation        | Example |
| -------------- | -------- | ---------------- | ------- |
| **Arithmetic** | \*\*     | Exponentiation   |         |
|                | %        | Modulus          |         |
|                | //       | Integer division |         |
|                | /        | Division         |         |
|                | \*       | Multiplication   |         |
|                | -        | Subtraction      |         |
| **Boolean**    | and      | Logical AND      |         |
|                | or       | Logical OR       |         |
|                | not      | Logical NOT      |         |
| **Comparison** |          |                  |         |
|                |          |                  |         |
|                |          |                  |         |
| **Identity**   |          |                  |         |
|                |          |                  |         |
| **Membership** |          |                  |         |
| **Bitwise**    |          |                  |         |
|                |          |                  |         |

### Strings

- Strings are zero-based arrays. s[0] is the first character
- Negative indexes wrap to the end of the string. Eg. s[-1] is the last character

| Type               | Example | Description/Return              |
| ------------------ | ------- | ------------------------------- |
| Length             | len(s)  | Length of string                |
| Access character   | s[4]    | Character at index 4            |
|                    | s[-2]   | Second to last character        |
| Slice substring    | s[2:5]  | Substring from index 2 to 4     |
|                    | s[2:]   | Substring from index 2 to end   |
|                    | s[:5]   | Substring from start to index 4 |
| Test for substring | s1 in s | True, if s1 is a substring of s |
|                    | s1 in s | True, if s1 is a substring of s |
|                    | s1 in s | True, if s1 is a substring of s |
| Concatenate        | s1 + s2 | Concatenates s1 and s2          |

## Functions

### Define a function:

```python
def print_sum(x, y):
  print(x+y)

print_sum(2,3)  # --> "5"
```

### Return a value

Use the `return` keyword

```python
def sum(x, y):
  return x+y

z = sum(3,4)   # --> z = 7
```

### Default parameter values

Set defaults in case an argument is not supplied

```python
def rotate(angle = 180):
  print("Turn to " + angle)

rotate()    # --> "Turn to 180"  (No argument, use default)
rotate(30)  # --> "Turn to 30"
```

### Accept a variable number of parameters

```python
def process(*argTuple):
  print(argTuple[1])  # Print the 2rd argument

process("a", "b", "c")  # Prints --> "b"
```

### Call with explicit keyword arguments

So parameter order doesn't matter

```python
def make_vector(length, angle):
    # do stuff here

make_vector(length = 3.2, angle = 3.14)  # Call with keywords.  Parameter order doesn't matter
```
