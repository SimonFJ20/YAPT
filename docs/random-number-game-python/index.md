
[Go back](../index.md)

# Random Number Game in Python

## Getting started

You can either [download Python3](../download-python3.md) or follow along [in the browser](../imbedded-trinket.html). I recommend downloading Python3 and VSCode.

Start by familiarising yourself with your IDE (*Integrated Development Enviroment*) by running a simple Hello World program.

1. Make a new file `main.py`
2. Write `print('Hello World!')`
3. Run program
4. Assert output to be `Hello World!`, otherwise fix errors

## Some programming basics in python

Mostly all concepts in programming are the same in all most languages. It might look different in some languages, but the fundamentals are the same. Here is some programming basics, in python.

### Math

Programming is just a fancy way of doing math. While most of the complicated math is abstracted away, we still use simple math when programming. Examine the following:

```python
# a function that calculates the area of a square
def calculate_square_area(width, height):
    area = width * height
    return area

# a function that calculates the circumference of a square
def calculate_square_circumference(width, height)
    circumference = (width + height) * 2
    return circumference
```

Dont mind all the unknown syntax (syntax meaning the programming language equivalent of words/sentences/grammar) of the program. Just focus on the 2 lines of math. First we see a simple operation: `width * height`, this simply multiplies `width` by `height` nothing fancy going on here. Second we see a bit more complex operation: `(width + height) * 2`, the parentheses: `(` and `)` are in this case, just the same same as the ones on paper math.

In programming we often use math as part of our program. Although seldom very complex math, we use simple math in nearly every program. Examine the following:

```python
# program that keeps count of guest in a hotel
guest_amount = 0

def guest_enters():
    guest_amount = guest_amount + 1

def guest_leaves():
    guest_amount = guest_amount - 1
```

In this case we just use very simple operations, like `- 1` and `+ 1`. The use of variables leads us into the next topic.

### Variables

In programming we need to the values we calculate. This is done with variables. We know variables from math, as `x`, `y`, etc., where they are used to represent values that are unknown and/or changing. In programming also use variables to represent values that are to change, but in programming we think of them a bit different.
In programming we think of variables as little containers/boxes with names that contains values, e.g. a box with the name `a` stores the value of `5`, another box with the name `b` and the value of `4`. Now I can use the values from the variables in my new variable with the name `c` that now will have the value of `a` added to the value of `b`, i.e. `5` added to `4`. This will make more sense with the following example:

```python
a = 5
b = 4
c = a + b
```

One thing that is important to remember, is the order of operation. We know order of operation from math, that is, we divide and multiply before we add and subtract, e.g. `2 + 3 * 4 is 14` and `(2 + 3) * 4 is 20`. We do the same in programming, but to a much higher level. Consider the following example:

```python
total = 5

# total should be 5

total = total + 1

# total should be 6
```

In math this is illegal, but we do this often in programming. Here the right hand side of the `=` is calculated first, before being assigned to the `total` variable. This is equivalent to:

```python
total = 5

a = total + 1
total = a
```

And because we do it so often, we have shorthands (compact way of writing larger sentences) for it. Examine the following:

```py
a = 1

a += 1  # equivalent to writing `a = a + 1` and used often
a -= 1  # used often
a *= 1  # rarely used
a /= 1  # rarely used
```

Variables can not only store whole integers, but all these value types:

- Integers, called int(s), `100`, `0`, `-14`
- Floating point numbers, called float(s) or double(s), `3.1415`, `-1.4`, `-2043.34`
- Letter strings, called string(s), `"Hello world!"`, `'John Doe'`, `'#&¤/("&'`
- Boolean values, called bool(s) or boolean(s), `True`, `False`

Integers are whole, positive and negative numbers including `0`. They can in Python be written as `45`, and with prefix, eg. `+45` and `-45`, representing positivity and negativity.

Floats are integers, but with decimal numbers. In python floats can be written just like integers with a decimal point and decimal numbers, eg. `-45.0`, `45.45`. In Python you can ommit either the pre- or proceding zero of a float, ie. `0.643` can be written as `.643` and `2.0` can be written as `2.`. If you ommit the `.` entirely, Python will think it is an integer.

Strings are just stored text. In python `'` and `"` can be used interchangably, although with case consistency, i.e. a string that begins with a `"` should also end with a `"` and vice versa. When dealing with strings, we sometimes need characters that aren't easy to encapsulate, these are called hard-to-type characters, these include newline, tabs etc. How we deal with hard-to-type characters is through escaped characters. This is done by first typing a `\` and then the desired character, e.g. a newline would be `\n`. One case we often use this is when we need the string char `"` or `'`. If we begin and end a string with a `'`, we can't just put a `'` in the middle of our string, here we will write `\'` instead. Examine the following:

```python
my_string = "this is a string"
my_string2 = 'this is also a string'
string_with_newline = "this string\nincludes a newline character"
string_with_quote_mark = "this string includes a \" mark"
```

Boolean values can either be false or true, and no other value. In Python true and false is written as `True` and `False`. Boolean values are used when doing boolean operations. Examine the following:

```
a = 5
a_is_less_than_6 = a < 6    # this should be True
a_is_equal_to_4 = a == 4    # this should be False
b = a_is_less_than_6
c = !b                      # here we use `!` called the NOT operator. if b == true then c = false and vice versa.
```

Note that in boolean logic, `.. a == 4`, we use double equals `==`, while in assignment, `a = 5`, we use single equal `=`


[Go back](../index.md)
