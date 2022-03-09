
[Go back](index.md)

# Programming 1

## Goal

Be able to program a simple program

## Language and Environment

We'll use the [Lua](https://www.lua.org/) programming langauge, because its simple.

And we'll use the online [Lua Demo](https://www.lua.org/cgi-bin/demo) to run our code.

![image](https://user-images.githubusercontent.com/28040410/157533858-6687bc20-5c0c-41c3-b182-92aad8b3bf30.png)

## Make "FizzBuzz" program

### Setup coding environment

Start by typing:

```lua
print("hello world")
```

Make sure to copy it character by character, and think about the composition of the "statement":
- The word `print` is you saying that your want to "print" something to the user
- Everything inside the parentheses, `(` and `)`, are values we give to the `print` "function"
- Quotationmarks `"` are used in programming, to convert written text to a string value. Lookup [strings](#Strings).

Now press 'run' and you should see:

![image](https://user-images.githubusercontent.com/28040410/157537505-f39b0e1f-769f-4516-bbf2-63654e205081.png)

Or if you typed in wrong, it should look something like:

![image](https://user-images.githubusercontent.com/28040410/157537629-d5c1f566-b797-4c00-9f6c-6d3f0bddd2f8.png)

![image](https://user-images.githubusercontent.com/28040410/157537685-54892d3d-2e60-4772-95eb-ae65544439c3.png)

Try changing the text, insert spaces and change it up a bit, to familiarize yourself. Consider the following:

```lua
local myString = "hello world"
print(myString)

local a = "train"
local b = "station"
local c = a + b
print (c)
```

The `local` word is for making variables. Lookup [variables](#Variables).

You now know, that your enviroment is ready for programming.

> - "statement": a coding line is also called a statement
> - to "print" something: writing text or numbers to the user/screen
> - "function": a piece of code with a name, can be built-in like `print`, or created by the programmer

### Identifying the problem

Now then, remember the childrens game [Fizz Buzz](https://en.wikipedia.org/wiki/Fizz_buzz).

The rules are simple:
1. Starting from 1 you count out loud up to however many you want
2. If the number is divisable by 3, you say Fizz instead
3. If the number is divisable by 5, you say Buzz instead
4. If both, say FizzBuzz

The series would go like: `1 2 Fizz 4 Buzz Fizz 7 8 Fizz Buzz 11 Fizz 13 14 FizzBuzz 16 17 ...`

### Discovering a solution

// TODO (wont be done)

### Naive implementation

```lua
print("1")
print("2")
print("Fizz")
print("4")
print("Buzz")
```

You can probably guess what's going on here, and why is probably isn't the smartest way of doing it.

### Smarter implementation

```lua
for i = 1, 15, 1 do
    if (i % 15 == 0) then
        print("FizzBuzz")
    elseif (i % 3 == 0) then
        print("Fizz")
    elseif (i % 5 == 0) then
        print("Buzz")
    else
        print(i)
    end
end
```

Let's start from the inside.
We know what the `print` function does, when it we give it a string. When we give `print` something else, like a number, it will do its best to print it.
You can test this out for yourself. Lookup [variables](#Variables) if you're unsure about `print(i)`.

Let go a level fo


## Lookup references

### Variables

Variables in programming (like in math) act like placeholders for values.

```lua
local a = 5
local b = "hello world"

local myString = "sussy imposter amogus"
print(myString)

local myInteger = 45
local myInteger2 = -3243

local myFloat = -3.0
local myFloat2 = 3.141592
print(myFloat)

local myBoolean = true
local myBoolean2 = false
print(myBoolean)

local myNull = nil
```

### Strings

Strings are text values. The text of a string is written inside quotationmarks.
Some languages use `"` called doublequote for strings, other langauges uses both `"` doublequotes and apostrophes `'` called singlequotes for strings.
Lua uses both, so pick your favorite, just be consistent.

```lua
local myName = "SimonFJ20"

print('hello world')
```



[Go back](index.md)
