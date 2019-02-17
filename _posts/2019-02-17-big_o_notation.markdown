---
layout: post
title:      "Big O Notation"
date:       2019-02-17 20:45:04 +0000
permalink:  big_o_notation
---

I've been recently getting into working alot with algorithms and have discovered a very important term used to classify them called "Big O Notation". "Big O Notation" is a way to measure an algorithms running time or space requirements. Knowing the fastest solution for solving a problem is essential to becoming an excellent programmer.

### Time Complexity

![https://giphy.com/gifs/sherlock-bbc-one-l0MYGtCMbPTYWOzaU](https://media.giphy.com/media/l0MYGtCMbPTYWOzaU/200.gif)

When input data grows for an algorithm how does that effect amount of time it takes the algorithm to run? Does the time grow evenly with the amount of data? Does it stay the same? Or is the time multiplied by itself each time the input increases? "Big O Notation" is used to be able to decipher the time complexity or efficiency, of the algorithm. It does this using “O” and “n”, example: “O(n)”. The "O" refers to the order of the function, or its growth rate, and "n" is the length of the array that is to be sorted.

![https://www.hackerearth.com/practice/notes/big-o-cheatsheet-series-data-structures-and-algorithms-with-thier-complexities-1/](https://he-s3.s3.amazonaws.com/media/uploads/ece920b.png)

### An Example

Let's say we are faced with a simple JavaScript challenge request: write a function called **addUpTo** that calculates the sum of all numbers from 1 up to a given number. Below we can see two different solutions to the problem that produce the exact same outcome yet one is more efficient than the other.

#### Solution 1:

```
function addUpTo(number) {
   let total = 0;
   for(let i = 1; i <= number; i++) {
      total += i;
   }
   return total;
}
```

#### Solution 2:

```
function addUpTo(number) {
   return number * (number + 1) / 2;
}
```

In Solution 1 we are using a loop. Loops are automatically labeled as O(n) because loops contain operations that are called on each item of an array. In this case if the input number is **5** the loop operations are called five times and if the input number is **1,000,000** then the operations are called one million times.

Solution 2 has only three operations: multiply `*`, add `+`, and divide `/`. No matter how large the input number gets there will only be these three operations and therefore it is classified as O(1).

### Why know Big O?

Studying "Big O Notation" is a gateway to comprehending the very important concept of efficiency in your code. While working with large sets of data, it is crucial to pinpoint where major slowdowns could surface. It is a very important part of problem solving and writing great software. Companies want to hire great problem solvers and will put their interviewees to the test. Increasing knowledge on concepts like Big O Notation are a way to separate yourself from the vast pool of junior level developers and will help to land that first job.


