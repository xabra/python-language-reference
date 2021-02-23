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

**`global`** keyword gives a local variable write access to a global variable of the same name:

```python
x = 3   # x is global
def myfunc():
  global x
  x = 5  # Write to the same global x
```

**`nonlocal`** keyword similarly gives a variable in a nested function write access to a variable in an enclosing function:

```python
def outer():
    x = "A"   # Set x in the outer function
    def inner():
        nonlocal x  # Give write access to x in the outer function
        x = "B"   # Over-writes x set in the outer function
    inner()   # Call inner()
    print(x)  # Output x

outer()   # Call outer() --> 'B'
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

### Built-in Constants

`True` is boolean true  
`False` is boolean true  
`None` is a null value

## Operators

| Type           | Operator | Operation                |     | Type           | Operator | Operation           |
| -------------- | -------- | ------------------------ | --- | -------------- | -------- | ------------------- |
| **Arithmetic** | `**`     | Exponentiation\*         |     | **Comparison** | `==`     | Equals              |
|                | `%`      | Modulus\*                |     |                | `!=`     | Not Equal           |
|                | `//`     | Integer division\*       |     |                | `>`      | Greater             |
|                | `/`      | Division\*               |     |                | `<`      | Less                |
|                | `*`      | Multiplication\*         |     |                | `>=`     | Greater or equal    |
|                | `-`      | Subtraction\*            |     |                | `<=`     | Less or equal       |
|                | `+`      | Addition\*               |     | **Identity**   | `is`     | Is same object      |
| **Assignment** | `=`      | Assign/Equals            |     |                | `is not` | Is not same object  |
| **Boolean**    | `and`    | Logical AND              |     | **Membership** | `in`     | Is contained in     |
|                | `or`     | Logical OR               |     |                | `not in` | Is not contained in |
|                | `not`    | Logical NOT              |     |                |          |                     |
| **Bitwise**    | `&`      | Bitwise AND\*            |     |                |          |                     |
|                | `\|`     | Bitwise OR\*             |     |                |          |                     |
|                | `^`      | Bitwise XOR\*            |     |                |          |                     |
|                | `~`      | Bitwise NOT\*            |     |                |          |                     |
|                | `<<`     | Shift left, zero fill\*  |     |                |          |                     |
|                | `>>`     | Shift right, zero fill\* |     |                |          |                     |

\*Arithmetic and bitwise operators have inline assignment versions where `a <op>= b` is equivalent to `a = a <op> b`

## Booleans

- Booleans evaluate to either `True` or `False`
- Cast an expression to a boolean value using `bool(expr)`
- Falsey boolean values include `False`, `None`, `0`, `""`, `()`, `[]`, `{}`. Casting any of these to `bool()` will return False

## Collections: Sequences, Sets & Dictionaries

- Sequences (Lists, Strings, Tuples) use zero-based indexes
- Negative indexes wrap to the end of the sequence. Eg. s[-1] is the last element

|                     | List              | String        | Tuple              | Set                            | Dictionary                  |
| ------------------- | ----------------- | ------------- | ------------------ | ------------------------------ | --------------------------- |
| Ordered             | ✔                 | ✔             | ✔                  | ❌                             | ❌                          |
| Mutable             | ✔                 | ❌            | ❌                 | ❌ (appendable)                | ✔                           |
| Duplicate Values    | ✔                 | ✔             | ✔                  | ❌                             | ✔                           |
| Constructor         | `a=list([1,2,3])` | `s=str("Hi")` | `t=tuple([1,2,3])` | `s=set([1,2,3])`               | `d=dict({"key" : "value"})` |
| Literal Constructor | `a=[1,2,3`]       | `s="Hi"`      | `t=(1,2,3)`        | `s={1,2,3}`                    | `d={"key" : "value"}`       |
| Element by index    | `a[2]`            | `s[2]`        | `t[2]`             | --                             | `d["key"]`                  |
| Slice               | `a[1:3]`          | `s[1:3]`      | `t[1:3]`           | --                             | --                          |
| Set element         | `a[2] = 3`        | --            | --                 | --                             | `d["key"] = "value"`        |
| Length              | `len(a)`          | `len(s)`      | `len(t)`           | `len(s)`                       | `len(d)`                    |
| Append Elements     |                   |               |                    | `.add(4)`or `.update([3,4,5])` | `d.newKey = "newVal"`       |
| Delete Elements     |                   |               |                    | .remove                        |                             |

### Slice Operations

```python
a[i]      # Return element at index i
a[-n]     # Return element n from end, where a[-1] is the last element
a[i:j]    # Return subsequence from i to j-1
a[i:]     # Return subsequence from i to end
a[:j]     # Return subsequence from start to j-1
a[:]      # Return a full copy
```

## Lists

- Lists are mutable

## Strings

- Strings are immutable
- String literals can use single or double quotes

