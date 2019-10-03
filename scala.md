---
title: "Scala"
---

## Reading line

We can read a single line string using the built-in method `readLine` from `scala.io.StdIn`:

```scala
import scala.io.StdIn._

val input: String = readLine
```

## Reading a list of integers

When you need to read a list of integers, you have to read the entire line, split it and the convert
each element to an int:

```scala
import scala.io.StdIn._

val listOfNumbers: List[Int] = readLine.split(" ").map(_.toInt)
```

## Reading first line with n, where n is number of rows made up of a single integer

```scala
import scala.io.StdIn._

val listOfNumbers: List[Int] = List.fill(readInt)(readLine).map(_.toInt)
```

## Reading first line with n, where n is number of rows made up of integers

```scala
import scala.io.StdIn._

val listOfListOfNumbers: List[List[Int]] = List.fill(readInt)(readLine.split(" ").map(_.toInt))
```

## Writing on STDOUT

When you need to write on *stdout* use:

```scala
println("some text")
```