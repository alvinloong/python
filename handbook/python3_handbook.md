# [Tutorial](https://docs.python.org/3/tutorial/index.html)

## [An Informal Introduction to Python](https://docs.python.org/3/tutorial/introduction.html)

```
# this is the first comment
spam = 1  # and this is the second comment
          # ... and now a third!
text = "# This is not a comment because it's inside quotes."
```

### [Using Python as a Calculator](https://docs.python.org/3/tutorial/introduction.html#using-python-as-a-calculator)

#### [Numbers](https://docs.python.org/3/tutorial/introduction.html#numbers)

```
>>> 1/2
0.5
>>> 2 + 2
4
>>> 50 - 5*6
20
>>> (50 - 5*6) / 4
5.0
>>> 8 / 5  # division always returns a floating point number
1.6
```

To do [floor division](https://docs.python.org/3/glossary.html#term-floor-division) and get an integer result (discarding any fractional result) you can use the `//` operator.

```
>>> 17 / 3  # classic division returns a float
5.666666666666667
>>>
>>> 17 // 3  # floor division discards the fractional part
5
>>> 17 % 3  # the % operator returns the remainder of the division
2
>>> 5 * 3 + 2  # result * divisor + remainder
17
```

the `**` operator to calculate powers.

Since `**` has higher precedence than `-`, `-3**2` will be interpreted as `-(3**2)` and thus result in `-9`. To avoid this and get `9`, you can use `(-3)**2`.

```
>>> -3**2
-9
>>> -(3**2)
-9
>>> (-3)**2
9
>>> 5 ** 2  # 5 squared
25
>>> 2 ** 7  # 2 to the power of 7
128
```

```
>>> width = 20
>>> height = 5 * 9
>>> width * height
900
```

```
>>> 4 * 3.75 - 1
14.0
```

In interactive mode, the last printed expression is assigned to the variable `_`. This means that when you are using Python as a desk calculator, it is somewhat easier to continue calculations, for example:

```
>>> tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
12.5625
>>> price + _
113.0625
>>> round(_, 2)
113.06
```

#### [Strings](https://docs.python.org/3/tutorial/introduction.html#strings)

```
>>> 'spam eggs'  # single quotes
'spam eggs'
>>> 'doesn\'t'  # use \' to escape the single quote...
"doesn't"
>>> "doesn't"  # ...or use double quotes instead
"doesn't"
>>> '"Yes," they said.'
'"Yes," they said.'
>>> "\"Yes,\" they said."
'"Yes," they said.'
>>> '"Isn\'t," they said.'
'"Isn\'t," they said.'
```

The [`print()`](https://docs.python.org/3/library/functions.html#print) function produces a more readable output, by omitting the enclosing quotes and by printing escaped and special characters.

Unlike other languages, special characters such as \n have the same meaning with both single ('...') and double ("...") quotes. The only difference between the two is that within single quotes you don’t need to escape " (but you have to escape \') and vice versa.

```
>>> '"Isn\'t," they said.'
'"Isn\'t," they said.'
>>> print('"Isn\'t," they said.')
"Isn't," they said.
>>> s = 'First line.\nSecond line.'  # \n means newline
>>> s  # without print(), \n is included in the output
'First line.\nSecond line.'
>>> print(s)  # with print(), \n produces a new line
First line.
Second line.
```

If you don’t want characters prefaced by `\` to be interpreted as special characters, you can use *raw strings* by adding an `r` before the first quote:

```
>>> print('C:\some\name')  # here \n means newline!
C:\some
ame
>>> print(r'C:\some\name')  # note the r before the quote
C:\some\name
```

String literals can span multiple lines. One way is using triple-quotes: `"""..."""` or `'''...'''`. End of lines are automatically included in the string, but it’s possible to prevent this by adding a `\` at the end of the line. The following example:

```
print("""\
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
""")
```

Strings can be concatenated (glued together) with the `+` operator, and repeated with `*`:

```
>>> # 3 times 'un', followed by 'ium'
>>> 3 * 'un' + 'ium'
'unununium'
```

Two or more *string literals* (i.e. the ones enclosed between quotes) next to each other are automatically concatenated.

```
>>> 'Py' 'thon'
'Python'
>>> 'Py''thon'
'Python'
>>> 'Py' "thon"
'Python'
>>> str='Py' 'thon'
>>> str
'Python'
>>> str='"Isn' "'" 't," they said.'
>>> print(str)
"Isn't," they said.
>>> str='"Isn'"'"'t," they said.'
>>> print(str)
"Isn't," they said.
```

This feature is particularly useful when you want to break long strings:

```
>>> text = ('Put several strings within parentheses '
...         'to have them joined together.')
>>> text
'Put several strings within parentheses to have them joined together.'
>>> ('Put several strings within parentheses '
...         'to have them joined together.')
'Put several strings within parentheses to have them joined together.'
```

This only works with two literals though, not with variables or expressions:

```
>>> prefix = 'Py'
>>> prefix 'thon'  # can't concatenate a variable and a string literal
  File "<stdin>", line 1
    prefix 'thon'
                ^
SyntaxError: invalid syntax
>>> ('un' * 3) 'ium'
  File "<stdin>", line 1
    ('un' * 3) 'ium'
                   ^
SyntaxError: invalid syntax
```

If you want to concatenate variables or a variable and a literal, use `+`:

```
>>> prefix + 'thon'
'Python'
```

Strings can be *indexed* (subscripted), with the first character having index 0. There is no separate character type; a character is simply a string of size one:

```
>>> word = 'Python'
>>> word[0]  # character in position 0
'P'
>>> word[5]  # character in position 5
'n'
```

Strings can be *indexed* (subscripted), with the first character having index 0. There is no separate character type; a character is simply a string of size one:

```
>>> word = 'Python'
>>> word[0]  # character in position 0
'P'
>>> word[5]  # character in position 5
'n'
```

Indices may also be negative numbers, to start counting from the right.

Note that since -0 is the same as 0, negative indices start from -1.

```
>>> word[-1]  # last character
'n'
>>> word[-2]  # second-last character
'o'
>>> word[-6]
'P'
>>> word[-0]
'P'
```

In addition to indexing, *slicing* is also supported. While indexing is used to obtain individual characters, *slicing* allows you to obtain substring:

```
>>> word[0:2]  # characters from position 0 (included) to 2 (excluded)
'Py'
>>> word[2:5]  # characters from position 2 (included) to 5 (excluded)
'tho'
```

**Note:**

word[m:n]  # starting from m, **(n-m) characters in total**.

Note how the start is always included, and the end always **excluded**. This makes sure that `s[:i] + s[i:]` is always equal to `s`:

```
>>> word[:2] + word[2:]
'Python'
>>> word[:4] + word[4:]
'Python'
```

Slice indices have useful defaults; an omitted first index defaults to zero, an omitted second index defaults to the size of the string being sliced.

```
>>> word[:2]   # character from the beginning to position 2 (excluded)
'Py'
>>> word[4:]   # characters from position 4 (included) to the end
'on'
>>> word[-2:]  # characters from the second-last (included) to the end
'on'
```

One way to remember how slices work is to think of the indices as pointing *between* characters, with the left edge of the first character numbered 0. Then the right edge of the last character of a string of *n* characters has index *n*, for example:

```
 +---+---+---+---+---+---+
 | P | y | t | h | o | n |
 +---+---+---+---+---+---+
 0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1
```

For non-negative indices, the length of a slice is the difference of the indices, if both are within bounds. For example, the length of `word[1:3]` is 2.

Attempting to use an index that is too large will result in an error:

```
>>> word[42]  # the word only has 6 characters
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range
```

However, out of range slice indexes are handled gracefully when used for slicing:

```
>>> word[4:42]
'on'
>>> word[42:]
''
>>> word[-2:5]
'o'
>>> word[-2:6]
'on'
>>> word[-2:7]
'on'
```

Python strings cannot be changed — they are [immutable](https://docs.python.org/3/glossary.html#term-immutable). Therefore, assigning to an indexed position in the string results in an error.

**Note**

[immutable](https://docs.python.org/3/glossary.html#term-immutable) - An object with a fixed value. Immutable objects include **numbers, strings and tuples.** Such an object cannot be altered. A new object has to be created if a different value has to be stored. 

```
>>> word[0] = 'J'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
>>> word[2:] = 'py'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
```

If you need a different string, you should create a new one:

```
>>> 'J' + word[1:]
'Jython'
>>> word[:2] + 'py'
'Pypy'
```

The built-in function [`len()`](https://docs.python.org/3/library/functions.html#len) returns the length of a string:

```
>>> s = 'supercalifragilisticexpialidocious'
>>> len(s)
34
```

See also

- [Text Sequence Type — str](https://docs.python.org/3/library/stdtypes.html#textseq)

  Strings are examples of *sequence types*, and support the common operations supported by such types.

- [String Methods](https://docs.python.org/3/library/stdtypes.html#string-methods)

  Strings support a large number of methods for basic transformations and searching.

- [Formatted string literals](https://docs.python.org/3/reference/lexical_analysis.html#f-strings)

  String literals that have embedded expressions.

- [Format String Syntax](https://docs.python.org/3/library/string.html#formatstrings)

  Information about string formatting with [`str.format()`](https://docs.python.org/3/library/stdtypes.html#str.format).

- [printf-style String Formatting](https://docs.python.org/3/library/stdtypes.html#old-string-formatting)

  The old formatting operations invoked when strings are the left operand of the `%` operator are described in more detail here.

#### [Lists](https://docs.python.org/3/tutorial/introduction.html#lists)

Lists might contain items of different types, but usually the items all have the same type.

```
>>> squares = [1, 4, 9, 16, 25]
>>> squares
[1, 4, 9, 16, 25]
```

Like strings (and all other built-in [sequence](https://docs.python.org/3/glossary.html#term-sequence) types), lists can be indexed and sliced:

```
>>> squares[0]  # indexing returns the item
1
>>> squares[-1]
25
>>> squares[-3:]  # slicing returns a new list
[9, 16, 25]
```

**Note:**

[sequence](https://docs.python.org/3/glossary.html#term-sequence) - An [iterable](https://docs.python.org/3/glossary.html#term-iterable) which supports efficient element access using integer indices via the [`__getitem__()`](https://docs.python.org/3/reference/datamodel.html#object.__getitem__) special method and defines a [`__len__()`](https://docs.python.org/3/reference/datamodel.html#object.__len__) method that returns the length of the sequence. Some built-in sequence types are [`list`](https://docs.python.org/3/library/stdtypes.html#list), [`str`](https://docs.python.org/3/library/stdtypes.html#str), [`tuple`](https://docs.python.org/3/library/stdtypes.html#tuple), and [`bytes`](https://docs.python.org/3/library/stdtypes.html#bytes). Note that [`dict`](https://docs.python.org/3/library/stdtypes.html#dict) also supports [`__getitem__()`](https://docs.python.org/3/reference/datamodel.html#object.__getitem__) and [`__len__()`](https://docs.python.org/3/reference/datamodel.html#object.__len__), but is considered a mapping rather than a sequence because the lookups use arbitrary [immutable](https://docs.python.org/3/glossary.html#term-immutable) keys rather than integers.

All slice operations return a new list containing the requested elements. This means that the following slice returns a [shallow copy](https://docs.python.org/3/library/copy.html#shallow-vs-deep-copy) of the list:

```
>>> squares[:]
[1, 4, 9, 16, 25]
```

Lists also support operations like concatenation:

```
>>> squares + [36, 49, 64, 81, 100]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

Unlike strings, which are [immutable](https://docs.python.org/3/glossary.html#term-immutable), lists are a [mutable](https://docs.python.org/3/glossary.html#term-mutable) type, i.e. it is possible to change their content:

```
>>> cubes = [1, 8, 27, 65, 125]  # something's wrong here
>>> 4 ** 3  # the cube of 4 is 64, not 65!
64
>>> cubes[3] = 64  # replace the wrong value
>>> cubes
[1, 8, 27, 64, 125]
```

Note:

```
>>> cubes[5] = 216
---------------------------------------------------------------------------
IndexError                                Traceback (most recent call last)
<ipython-input-71-32a497edfdfe> in <module>
----> 1 cubes[5] = 216

IndexError: list assignment index out of range

```

```
>>> cubes = cubes + [216]
>>> cubes
[1, 8, 27, 65, 125, 216]
```

You can also add new items at the end of the list, by using the `append()` *method* (we will see more about methods later):

```
>>> cubes.append(216)  # add the cube of 6
>>> cubes.append(7 ** 3)  # and the cube of 7
>>> cubes
[1, 8, 27, 64, 125, 216, 343]
```

Assignment to slices is also possible, and this can even change the size of the list or clear it entirely:

```
>>> letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> letters
['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> # replace some values
>>> letters[2:5] = ['C', 'D', 'E']
>>> letters
['a', 'b', 'C', 'D', 'E', 'f', 'g']
>>> # now remove them
>>> letters[2:5] = []
>>> letters
['a', 'b', 'f', 'g']
>>> # clear the list by replacing all the elements with an empty list
>>> letters[:] = []
>>> letters
[]
```

The built-in function [`len()`](https://docs.python.org/3/library/functions.html#len) also applies to lists:

```
>>> letters = ['a', 'b', 'c', 'd']
>>> len(letters)
4
```

It is possible to nest lists (create lists containing other lists), for example:

```
>>> a = ['a', 'b', 'c']
>>> n = [1, 2, 3]
>>> x = [a, n]
>>> x
[['a', 'b', 'c'], [1, 2, 3]]
>>> x[0]
['a', 'b', 'c']
>>> x[0][1]
'b'
```

### [First Steps Towards Programming](https://docs.python.org/3/tutorial/introduction.html#first-steps-towards-programming)

For instance, we can write an initial sub-sequence of the [Fibonacci series](https://en.wikipedia.org/wiki/Fibonacci_number) as follows:

```
>>> # Fibonacci series:
... # the sum of two elements defines the next
... a, b = 0, 1
>>> while a < 10:
...     print(a)
...     a, b = b, a+b
...
0
1
1
2
3
5
8
```

This example introduces several new features.

- The first line contains a *multiple assignment*: the variables `a` and `b` simultaneously get the new values 0 and 1. On the last line this is used again, demonstrating that **the expressions on the right-hand side are all evaluated first before any of the assignments take place**. The right-hand side expressions are evaluated from the left to the right.

- The [`while`](https://docs.python.org/3/reference/compound_stmts.html#while) loop executes as long as the condition (here: `a < 10`) remains true. In Python, like in C, **any non-zero integer value is true; zero is false.** **The condition may also be a string or list value, in fact any sequence; anything with a non-zero length is true, empty sequences are false.** The test used in the example is a simple comparison. The standard comparison operators are written the same as in C: `<` (less than), `>` (greater than), `==` (equal to), `<=` (less than or equal to), `>=` (greater than or equal to) and `!=` (not equal to).

- The *body* of the loop is *indented*: indentation is Python’s way of grouping statements. At the interactive prompt, you have to type a tab or space(s) for each indented line. In practice you will prepare more complicated input for Python with a text editor; all decent text editors have an auto-indent facility. When a compound statement is entered interactively, **it must be followed by a blank line to indicate completion** (since the parser cannot guess when you have typed the last line). Note that each line within a basic block must be indented by the same amount.

- The [`print()`](https://docs.python.org/3/library/functions.html#print) function writes the value of the argument(s) it is given. It differs from just writing the expression you want to write (as we did earlier in the calculator examples) in the way it handles multiple arguments, floating point quantities, and strings. Strings are printed without quotes, and a space is inserted between items, so you can format things nicely, like this:

  ```
  >>> i = 256*256
  >>> print('The value of i is', i)
  The value of i is 65536
  ```

  The keyword argument *end* can be used to avoid the newline after the output, or end the output with a different string:

  ```
  >>> a, b = 0, 1
  >>> while a < 1000:
  ...     print(a, end=',')
  ...     a, b = b, a+b
  ...
  0,1,1,2,3,5,8,13,21,34,55,89,144,233,377,610,987,
  ```

## [More Control Flow Tools](https://docs.python.org/3/tutorial/controlflow.html)

### [`if` Statements](https://docs.python.org/3/tutorial/controlflow.html#if-statements)

```
>>> x = int(input("Please enter an integer: "))
Please enter an integer: 42
>>> if x < 0:
...     x = 0
...     print('Negative changed to zero')
... elif x == 0:
...     print('Zero')
... elif x == 1:
...     print('Single')
... else:
...     print('More')
...
More
```

### [`for` Statements](https://docs.python.org/3/tutorial/controlflow.html#for-statements)

```
>>> # Measure some strings:
... words = ['cat', 'window', 'defenestrate']
>>> for w in words:
...     print(w, len(w))
...
cat 3
window 6
defenestrate 12
```

Code that modifies a collection while iterating over that same collection can be tricky to get right. Instead, it is usually more straight-forward to loop over a copy of the collection or to create a new collection:

```
users = {'Lucy': 'active', 'Lily': 'inactive', 'Tom': 'active'}

# Strategy:  Iterate over a copy
for user, status in users.copy().items():
    if status == 'inactive':
        del users[user]

users = {'Lucy': 'active', 'Lily': 'inactive', 'Tom': 'active'}
# Strategy:  Create a new collection
active_users = {}
for user, status in users.items():
    if status == 'active':
        active_users[user] = status
```

### [The `range()` Function](https://docs.python.org/3/tutorial/controlflow.html#the-range-function)

```
>>> for i in range(5):
...     print(i)
...
0
1
2
3
4
```

It is possible to let the range start at another number, or to specify a different increment (even negative; sometimes this is called the ‘step’):

```
range(5, 10)
   5, 6, 7, 8, 9

range(0, 10, 3)
   0, 3, 6, 9

list(range(10, 0, -3))
   [10, 7, 4, 1]

range(-10, -100, -30)
  -10, -40, -70
```

To iterate over the indices of a sequence, you can combine [`range()`](https://docs.python.org/3/library/stdtypes.html#range) and [`len()`](https://docs.python.org/3/library/functions.html#len) as follows:

```
>>> a = ['Mary', 'had', 'a', 'little', 'lamb']
>>> for i in range(len(a)):
...     print(i, a[i])
...
0 Mary
1 had
2 a
3 little
4 lamb
```

### [`break` and `continue` Statements, and `else` Clauses on Loops](https://docs.python.org/3/tutorial/controlflow.html#break-and-continue-statements-and-else-clauses-on-loops)

### [`pass` Statements](https://docs.python.org/3/tutorial/controlflow.html#pass-statements)

### [Defining Functions](https://docs.python.org/3/tutorial/controlflow.html#defining-functions)

## [Data Structures](https://docs.python.org/3/tutorial/datastructures.html)

### [Dictionaries](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)

### [Looping Techniques](https://docs.python.org/3/tutorial/datastructures.html#looping-techniques)

# [Library Reference](https://docs.python.org/3/library/index.html)

## [Built-in Functions](https://docs.python.org/3/library/functions.html)

### [float](https://docs.python.org/3/library/functions.html#float)

```
>>> float('+1.23')
1.23
>>> float('   -12345\n')
-12345.0
>>> float('1e-003')
0.001
>>> float('+1E6')
1000000.0
>>> float('-Infinity')
-inf
```

### [int](https://docs.python.org/3/library/functions.html#int)

```
int('010')
int('010',10)
int('010', 2)
int('010', 8)
```

### [len](https://docs.python.org/3/library/functions.html#len)

Return the length (the number of items) of an object. The argument may be a sequence (such as a string, bytes, tuple, list, or range) or a collection (such as a dictionary, set, or frozen set).

### [print](https://docs.python.org/3/library/functions.html#print)

```
print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
```

## [Built-in Types](https://docs.python.org/3/library/stdtypes.html)

### [Numeric Types](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex)

## [Numeric and Mathematical Modules](https://docs.python.org/3/library/numeric.html)

### [decimal](https://docs.python.org/3/library/decimal.html)

### [fractions](https://docs.python.org/3/library/fractions.html)





