---
layout: post
title:      "Recursion vs. Iteration"
date:       2019-03-18 01:52:39 +0000
permalink:  recursion_vs_iteration
---

In functional programming there is a pattern that can be implemented in some situations when a process can be separated into several simpler sub parts. In JavaScript this pattern is specifically used when a function, within its own scope, will call itself. This pattern is called **Recursion**.

Most graduates of Code boot camps or self-taught JavaScript Developers will have a solid understanding of how to loop over datasets to solve algorithm problems. **Iteration** is not always the most ideal option. This is where it is very beneficial to have an alternative approach using recursion.

Deciding which of these techniques to use is a trade-off between time complexity(read my previous blog on Big O notation) and the amount of actual code. If time complexity is the biggest concern, and the input is huge, iteration is a always a better choice. However, if time complexity is not a problem, but the length of code required is, recursion is more ideal.

#### Would you like an Example?

![](https://thumbs.gfycat.com/SelfreliantPiercingCowbird-size_restricted.gif)

Ok! We will see an iterative solution followed by a recursive solution for the following problem: write a function called **powered** that takes in the two arguments `num` and `pow` that raises `num` to a natural power of `pow`(multiplies `num` by itself `pow` times).

```
function powered(num, pow) {
  let result = 1;
  for (let i = 0; i < pow; i++) {
    result *= num;
  }
  return result;
}

powered(2, 3); // 8
```

In the above code we see repetition of a block of code inside the `for` loop. If `pow` was *1,000,000* then the time complexity would be much less here than using recursion. This is because we only repeat what is inside the block of code.

```
function powered(num, pow) {
  if (pow === 1) {
    return num;
  } else {
    return num * powered(num, pow - 1);
  }
}

powered(2, 3); // 8
```

Here we see in the `else` portion of the conditional statement the function is calling itself again and again until `pow === 1`.

In this example both solutions are roughly equal in the amount of code needed. If this problem had been a much more complex and lengthy algorithm we would have seen the recrusive option as more compact solution. For this, recursion is advantageous in that it can produce shorter code. It is very important to forsee what the problem presented requires and what your time and space constraints are before deciding wheather to solve problems using iteration or recursion.




