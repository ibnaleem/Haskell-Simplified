# INTRO TO LISTS
Lists in Haskell are highly valuable, like shopping lists in real life. They serve as the most commonly used data structure, offering versatile solutions to various problems. This section covers fundamental aspects of lists, including *strings* (which are a *type* of list) and list comprehensions.

In Haskell, lists are **homogeneous,** storing elements of the same type. You can have a list of integers or a list of characters, but mixing types, like having both integers and characters in one list, is not allowed.

## Let Statements
Before we begin, let's understand a new keyword we will be using a lot; `let`. In Haskell, a `let` statement is used to bind a name to a value within a specific scope. It allows you to create *local definitions* that are only valid within the block of code where the `let` statement is used. This helps in making code more modular and readable by restricting the scope of definitions to where they are actually needed.

> 💡 In Haskell, a definition is a way of giving a name to a value or a function. It establishes an association between a name and an expression or a set of equations, specifying the value or behavior that the name represents. Definitions are crucial for clarity and reusability in Haskell code. These named entities can represent anything from simple values to complex functions.

## Lists
`let`'s create a list:
```
ghci > let lostNumbers = [4, 8, 15, 16, 23, 48] 
ghci > lostNumbers
[4, 8, 15, 16, 23, 48]
```
Lists in Haskell are represented with square brackets, and their values are separated by commas. If we attempt a list like `[1,2,'a',3,'b','c',4]`, Haskell would raise an error since characters (indicated by single quotes) cannot mix with numbers. Speaking of characters, strings in Haskell are essentially lists of characters. For example, "hello" is equivalent to `['h','e','l','l','o']`. Since strings are lists, we can apply list functions to them, making it quite convenient.

> 💡 `" "` are reserved for strings (a list of characters) where as `' '` are used for single characters (`'a'`, `'b'`). `"a"` will raise an error.

## `:` and `++` Operators

Now let's combine to lists together using the `++` operator:
```
ghci> [1,2,3,4] ++ [9,10,11,12] 
[1,2,3,4,9,10,11,12]
ghci> "hello" ++ " " ++ "world" 
"hello world"
ghci> [’w’,’o’] ++ [’o’,’t’] 
"woot"
```
Be cautious when repeatedly using the `++` operator on lengthy strings. When combining two lists, even appending a singleton list (`[1,2,3] ++ [4]`), Haskell internally traverses the entire left list. This is fine for smaller lists, but for a list with fifty million entries, it can be time-consuming. On the other hand, adding an element at the beginning of a list using the `:` operator (cons operator) is instantaneous.
```
ghci> ’A’:" SMALL CAT" 
"A SMALL CAT"
ghci > 5:[1 ,2 ,3 ,4 ,5] 
[5,1,2,3,4,5]
```
> 💡 A singleton list is a list that contains only one element.

Note that `:` combines a number with a list of numbers or a character with a list of characters, while `++` merges two lists. Even when appending an element to the end of a list with `++`, you need to enclose it in square brackets to form a list.

For instance, `[1,2,3]` is essentially shorthand for `1:2:3:[]`. `[]` denotes an empty list. If we add 3 to it using `:`, it becomes `[3]`. Prepending 2 to that gives `[2,3]`, and the pattern continues.
> 💡 `[]`, `[[]]`, and `[[],[],[]]` represent distinct entities. The first is an empty list, the second is a list containing one empty list, and the third is a list containing three empty lists.

## Indexing
To retrieve an element from a list by index, use the `!!` operator, where indices begin at 0.
```
ghci> "Steve Buscemi" !! 6
’B’
ghci > [9.4 ,33.2 ,96.2 ,11.2 ,23.25] !! 1
33.2
```
> 💡 "Out of bounds" error exist in Haskell! If you try to get the sixth element from a list that only has four elements, you’ll get an error so be careful!

