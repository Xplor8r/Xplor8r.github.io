---
layout: post
title:      "JavaScript Refresher: Scope and Hoisting"
date:       2019-01-11 23:43:30 -0500
permalink:  javascript_refresher_scope_and_hoisting
---

In JavaScript it may seem like scope is a very basic and easy thing to grasp but it could be something all JS developers, junior to senior, will repeatedly run into problems with. Variables in JavaScript are declared using the `var`, `let`, or `const` and where they are called dictates it's scope. If `var` is declared in the global context, it is in the global scope. This is where variables can become a bit buggy, and it's best to never use `var` in a global context.

>The worst of all of JavaScript's bad features is its dependence on global variables. A *global  variable* is a variable that is visible in every scope. Global variables can be a convenience in very small programs, but they quickly become unwieldy as programs get larger.
>
>  -Douglas Crockford, JavaScript: The Good Parts

The block of code where a variable or argument is declared determines its scope. When using `let` or `const`, the scope of a variable is the block in which it is declared. When calling `var` in a `for` loop block will assign the variable to the scope of the nearest enclosing function. This is a JavaScript feature called hoisting.

Lets see this in action below.

```
function zeroOneTwoThree() {
  for (var i = 0; i < 3; i++){
    console.log(i)
  }
  console.log(i);
}

zeroOneTwoThree();
// =>0
// =>1
// =>2
// =>3
```

The above `for` loop will `console.log` the value of `i` for each iteration. Though `i` is declared inside the scope of the `for` loop, with hoisting `i` actually belongs to `zeroOneTwoThree`’s scope. 

Hoisting basically is when JavaScript moves all variable and function declarations to the top of the current scope. It is important to note that only the actual declarations are hoisted. Any assignments are left where they are.

Taking a look at a few examples below we can examine scope and hoisting further.

**FUN FACT: commonly used by programmers, the terms foo and bar originate from the WWII slang word FUBAR which was famously used in the 1989 film Tango and Cash**

```
function fubar() {
  var fu = 1;
  var bar = 2;

  console.log(fu + " " + bar);
}

fubar();

// => 1 2
```

We see above a simple function with two variables defined above a `console.log` method within a function. The output value is as expected. But what happens if `var bar` is moved below the `console.log` method?

```
function fubar() {
  var fu = 1;
  console.log(fu + " " + bar);
  var bar = 2;
}
fubar();
// => 1 undefined
```

![](https://i.imgur.com/GCNcXBz.gif?noredirect)

**Oops!**

Now we see that `var bar` doesn't show up in `console.log`'s radar yet and sees the value of `bar` as undefined. Now we will declare our variables above the `console.log` yet assign `var bar` below and see what happens.

```
function fubar() {
  var fu;
  var bar;
  fu = 1;
  console.log(fu + " " + bar);

  bar = 2;
}
fubar();
// => 1 undefined
```

![](https://i.imgur.com/GCNcXBz.gif?noredirect)

In this case we are still seeing the same result(unhappy Tango). Though both variables are declared `bar` isn't assigned yet when the `console.log` method is called.

Function hoisting is a more useful tool for programming but there are still a couple of things to remember. Functions that are assigned to variables are not hoisted. In the following code we attempt function declaration hoisting.

```
tango();

function tango() {
  console.log("He thinks he's Rambo!");
}
// => "He thinks he's Rambo!"
```

![](https://66.media.tumblr.com/242a874e16f002d9a5c2d8b58a218409/tumblr_oucipwnNvF1qhu2ibo5_400.gif)

**Sweet!**

This time let's see what happens if the variable declaration for `tango` is hoisted before the function call in the following code. 

```
tango();

var tango = function() {
  console.log("He thinks he's Rambo!");
};
// =>
```

![](https://i.imgur.com/GCNcXBz.gif?noredirect)

**Nothing!**

Since the assignment to `tango` is not hoisted, an exception is thrown for trying to call a non-function variable.

In conclusion, scope and hoisting are two very important concepts to grasp when working with JavaScript. To avoid dealing with bugs(and being an unhappy Tango) it is good practice to use `let` and `const`. By single variable declaration at the top of any particular scope you can increase your chances of writing stress free(happy Cash) code.
