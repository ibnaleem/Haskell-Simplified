# FUNCTIONS
To recap, we learned in [02-Loading Modules](https://github.com/ibnaleem/Haskell-Simplified/blob/main/Introduction/02-Loading%20Modules.md) that Haskell does not declare variables; instead, **it declares functions.**

```
ghci> myVar = 1
ghci> myVar
1
```

## Pure Functions
I know you've never heard the term *pure function* before, but in Haskell, this is a prerequisite for creating functions. 

To put it simply, a pure function is a function that does not have any *side-effects*, and always returns *a value*. Previously, we declared myVar = 1, which is a pure function since myVar always returns 1. Haskell functions don't have to return integers as their values, they could return strings, lists, tuples, etc.

A side-effect in programming happens when a function not only calculates a result but also **causes changes outside of its own calculation.** Haskell avoids side-effects to make programs clearer and more predictable. In Haskell, functions are like math—they take inputs and give outputs without hidden changes. This is good because it makes code easier to understand and less prone to bugs. In contrast, some other languages, like Python, often use side effects. For instance, a function in Python might not just return a value but also print something or modify a variable somewhere else:
```python
# Side effect: Modifying a variable outside the function
total = 0

def add_and_print(x):
    global total
    total += x
    print("Current total:", total)

add_and_print(5)  # Prints: Current total: 5
```

The function not only adds a number but also changes the `total` variable and prints a message. This kind of hidden change is a side-effect.

Another importance of pure functions is the order they are carried out **does not matter:**

```haskell
func1 x = x + 1

func2 y = y * 2

func3 x y = (func1 3) * (func2 5)

func4 x y = (func2 5) * (func1 3)
```

`func3` and `func4` yield the same value, 40, regardless of their order execution. Now consider Python that has *side-effects:*

```python
def open_file(file_path, mode='r'):
    file = open(file_path, mode)
    print(f"File '{file_path}' opened successfully.")
    return file

def close_file(file):
    file.close()
    print("File closed.")
```

Could you run `close_file()` before `open_file()`? Let's see what would happen:

```
close_file("example.txt")
ERROR: FILE IS NOT OPEN
```
> 💡 For simplicity, we have presented the error as *FILE NOT OPEN* instead of the actual error that Python would throw.

The side-effect is that the file must be open before you can run the `close_file()` function.

## Infix vs Prefix Functions
We've actually been using functions without explicitly mentioning them. For example, the `*` symbol functions as a multiplier, taking two numbers and producing a result. When working with numbers, we call it by placing it *between* them, known as an *infix function*. Functions that don't involve numbers are generally used in a *prefix form*. 

```
ghci > 5 * 6 (infix function)
30
ghci> succ 8 (prefix function)
9
```

> 💡 Infix functions are placed *between* their parameters. For example, the `*` function takes 2 parameters which are placed between it like `5 * 6`; `5` and `6` are the parameters of `*` function.

In Haskell, functions are called by writing the function name, followed by a space and then the parameters separated by spaces. 

```haskell
func3 x y = x + y -- x and y are parameters of func3
```
Unlike most imperative languages, Haskell does not require parentheses for function calls. We'll now assume that functions are in the prefix form unless specified. Let's begin by calling one of the simplest functions in Haskell, which was shown in the example above:
```
ghci > succ 8
9
```
The `succ` function gives the next value in a sequence. To use it, we just put the function name and the parameter with a space. Calling functions with multiple parameters is easy. The `min` and `max` functions take two comparable things, like numbers, and return the smaller or larger one, respectively:
```
ghci > min 9 10 
9
ghci > min 3.4 3.2 
3.2
ghci > max 100 101 
101
```
Calling a function by putting a space after it and then typing out the parameters has the highest precedence. This means these two statements are the same:
```
ghci> succ 9 + max 5 4 + 1 16
ghci> (succ 9) + (max 5 4) + 1 16
```
Using parenthesis will not change the precedence; it is good practice because it makes code more readable.

However, to find the successor of the product of 9 and 10, we can't write `succ 9 * 10` because it would get the successor of 9 and then multiply by 10 (resulting in 100). Instead, we use parentheses: `succ (9 * 10)` to get 91.
```
ghci> succ 9 * 10
100
ghci> succ (9 * 10)
91
```
**This is not a side-effect;** recall that the `succ` function takes 1 parameter, and because calling a function has the highest precedence as previously mentioned, Haskell will evaluate `succ 9` before multiplication. This can be easily fixed by adding parenthesis since `(9 * 10)` will yield a *single* value, which can be input into the `succ` function.

When a function has two parameters, we can call it as an infix function by using backticks. 
```
ghci> 9 `min` 10
9
ghci > 3.4 `min` 3.2 
3.2
ghci > 100 `max` 101 
101
```
This is especially useful when you're using functions like `div`. The `div` function takes two integers and does integral division between them, so `div 92 10` would yield 9. However, it's confusing to determine which number is doing the division and which number is being divided. Instead if we type ```92 `div` 10``` it becomes much more clear which number is doing the division and which one is being divided (in this case 92 is being divided by 10).

People from imperative languages often use parentheses for function application. In Python, it's common to see functions called like `foo()`, `bar(1)`, or `baz(3, "haha")`. In Haskell, we use spaces for function application. So, in Haskell, it would be `foo`, `bar 1`, and `baz 3 "haha"`. When you see something like `bar (bar 3)`, it doesn't mean `bar` is called with `bar` and `3` as parameters. It means we first call the function `bar` with `3` as the parameter to get a number, and then we call `bar` again with that number. In Python, that would be something like `bar(bar(3))`.

## Exercises
- Create 2 functions called doubleMe1 and doubleMe2 that take an input and return its double.

- Create a function called doubleUs that take two inputs, doubles them, then adds them together. For example, `doubleUs 3 4` should yield 14.

- Create a function called nextUp that takes 2 values, performs integral division, and finds the successor. For example, `nextUp 10 5` should yield 3.

> 💡 Once you have loaded your file, you can run each function by calling it, like `nextUp 10 5`

[Solutions are posted here.](https://github.com/ibnaleem/Haskell-Simplified/blob/main/Introduction/Solutions/04-Solutions.md)