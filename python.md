---
title: "Python"
---

## Reading strings

We can read a single line string using the built-in functions `input()`:

```python
a_line_read = input()
```

## Reading an array of integers

When you need to read an array of integers, you have to read the entire line, split it and the convert
each element to an int:

```python
a_list_of_nums = map(int, input().split())
```

## Reading n rows made up of a single integer

```python
for n in range(10):
    single_int = map(int, input())
```

## Writing on STDOUT

When you need to write on *stdout* use:

```python
print("some text", file=sys.stdout)
```

## Faster collections

Some exercices are skewed towards languages with very low overhead in handling collections
of integers. For these kind of exercises using a `list` to hold data may not cut it. A faster
alternative with lower overhead but the same nice ergonomics is provided by the `array` module.

For example to store a collections of unsigned integers and append to it one element:

```
from array import array

a = array('I', [1, 2, 3, 4, 5])
a.append(6)
print(a, len(a))
```

Check out the reference documentation at:
https://docs.python.org/3/library/array.html