### Multiline Strings

```python
a = """This is a
multiline string."""
```

### String Formatting

A string may contain replacement fields delimited by braces. Each field will be replaced by the value of an expression, formatted according to an optional format specifier:

```python
{ [argument_name | argument_index] : [format_spec] }
```

Format spec has the form:

```python
format_spec     ::=  [[fill]align][sign][#][0][width][grouping_option][.precision][type]
fill            ::=  <any character>
align           ::=  "<" | ">" | "=" | "^"
sign            ::=  "+" | "-" | " "
width           ::=  digit+
grouping_option ::=  "_" | ","
precision       ::=  digit+
type            ::=  "b" | "c" | "d" | "e" | "E" | "f" | "F" | "g" | "G" | "n" | "o" | "s" | "x" | "X" | "%"
```

See https://docs.python.org/3/library/string.html#formatstrings for details

### Formatted String Literal

```python
year = 2020
# Put f or F before a string literal.
s = F"Results for {year}" # Use {} to substitute in an expression
print(s)    # --> Results for 2020
```

### Using the _str.format()_ function

```python
"Values = {}, {}".format('a','b')         # By positional order --> 'Values = a, b'
"Values = {1}, {0}".format('a','b')       # By index --> 'Values = b, a'
"Values = {type}, {name}".format(name='a', type='b') # By name --> 'Values = b, a'
"Values = {: .3f}".format(3.14159)       # Float with minus, aligned, precision 3
```

### String Functions

| Function       | Description                                                                                   |
| -------------- | --------------------------------------------------------------------------------------------- |
| .capitalize()  | Converts the first character to upper case                                                    |
| .casefold()    | Converts string into lower case                                                               |
| .center()      | Returns a centered string                                                                     |
| count()        | Returns the number of times a specified value occurs in a string                              |
| encode()       | Returns an encoded version of the string                                                      |
| endswith()     | Returns true if the string ends with the specified value                                      |
| expandtabs()   | Sets the tab size of the string                                                               |
| find()         | Searches the string for a specified value and returns the position of where it was found      |
| format()       | Formats specified values in a string                                                          |
| format_map()   | Formats specified values in a string                                                          |
| index()        | Searches the string for a specified value and returns the position of where it was found      |
| isalnum()      | Returns True if all characters in the string are alphanumeric                                 |
| isalpha()      | Returns True if all characters in the string are in the alphabet                              |
| isdecimal()    | Returns True if all characters in the string are decimals                                     |
| isdigit()      | Returns True if all characters in the string are digits                                       |
| isidentifier() | Returns True if the string is an identifier                                                   |
| islower()      | Returns True if all characters in the string are lower case                                   |
| isnumeric()    | Returns True if all characters in the string are numeric                                      |
| isprintable()  | Returns True if all characters in the string are printable                                    |
| isspace()      | Returns True if all characters in the string are whitespaces                                  |
| istitle()      | Returns True if the string follows the rules of a title                                       |
| isupper()      | Returns True if all characters in the string are upper case                                   |
| join()         | Joins the elements of an iterable to the end of the string                                    |
| ljust()        | Returns a left justified version of the string                                                |
| lower()        | Converts a string into lower case                                                             |
| lstrip()       | Returns a left trim version of the string                                                     |
| maketrans()    | Returns a translation table to be used in translations                                        |
| partition()    | Returns a tuple where the string is parted into three parts                                   |
| replace()      | Returns a string where a specified value is replaced with a specified value                   |
| rfind()        | Searches the string for a specified value and returns the last position of where it was found |
| rindex()       | Searches the string for a specified value and returns the last position of where it was found |
| rjust()        | Returns a right justified version of the string                                               |
| rpartition()   | Returns a tuple where the string is parted into three parts                                   |
| rsplit()       | Splits the string at the specified separator, and returns a list                              |
| rstrip()       | Returns a right trim version of the string                                                    |
| split()        | Splits the string at the specified separator, and returns a list                              |
| splitlines()   | Splits the string at line breaks and returns a list                                           |
| startswith()   | Returns true if the string starts with the specified value                                    |
| strip()        | Returns a trimmed version of the string                                                       |
| swapcase()     | Swaps cases, lower case becomes upper case and vice versa                                     |
| title()        | Converts the first character of each word to upper case                                       |
| translate()    | Returns a translated string                                                                   |
| upper()        | Converts a string into upper case                                                             |
| zfill()        | Fills the string with a specified number of 0 values at the beginning                         |

## Tuples

- Tuples are immutable

## Sets

- Python automatically deletes duplicate elements
- To create an empty set, use: `s = set(())`. Don't use `s = {}`

