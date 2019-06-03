---
title: "Rust"
---

## Premise

At to date, HackerRank does not give you anything more than a _Write you code here_. If you take into account that the version of the compiler is a bit old, it is a bit slow to compile, no completion or rustfmt... It is not exactly a pleasure to code in Rust on HackerRank.

So... let's open your favorite IDE/Editor on steroids and copy-paste your solution to HR! You can also try [The Rust Playground](https://play.rust-lang.org/)! :wink:

## A starting point

Maybe the empty prompt is a bit... too empty. Here something better:

```rust
fn main() {
  use std::io;

  let stdin = io::stdin();
  let mut stdin_lock = stdin.lock();

  // Play with your `stdin_lock`!
}
```

## Reading an array of N elements

A classic: the first line contains `N`, the number of elements. The next line contains `N` space-separated integers.

Let's try the _easy_ way:

```rust
fn main() {
    use std::io::{self, BufRead};

    let stdin = io::stdin();

    let mut lines = stdin.lock().lines().map(Result::unwrap);
    let n_elements: usize = lines.next().unwrap().parse().unwrap();
    let elements: Vec<i32> = lines
        .next()
        .unwrap()
        .split(' ')
        .map(|x| x.parse().unwrap())
        .collect();
    assert_eq!(n_elements, elements.len());
}
```

Ouch! In real-life problems, Rust's explicit error handling is awesome, but in this case it is just cumbersome.

We can write down a small set of utility functions, that can help us in many HR exercises. Here a practical example:

```rust
use std::{fmt::Debug, iter::FromIterator, str::FromStr};

fn parse_line_into<T, L>(lines: &mut L) -> T
where
    L: Iterator<Item = String>,
    T: FromStr,
    <T as FromStr>::Err: Debug,
{
    lines.next().unwrap().parse().unwrap()
}

fn next_parsed_line<C, T, L>(lines: &mut L) -> C
where
    L: Iterator<Item = String>,
    C: FromIterator<T>,
    T: FromStr,
    <T as FromStr>::Err: Debug,
{
    lines
        .next()
        .unwrap()
        .split(' ')
        .map(|x| x.parse().unwrap())
        .collect()
}
```

It is a bit of boilerplate, but it can be easily reusable. And the main becomes cleaner:

```rust
fn main() {
    use std::io::{self, BufRead};

    let stdin = io::stdin();

    let mut lines = stdin.lock().lines().map(Result::unwrap);
    let n_elements: usize = parse_line_into(&mut lines);
    let elements: Vec<i32> = next_parsed_line(&mut lines);
    assert_eq!(n_elements, elements.len());

    // Use elements!
}
```

## Collect all the things!!!

Remember that most of the time `collect` is your friend! Do you need to collect numbers in a `BTreeSet`?

```rust
let elements: BTreeSet<i32> = next_parsed_line(&mut lines);
```

Easy!!!

## Output

In Rust, printing is pretty easy thanks to `println!` macro:

```rust
println!("This is a string: {}", the_string);
println!("This is a vector, debug style: {:?}", the_vec);
println!("This is a pretty printed vector: {:#?}", the_vec);
println!("This is a float with 16 precision digits: {:.16}", the_float);
```
