---
title: "Javascript"
---



## Reading strings

We can read a single line string using the built-in functions `process.stdin`:

To fetch data from a stdin you can use `process.stdin` and send fetching result to a custom parsing function (`parsingFunction`)
Following examples assume you are implementing `parsingFunction` content

```javascript 
process.stdin.resume();
process.stdin.setEncoding("ascii");
let fetchedInput = "";
process.stdin.on("data", function (input) {
    fetchedInput += input;
});

process.stdin.on("end", function () {
  // call here your parsing function
  console.log(fetchedInput);
});

```

## Reading an array of integers

When you need to convert a string of integers (eg. `1 2 3`) to an array of integers `[1, 2, 3]`
each element to an int:

```javascript

parsingFunction = (fetchedInput) => {
  return fetchedInput.split(' ').map((n) => parseInt(n, 10));
}
```

## Reading n rows made up of a single integer


```javascript

parsingFunction = (fetchedInput) => {
  return inputString.split(/\r?\n/)
    .map((line) => line.split(' ')
    .map((number) => parseInt(number, 10)))
  }

```

## Writing on STDOUT

When you need to write on *stdout* use:

```javascript

process.stdout.write('output');

```
