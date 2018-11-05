---
layout: post
title: "Weekly Reflection #7"
date: 2018-11-02
---

This week was a short week for me in computer science class. We didn't have computer science Wednesday and I was absent Thursday.

On Monday (10/29/2018) we were reviewing how to define our own functions, and this is what we reviewing over the course of the week. To start off we were comparing different expressions in racket and how they are similar and different. This was easy as it was just a change ina  symbol.

Then we got on to the individual parts of a function. The contract (or way a triangle function is setup) of a triangle function is as follows:

```racket
;triangle : Number String String --> Image
```

And an example of the function:

```racket
(triangle 50 "solid" "green")
```

1. The first part of the function, or the *triangle* part is the function name. In the case of our function it is the triangle.
2. The second part of the function, or the *50 "solid" "green"* part is called the domain. 
  * The first part of the domain, or the *number* part is the size of the triangle. This will determine the value that makes how long     the base is and how tall the triangle is
  * The second part of the domain, or the *"solid"* string is the style of the triangle. There are two styles, outline and solid. Solid   will make the triangle filled in in the selected color, and outline will make it an outline in the selected color.
  * The third part of the domain, or the *"green"* string is the color of the triangle.
3. The final part of the string, or the *range*, is what is created when the function is ran.

Below is an example of our function. We made the function gt (green triangle). The contract for it is as follows:
```racket
;gt : Number --> Image
```

You imput a number and out comes a green triangle of that size.

```racket
(define (gt size)(triangle size "solid" "green"))
(gt 50)
```
