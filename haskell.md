---
title: "Haskell"
---

## T test cases, each test case has 2 lines

The first line contains \\( T \\), the number of test cases.

The next \\( T \\) pairs of lines each represent a test case.

 - The first line contains \\( n \\), the number of elements in the array \\( arr \\).
 - The second line contains \\( n \\) space-separated integers

We can ignore the first line (we will read to the end of file) and the lines
with \\( n \\). So we can just read the lines with the actual array and split it
with the `words` function.

```haskell
import Data.List.Split (chunksOf)

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