Lists have the flexibility to encompass other lists, including lists within lists, forming nested structures.
```
ghci> let b = [[1,2,3,4],[5,3,3,3],[1,2,2,3,4],[1,2,3]] 
ghci> b
[[1,2,3,4],[5,3,3,3],[1,2,2,3,4],[1,2,3]] 
ghci> b ++ [[1,1,1,1]]
[[1,2,3,4],[5,3,3,3],[1,2,2,3,4],[1,2,3],[1,1,1,1]] 
ghci> [6,6,6]:b
[[6,6,6],[1,2,3,4],[5,3,3,3],[1,2,2,3,4],[1,2,3]] 
ghci> b !! 2
[1,2,2,3,4]
```
Lists within a list may vary in length, but they must maintain uniformity in terms of data types. Similar to not having a list with both characters and numbers, you cannot construct a list containing both lists of characters and lists of numbers.
```
ghci> let a = [[1,2,3], ['a','b','c']]
<interactive>:1:11: error:
    • No instance for (Num Char) arising from the literal ‘1’
    • In the expression: 1
      In the expression: [1, 2, 3]
      In the expression: [[1, 2, 3], ['a', 'b', 'c']]
```

## Comparing Lists
Lists are comparable if their elements are comparable. When using `<`, `<=`, `>`, and `>=` for list comparison, it follows a lexicographical order. Initial comparisons focus on the **heads** of the lists. If they are equal, the comparison extends to the second elements, and so forth.
```
ghci> [3,2,1] > [2,1,0] 
True
ghci> [3,2,1] > [2,10,100] 
True
ghci> [3,4,2] > [3,4] 
True
ghci> [3,4,2] > [2,4] 
True
ghci> [3,4,2] == [3,4,2] 
True
```
## List Functions
The `head` function accepts a list and yields its initial element, which is essentially the first element of the list.
```
ghci > head [5, 4, 3, 2, 1]
5
```
`last` does the opposite since it returns the last element in the list (opposite to `head`).
```
ghci > last [5, 4, 3, 2, 1]
1 
```
`tail` takes a list and returns everything except the `head`, so the first element of the list
```
ghci > tail [5, 4, 3, 2, 1] 
[4, 3, 2, 1]
```
> 💡 `head` returns the first element and cuts off the entire list after it, whereas `tail` cuts off the head and returns all elements after it

`init` takes a list and returns everything except its last element, so opposite of `tail`.
```
ghci > init [5, 4, 3, 2, 1] 
[5, 4, 3, 2]
```

Moving forward, when we refer to the head of a list, we are referring to the first element of the list at index 0.

- head of `[1,2,3,4]` is 1
- head of `[87, 62, 55, 22]` is 87
- head of `[22, 99, 66]` is 22

When we refer to the tail of a list, we are referring to a list *without* the head
- tail of `[1,2,3,4]` is `[2,3,4]`
- head of `[87, 62, 55, 22]` is `[62, 55, 22]`
- head of `[22, 99, 66]` is `[99, 66]`

With that established, what do you think `ghci>` will return if we do this?
```
ghci> head (tail [1, 2, 3, 4, 5, 6, 7, 8, 9])
``` 
<details open>
  <summary>🔓 Click me to reveal the answer!</summary>
  In programming and especially in Hasekell, breaking down the problem is crucial:

  - Haskell will evaluate the parenthesis first as a rule of precedence, therefore, `tail [1, 2, 3, 4, 5, 6, 7, 8, 9]` would be evaluated first
  - `tail` always returns a list *without* the head, and since the head is 1, the new list will be `[2, 3, 4, 5, 6, 7, 8, 9]`
  - Finally, Haskell will evaluate the outer `head` function on the new list, `[2, 3, 4, 5, 6, 7, 8, 9]`
  - The first element of that list is 2, therefore, `ghci>` will return 2

  ```
  ghci> head (tail [1, 2, 3, 4, 5, 6, 7, 8, 9])
  2
  ``` 
</details>

> ✍️ Try to get the head of an empty list `[]`; what does it return?

*more being added soon*
