---
Title: "Javascript"
---

## Reading an array on a line

The first line contains `n`, the number of elements.

The next line contains `n` space-separated integers.

```js
const n = parseInt(readLine(), 10);
const arr = readLine().split(' ').map(qTemp => parseInt(qTemp, 10));
```

Since we use readLine, we can easily read different arrays:

```js
const n = parseInt(readLine(), 10);
const arr1 = readLine().split(' ').map(qTemp => parseInt(qTemp, 10));
const arr2 = readLine().split(' ').map(qTemp => parseInt(qTemp, 10));
```
