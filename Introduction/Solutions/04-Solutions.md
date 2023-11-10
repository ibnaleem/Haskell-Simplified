# EXERCISE SOLUTIONS IN 04-INTRO TO HASKELL

Create 2 functions called doubleMe1 and doubleMe2 that take an input and return its double.

```haskell
doubleMe1 x = x + x
doubleMe2 x = x * 2
```

Create a function called doubleUs that take two inputs, doubles them, then adds them together. For example, `doubleUs 3 4` should yield 14.

```haskell
doubleUs x y = x*2 + y*2
```

Create a function called nextUp that takes 2 values, performs integral division, and finds the successor. For example, `nextUp 10 5` should yield 3.

```haskell
nextUp x y = succ (x `div` y)
```