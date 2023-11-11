<head>
    <base href="https://ibnaleem.github.io/Haskell-Simplified/" />
</head>

# LOADING MODULES
Now that Haskell has been successfully installed, we can create Haskell files and load them into the compiler (GHC).

Start by creating a `hello.hs` file, open it with your favourite text editor and type the following:

```haskell
main = putStrLn "Hello, Haskell!"
```

To compile, make sure you are in the same directory as `hello.hs`, and run `ghc hello.hs` in your CLI:
```
>> ghc hello.hs
[1 of 1] Compiling Main             ( hello.hs, hello.o )
Linking hello ...
```

To run the our compiled program, we simply type `./hello` in our CLI, just like `C`!

```
./hello 
Hello, Haskell!
```

Congrats, you've written your first Haskell code! Now let's disect what we wrote:

- `main`: In Haskell, every program must have a `main` function, which is the entry point of the program. The `main` function is of type I/O, indicating that it performs **i**nput/**o**utput operations and **does not return a value.** Think of the `main` function like the `if __name__ == "__main__":` in Python, `int main() {...}` in C, and `public static void main(String[] args) {...}` in Java. It will always run.
<br>
- `putStrLn`: This is a function that takes a String (a sequence of characters, remember that as we'll discuss this in the Types chapter) and performs an I/O operation by printing the string to the console.
<br>
- `"Hello, Haskell!"`: This is the string that was printed to the console. This is probably the only line of code you understood *before* the explanation if you've ever coded before.

Notice that the `main` function was declared with `=` and some value to return. If you've coded in JavaScript, it is equivalent to a `const` function:

```javascript
const multiply = (a, b) => {
    const result = a * b;
    return result;
};
```

This is because Haskell **does not declare variables, only functions.** 

🗣️ *But can't we do `myVar = 3`*?

Yes, but `myVar` would not be a variable **but a function:**
```
ghci> myVar = 1
ghci> myVar
1
```
`myVar` is a function because it returns a value, which in this case is just 1. 

To understand this further, let's dive into [03-Intro to Haskell](/Introduction/03-Intro%20to%20Haskell).
