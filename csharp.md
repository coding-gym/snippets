---
title: "C#"
---

## Reading an array of N elements

The first line contains `N`, the number of elements.

The next line contains `N` space-separated integers.

```csharp
int N = Convert.ToInt32(Console.ReadLine());
int[] arr = Array.ConvertAll(Console.ReadLine().Split(' '), Convert.ToInt32);
```
