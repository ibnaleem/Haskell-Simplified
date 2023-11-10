# INTRO TO HASKELL

Let's begin! If you skipped the introduction, go back and check the last part; it tells you what you need for this tutorial and how we'll use functions. Now, open your terminal and type "ghci" to enter Haskell's interactive mode. You'll see something like this:

```
GHCi, version 9.2.8: https://www.haskell.org/ghc/  :? for help
ghci> 
```
If you see something like this:
```
GHCi, version 9.2.8: https://www.haskell.org/ghc/  :? for help
Prelude> 
```
then simple type `:set prompt "ghci> "`:
```
Prelude> :set prompt "ghci> "
ghci> 
```

Good, now let's try some arithmetic:
```
ghci> 2 + 15
17
ghci > 49 * 100
4900
ghci > 1892 - 1472 
420
ghci> 5 / 2 
2.5
ghci >
```
This is easy to understand. You can use multiple operators in a single line, and they follow the standard precedence rules. If needed, you can use parentheses to clarify or modify the precedence.
```
hci > (50 * 100) - 4999
1
ghci> 50 * 100 - 4999
1
ghci > 50 * (100 - 4999)
-244950
```
> 💡 Precedence: the condition of being considered more important than someone or something else; priority in importance, order, or rank. **Order of operations in mathematics.**

Be cautious when dealing with negative numbers; it's safer to enclose them in parentheses. For instance, `5 * -3` might cause an issue, but `5 * (-3)` will work fine.

Boolean algebra is simple too. As you likely know, `&&` represents a boolean **AND**, `||` stands for a boolean **OR,** and `not` negates either True or False.
```
ghci > True && False
False
ghci > True && True
True
ghci > False || True
True
ghci > not False
True
ghci> not (True && True)
False
```
The expression `(True && True)` yielded `True` and `not` negated this, resulting in `False`.

Testing for equalities:
```
ghci> 5 == 5
True
ghci> 1 == 0
False
ghci> 5 /= 5
False
ghci> 5 /= 4
True
ghci> "hello" == "hello"
True
```

Note that `/=` means not equal to, which is why `5 /= 4` yielded True. 

What if we try to combine an integer with a string, like `5 + "hello"`? Let's try it:
```
ghci> 5 + "hello"

<interactive>:1:3: error:
    • No instance for (Num String) arising from a use of ‘+’
    • In the expression: 5 + "hello"
      In an equation for ‘it’: it = 5 + "hello"
```
We see that the Haskell compiler cannot find a valid implementation (instance) of a particular type class for a given type. The given type is (Num String) which cannot be implemented from the use of `+` operator. 

Instead, we can use the `++` operator for concatenation:
```
ghci> 5 ++ "hello"
"5hello"
```
We will discuss what distinguishes `+` from `++` and why you can concatenate different types with `++` and not `+` in the [Types]() chapter.

For now, let's learn about [04-Functions in Haskell]().