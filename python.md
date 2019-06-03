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
