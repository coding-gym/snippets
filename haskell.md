---
title: "Haskell"
---

## The `interact` function

The `interact` function takes a function of type `String -> String` as its argument.
The entire input from the standard input device is passed to this function as
its argument, and the resulting string is output on the standard output device.

### Predicate on strings

Example: [Balanced Brackets](/challenges/balanced-brackets)

Input:

```txt
3
{[()]}
{[(])}
{{[[(())]]}}
```

Output:

```txt
YES
NO
YES
```

The first line contains a single integer `n`, the number of strings.

Each of the next `n` lines contains a single string `s`.

In this example:

 - `lines` split the complete input, as `String` on the line break, resulting in
     a `[String]` (list of strings).
 - `tail` is here just to ignore the first line (normally *hackerrank* tests have
    a number denoting the count of following elements)
 - `yesNo` transalte a boolean to a string *YES*/*NO*
 - `unlines` joins the resulting list of string, placing a line break between
   the strings.

```haskell
doSomething :: String -> Bool
doSomething str = undefined -- TO BE COMPLETED

main = interact . unlines . fmap (yesNo . doSomething) . tail . lines
```

## List of numbers

Example: [Closest Numbers](/challenges/closest-numbers)

Input:

```txt
10
-20 -3916237 -357920 -3620601 7374819 -7330761 30 6246457 -6461594 266854
```
Output:

```txt
-20 30
```

We are provided with a list of numbers and our algorithm must produce another
list of numbers (not necessarily of the same length).

In this example:

 - `words` split the complete input, as `String` on any blank character, resulting in
     a `[String]` (list of strings).
 - `tail` is here just to ignore the first number (normally *hackerrank* tests have
    a number denoting the count of following elements)
 - `fmap read` convert each string to a number
 - `fmap show` convert each number back to a string
 - `unwords` joins the resulting list of string, placing a space between
   the strings.

```haskell
doSomething :: [Int] -> [Int]
doSomething xs = undefined -- TO BE COMPLETED

main = interact (unwords . fmap show . doSomething . fmap read . tail . words)
```

## T test cases, each test case has 2 lines

The first line contains `t`, the number of test cases.

The next `t` pairs of lines each represent a test case.

 - The first line contains `n`, the number of elements in the array `arr`.
 - The second line contains`n` space-separated integers

We can ignore the first line (we will read to the end of file) and the lines
with `n`. So we can just read the lines with the actual array and split by spaces.

We can even ignore odd lines, this is why `filter fst`, where `fst` is
alternately `True` and `False`.

```haskell
doSomething :: [Int] -> Bool
doSomething arr = undefined -- TO BE COMPLETED

yesNo True = "YES"
yesNo False = "NO"

main =
  getContents >>=
  putStr .
  unlines .
  fmap (yesNo . doSomething . fmap read . words . snd) .
  filter fst . zip (concat $ repeat [False, True]) . tail . lines
```
