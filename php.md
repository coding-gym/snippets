---
title: "PHP"
---

## Reading strings

We can read a single line string using the built-in functions `fscanf()` where `%s` operator casts input stream as a string:

```php
$s = '';
fscanf(STDIN, "%s\n", $s);
```

or `fgets()`

```php
$s = trim(fgets(STDIN));
```

## Reading an array of integers

When you need to read an array of integers, you have to read the entire string line and then convert it in array using `explode()` built-in function. For instance, if your input line is `2 10 24 3 5 25`, here is the shippet you'll need:

```php
$line = trim(fgets(STDIN));
$a = array_map('intval', explode(' ', $line));
```

`array_map()` applies `intval()` function as a callback to each string item retrieved by `explode()`.

## Reading $n rows made up of a single integer

Also here you can use `fscanf()` function, but in this case you'll need the `%d` operator to cast input stream as an integer:

```php
$numbers = [];
for ($i = 0; $i < $n; $i++) {
    fscanf(STDIN, "%d\n", $n);
    $numbers[] = $n;
}
```

## Writing on STDOUT

When you need to write your result on *stdout* streaming.

```php
$result = 'my result';
$stdout = fopen('php://stdout', 'w');
fprintf($stdout, $result);
fclose($stdout);
```
