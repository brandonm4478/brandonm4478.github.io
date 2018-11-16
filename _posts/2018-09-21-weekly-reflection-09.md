---
layout: post
title: "Weekly Reflection #9"
date: 2018-11-16
---
This week we reviewed functions and definitions. On Tuesday we practiced defining different strings. After that, we reviewed some more stuff about functions. One thing I learned is that the values of a function are dynamic (they can change) and the values of a definition are static (they cannot change).

We also reviewed how contracts, examples and definitions relate to one another. An example function is:

```racket
(define (ys size) (star size "solid" "yellow"))
```
The function above creates a star with the chosen size. The contract for the function is as follows.

```racket
;ys : Number → Image
```

Some examples for the function are as follows:

```
(ys 50) 
(ys 75)
```

All of the above things relate to each other. The way the contract relates to the function is it shows you the type of data needed for the function, and the template you need to follow when you use this function.

An example relates to the contract because it shows you what a filled in version of the contract would look like. It also relates to the contract because it is an example of the function (as the name says).

The function relates to the contract and examples because it is the code for these things.

On Thursday we got a scenario “A rocket blasts off. How else could we model this situation? What else would you like to know?”. A way I believed we could model this situation is a data table with one column for thrust and another column for distance traveled.
 