| Set Operation        | Code                                       | Returned Set                 |
| -------------------- | ------------------------------------------ | ---------------------------- |
| Union                | `s1 \| s2` or `s1.union(s2)`               | All elements in both sets    |
| Intersection         | `s1 & s2` or `s1.intersection (s2)`        | Elements common to both sets |
| Difference           | `s1 - s2` or `s1.difference(s2)`           | Elements unique to s1        |
| Symmetric Difference | `s1 ^ s2` or `s1.symmetric_difference(s2)` | Elements unique to s1 or s2  |

## Dictionaries

- A dictionary
- To create an empty set, use: `s = set(())`. Don't use `s = {}`

## Functions

### Define a Function

```python
def print_sum(x, y):
  print(x+y)

print_sum(2,3)  # --> "5"
```

### Return a Value

Use the `return` keyword

```python
def sum(x, y):
  return x+y

z = sum(3,4)   # --> z = 7
```

### Argument Default Values

Set defaults in case an argument is not supplied

```python
def rotate(angle = 180):
  print("Turn to " + angle)

rotate()    # --> "Turn to 180"  (No argument, use default)
rotate(30)  # --> "Turn to 30"
```

### Variable Number of Arguments

```python
def process(*argTuple):
  print(argTuple[1])  # Print the 2rd argument

process("a", "b", "c")  # Prints --> "b"
```

### Named Arguments

Call any function using explicit argument names so parameter order doesn't matter

```python
def make_vector(length, angle):
    # do stuff here

make_vector(length = 3.2, angle = 3.14)  # Call with keywords.
```

### Lambda Functions

A lambda function is a small anonymous function: **lambda** _arguments_ : _expression_.  
Lambdas are useful for passing into higher-order functions such as map(), filter(), sort(), reduce()

```python
my_lambda_function = lambda arg1, arg2 : arg1 + 2*arg2    #  Define the lambda

my_lambda_function(2,3)   # Call it --> 8
```

## Conditionals

### if...elif...else

```python
if a > b:
  print(a)
elif a < b:   # Optional elif block
  print(b)
else:         # Optional else block
  print("equal")
```

### Short-hand

```python
if a > b: print("a > b")    # Inline if statement

print("a") if a > b else print("b")   # Ternary if-else statement
```

## Loops

### While Loop

```python
i = 1
while i < 10:
  print(i)
  i += 1
```

### For Loop

Iterates over a sequence: a list, tuple, dictionary, set, or string.

```python
names = ["tom", "sue", "bob"]
for name in names:
  print(name)
```

Use the `range()` function to generate a sequence:

```python
for x in range(1, 20, 3): # Sequence from 1 to 20 incrementing by 3
  print(x)
```

### Loop Termination

`break` exits the loop.  
`continue` starts the next iteration, short-circuiting the current interation  
`else:` runs a code block after the loop exits

## Classes and Objects

### Define a Class

```python
class MyClass:
   'Optional class documentation string'
   myClassVariable = 0 # variable shared with all class instances

   # Constructor function
   def __init__(self, myArg):  # self is required
      self.myInstanceVar = myArg    # Instance variable
      myClassVariable += 1  # Modify class variables, if needed

   # Define methods
   def myFunction(self, arg):
      # Do something here
```

### Create a New Object Instance

```python
myObject = MyClass(my_arg1) # Call the constructor using the class name.  The self argument is implicit
```

### Access Methods and Data with Dot Notation

```python
myObject.myFunction(arg)      # Call instance method. self is passed implicitly
x = myObject.myClassVariable  # Access class variable
myObject.myInstanceVariable   # Modify an instance variable (not private)
```

### Add new instance variables

```python
myObject.newVar = 30   # Modify an instance variable (not protected)
```

## Other Keywords

`pass` is a null operation, useful as a placeholder in the body of a function or a class:

```python
   def myPlaceholderFunction():
     pass   # Do nothing
```

`del` deletes a variable or object completely from the namespace:

```python
   del x
```

## Exceptions

### Standard Exceptions

- Python defines a set of standard exceptions: https://docs.python.org/3/library/exceptions.html
- Examples include `Exception()`, `TypeError()`, `ValueError()`, `SystemError()`, and many others.
- Python automatically raises exceptions of these types
- If not handled, exceptions will halt the code with a message

### Raise an Exception in Code

An exception can also be forcibly raised in code using `raise` _exceptionName ("custom message")_

```python
x = 10

if x > 5:
  raise Exception('x must be <= 5')  # Raise a generic exception

if type(x) != float:
  raise TypeError('Must be a float')  # Raise a standard TypeError() exception
```

### Handle Exceptions in a try-except-else-finally Block

```python
  try:
    # Code block to be tried.
  except TypeError():
    # Handle a specific exception type
  except:
    # Handle any other exception.  Default must be last
  else:
    # Run if no exceptions
  finally:
    # Run at the end in all cases, exception or not

```

## Modules & Packages

???????????

## Built-in Functions

?????????

## TODO

-- Finish Collections/Arrays/Iterators  
-- Add arguments to the table of string functions
