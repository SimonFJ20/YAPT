
[Go back](index.md)

# Python basics

## Getting started

You can either [download Python3](../download-python3.md) or follow along [in the browser](../imbedded-trinket.html). I recommend downloading Python3 and VSCode.

Start by familiarising yourself with your IDE (*Integrated Development Enviroment*) by running a simple Hello World program.

1. Make a new file `main.py`
2. Write `print('Hello World!')`
3. Run program
4. Assert output to be `Hello World!`, otherwise fix errors

## In general

Mostly all concepts in programming are the same in all most languages. It might look different in some languages, but the fundamentals are the same. Here is some programming basics, in python.

## Math

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

## Variables

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

## If statements

The fundamentals of all computer programming is based on logic. The simplest for of logic is called condition logic, e.g. '*if light is green then walk*', '*if no more milk in fridge then buy more*', '*if sign says turn right then turn right else turn left*. In most programming languages, python included, **if statements** represent conditional logic. Examine following example of if statements in Python:

```py
a = 5
b = input()

if a == b:                      # if a is equal to be then
    print('you guessed right')
```

```py
window_should_close = True

if window_should_close:
    close_window()
else:
    render_window()

```

```py
a = 5
b = 6

if b > a:                   # if `b` is greater than `a` then
    b = b - 1               # subtract 1 from `b`
elif b < a:                 # else if `b` is less than `a` then
    b = b + 1               # add 1 to `b`
else:                       # else
    print('a equals b')
    
```

## Loops

In programming we don't just copy and paste code. As said by [Martin Fowler](https://en.wikipedia.org/wiki/Martin_Fowler_(software_engineer)): '*Once and once only*', meaning that when we program, we should only write the same line of code once. But what if, for example, we need to increase `x` to be the same size as `y`. A naive approach could be the following:

```py
x = 2
y = 5

if x < y:
    x = x + 1

if x < y:
    x = x + 1

if x < y:
    x = x + 1

if x < y:
    x = x + 1

```

As you can see this is not a very elegant solutions, a better solution would be to use some kind of a loop, which should look something like the following:

```
x = 2
y = 6

while x less than y increase x by one
```

This leads us into the first of the 2 most common loops.

### While loop

While loops are the simpler of the 2 mmost common loops. While do exactly what you think; while something is true, do something. The while loop just like the if statement, except it starts over if the condition is still true after it has run.

Examples of while loops in Python:

```py
x = 9
y = 1

while x > y:
    x -= 1
```

```py
print('enter the number: 5')
user_input = input()

while user_input != 5:
    print('try again')
    user_input = input()

print('you printed the number: 5')
```

```py
while connection_check_connection()
    data = read_connection_data()
    do_important_work_with(data)
```

### For loop

The while loop is fundamentally just a while loop, but more specific. For loops are for ranges, e.g. 1 to 10.

Example of a For Loop:

```py
for i in range(0, 10):
    print(i)

# this will print:
# 0
# 1
# 2
# ...
# 9
```

This is just the same as writing:

```py
i = 0
while i < 10:
    print(i)
    i += 1

# this will also print:
# 0
# ...
# 9
```

For loops are just a shorthands for while loops, despite that, the for loop is to prefer over the while loop. The while loops has it purposes, but when it comes to ranges of numbers, the for loop should be used.

For loops can also be used to go through a list/array (we'll touch on list/array later). Examine the following example:

```py
values = [4, 2, 6, 7, 3, 9]

for value in values:
    print(value)

# this will print 4 2 6 7 3 9 on seperate lines
```

This is the same as writing:

```py
values = [4, 2, 6, 7, 3, 9]
values_length = len(values)

for i in range(0, values_length):
    value = values[i]
    print(value)
```

Which then also is the same as writing:

```py
values = [4, 2, 6, 7, 3, 9]
values_length = len(values)

i = 0
while i < values_length:
    value = values[i]
    print(value)
    i += 1
```

As you can see, the for loop can shorten the code quite a bit, without removeing informations.

### Break and Continue

Both the while- and the for loop can be manipulated by using `break` and `continue`.

The `break` keyword just exits the loops, see following example:

```py
for i in range(0, 10):
    if i == 5:
        break
    print(i)

# this will print the values 0 1 2 3 4 but stop at 5
```

The `continue` keyword starts over the loop, check the condition again. Example:

```py
for i in range(0, 10):
    if i == 5:
        continue
    print(i)

# this will print the values 0 1 2 3 4 6 7 8 9, but not 5
```

## Arrays/Lists

In Python they are called lists, in many languages they are calles arrays, therefore i will from now on refer to the Python list as an array.

Heads up!, array indexing, i.e. the reference to elements, start at 0, i.e. my_array\[0\] is the first element in the array. This is the case for all languages, except for Lua, where it start at 1, i.e. my_array\[1\] is the first element. But we're not using Lua right now.

Arrays are just variables but more of them combined, e.g. instead of:

```py
player0_score = 34
player1_score = 62
player2_score = 16
player3_score = 94
```

We can use an array instead:

```py
player_score = [34, 62, 16, 94]
```

Now we can refer to them as:

```py
player0_score = player_score[0]
player1_score = player_score[1]
player2_score = player_score[2]
player3_score = player_score[3]
```

We can print arrays:

```py
print(player_score) # prints '[34, 62, 16, 94]'
```

We can change single elements in the array:

```py
player_score[2] = 25
print(player_score) # prints '[34, 62, 25, 94]'
```

We can append values to the array:

```py
player_score.append(43)
print(player_score) # prints '[34, 62, 25, 94, 43]'
```

We can find a value and remove it:

```py
player_score.remove(62)
print(player_score) # prints '[34, 25, 94, 43]'
```

We can remove specific indices:

```py
player_score[2].pop(2)
print(player_score) # prints '[34, 25, 43]'
```

Arrays can also store different values like strings or booleans:

```py
my_string_array = ['john', 'jack', 'joe', 'jeremy']
my_bool_array = [False, False, False, True, True, False]
```

Sometimes we need to sort arrays based on the values. We can do that either with an inbuild function, or by doing it ourselves:

Inbuild sort example:

```py
my_values = [5, 2, 6, 7, 1, 4, 6]

my_values.sort()

print(my_values) # prints '[1, 2, 4, 5, 6, 6, 7]'
```

Doing it ourselves. This is using the [Selection Sort](https://en.wikipedia.org/wiki/Selection_sort) algorithm:

```py
my_values = [2, 5, 3, 7, 8, 2, 1]
my_values_length = len(my_values)

# go through intire array
for i in range(my_values_length):
    # find the minimum element in remaining unsorted array
    minimum_index = i
    for j in range(i + 1, my_values_length):
        if my_values[minimum_index] > my_values[j]:
            minimum_index = j
    
    # simple swap maneuver
    temp = my_values[i]
    my_values[i] = my_values[minimum_index]
    my_values[minimum_index] = temp

print(my_values) # should print '[1, 2, 2, 3, 5, 7, 8]'
```

## Functions

```py
# create the function
def my_function():
    print('called my_function')

# call the function
my_function()
```

```py
def print_range(a, b):
    for i in range(a, b):
        print(i)


print_range(-5, 10)
```

```py
from random import randint

STRING_CHARS = 'abcdefghijklmnopqrstuvwxyz0123456789'
def generate_random_string(length):
    string = ''
    for i in range(length):
        string += STRING_CHARS[randint(0, len(STRING_CHARS))]
    return string


my_new_player_id = generate_random_string(16)
print(my_new_player_id) # should print something like 'af8n923ngFSF9dgG'
```


[Go back](index.md)

