---
layout: post
title: "Weekly Reflection #11"
date: 2018-11-30
---

This reflection is different from past reflections, as I had a midterm this week and will be talking about it in this post. I will be going over a question on the midterm.

The question I am going over is:

```
Which definition abstracts over the repeated expressions below?

  (+ (* 19.99 0.825) (19.99))
  (+ (* 82.01 0.0825) 82.01))
  (+ (* 10.99 0.0825) 10.99))
```
  
The answers for the question are as follow:

```
(a) (define (bill sub-total)
      (+ (* sub-total 0.0825 sub-total))
(b) (+ (* sub-total 0.0825) 82.01))

(c) (define (bill sub-total tax)
    (+ (* sub-total tax) sub-total))
    
(d) (define bill sub-total) 
    (* sub-total 0.0825)
    
(e) None of the above```
