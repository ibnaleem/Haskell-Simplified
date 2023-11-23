# IF STATEMENTS

Let's create a function that multiplies a number by 2 *if* it's less than or equal to 100:

```haskell
doubleSmallNumber x = if x > 100 then x else x*2
```
A new keyword, `then`; this is equivalent to the `:` at the end of `if`-statements in languages like Python:

```python
def doubleSmallNumber(num:int) -> int:
    if num > 100:
        return num
    else:
        return (num * 2)
```
Apart from the new `then` keyword, Haskell requires an `else` statement when an `if` statement is used.

In Haskell, every piece of code, including conditions and functions, **must give back a result.** Unlike some other languages where you can skip steps in certain conditions, Haskell requires every expression to return something. In Haskell, the `if` statement is an expression too. An expression is just a piece of code that gives a value. For example, `5`, `4 + 8`, and `x + y` are all expressions because they produce a result. In Haskell, the `if` statement always returns something because the `else` part is obligatory, making it an expression as well.

> 💡 `5` is an expression because it returns `5`, much like the `myVar = 1` function in [02-Loading Modules](./02-Loading%20Modules)

> 💡 Boolean values are valid return values; The `else` expression is executed once the `if` expression returns `False`. In other words, unlike in Python where you can `pass` an if statement, the if expression **must** return `False` for the `else` expression to run. The `if` expression runs when it returns `True`.

If our intention was to increment each generated number in the previous function, we could have formulated its body in this manner:

```haskell
doubleSmallNumber’ x = (if x > 100 then x else x*2) + 1
```

Remember that parenthesis are of higher precedence than expressions without them; the expression in the parenthesis is executed, which checks if the input `x` is greater than (`>`) 100, else, multiply `x` by 2. The parenthesis produces a value, for example, 8 if `x = 4`, and then the expression `+ 1` is evaluated.

> 💡 There is a much more efficient way of writing this function. Think back to [04-Functions in Haskell](./04-Functions%20in%20Haskell). Could we use a function that produces the next value in a sequence (equivalent to `+ 1`)?

If we excluded the parentheses, it would have added one only if `x` wasn't greater than 100. Pay attention to the apostrophe (`’`) at the end of the function name. In Haskell's syntax, this apostrophe doesn't have any special meaning; it's a valid character to include in a function name. Typically, we use the apostrophe to indicate either a strict version of a function (one that isn't lazy) or a slightly modified version of a function. Since the apostrophe is permitted in function names, we can create a function like this.

```haskell
conanO’Brien = "It’s a-me, Conan O’Brien!"
```
Do you see something off with this function name? Pay close attention to the first name (Conan); why is `C` not capitalized? English grammar tells us the first letter of anyone's name is always capitalized, so why have we purposely named the function `conanO’Brien` and not `ConanO’Brien`?

That's because Haskell isn't your English teacher, it does not like functions with a leading capital character. So functions **must** be written with a lowercase first character.

Back to if-statements, what if we wanted to code it on multiple lines like Python? Well, we can do this:

```haskell
doubleSmallNumber x = if x > 100
                      then x
                      else x * 2
```

**Make good note of the indentation:** Haskell relies on good indentation to define the structure of code blocks. This means the following indentations are **incorrect:**
```haskell
doubleSmallNumber x = if x > 100 
                    then x
                    else x*2
```
```haskell
doubleSmallNumber x = if x > 100 
                        then x
                        else x*2
```
The `if`, `then` and `else` keywords are all in-line. Don't worry, *many many many* Haskell devs make this mistake; sometimes re-reading code can help, but a minor indentation is always overlooked by us. You can use ChatGPT or other tools to help you fix your code indentation.

To recap, the only unique feature Haskell brings to conditional statements is that they must have an `else` statement (formally known as an *expression* in Haskell) use a `then` keyword to evaluate the `if` expression, and the `if`, `then` and `else` keywords must be indented vertically.

Next, [06-Intro to Lists](./06-Intro%20to%20Lists)