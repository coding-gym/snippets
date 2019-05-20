---
title: "C++"
---

## Premise

To be more exact, we should include all the needed headers first. 

For example:

```cpp
#include <iostream> // for I/O
#include <iterator> // for istream_iterator
#include <vector> // for vector
#include <string> // for string
```

Actually, since we are usually hosted on machines with GCC, we can include only:

```cpp
#include <bits/stdc++.h>
```

Which makes everything from the STL available. Remember this header **is not** standard.

## Reading an array of N elements

The first line contains `N`, the number of elements.

The next line contains `N` space-separated integers.

```cpp
int N;
std::cin >> N;
std::vector<int> v(N);
std::copy_n(std::istream_iterator<int>(std::cin), N, begin(v));
```

Using `copy_n` is the best choice because we can use it to read more things in sequence:

```cpp
int N1, N2;
std::cin >> N1 >> N2;
std::vector<int> v1(N1);
std::vector<int> v2(N2);
std::copy_n(std::istream_iterator<int>(std::cin), N1, begin(v1));
std::copy_n(std::istream_iterator<int>(std::cin), N2, begin(v2));
```

## Reading strings

We can simply use `std::string`:

```cpp
std::string s;
std::cin >> s;
```

If the string length is introduced first, we can either read it:

```cpp
int N;
std::cin >> N; // not used
std::string s;
std::cin >> s;
```

or ignore it (there are many ways, here is the simplest):

```cpp
std::string s;
std::cin >> s >> s;
```

## Output

We can easily print values and strings by sending them to `cout`:

```cpp
std::cout << value << " " << stringValue << "\n";
```

### Printing arrays

Vectors and arrays are easy to `std::copy` to standard output.

If `v` is a vector or array of `int`s, we can print its content separated by whitespaces this way:

```cpp
std::copy(begin(v), end(v), std::ostream_iterator<int>(std::cout, " "));
```

If we must omit the last whitespace, we can do the following refinement:

```cpp
std::copy(begin(v), std::prev(end(v)), std::ostream_iterator<int>(std::cout, " "));
std::cout << *std::prev(end(v));
```

### Floating point with exact precision

Some challenges require printing floting points with a certain width.

In such cases, we use `std::fixed` in combination with `std::setprecision(numberOfDigits)` can be used.

For instance, suppose we want only two digits after comma:

```cpp
cout << fixed << setprecision(2) << value << "\n";
```

Or suppose we want only one digit after comma:

```cpp
cout << fixed << setprecision(1) << value << "\n";
```
