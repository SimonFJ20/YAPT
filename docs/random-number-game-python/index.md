
[Go back](../index.md)

# Random Number Game in Python

## Getting started

You can either [download Python3](../download-python3.md) or follow along [in the browser](../imbedded-trinket.html). I recommend downloading Python3 and VSCode.

Start by familiarising yourself with your IDE (*Integrated Development Enviroment*) by running a simple Hello World program.

1. Make a new file `main.py`
2. Write `print('Hello World!')`
3. Run program
4. Assert output to be `Hello World!`, otherwise fix errors

Check out the [Python basics](../python-basics.md).

Now start up an empty project.

## The goal

The goal for this application is a game, where the game will generate a random number between 0 and 100. Now the player has to guess the random number in as little attempts as possible. When the player guesses the number, a new number generates and the cycle continues.

## Getting user input and output

Start py printing `Hello user` with the buildin `print` function by writing:

```py
print('hello user')
```

Now when we run the program, it should output `Hello user`.

To get user input we use the buildin `input` function.

```py
print('hello user')

user_input = input('> ')
print('you wrote': user_input)
```


[Go back](../index.md)
