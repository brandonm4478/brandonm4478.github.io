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

This question is asking "What definition is changing over the repeated expressions below?".

The answers for the question are as follow:

```
(a) (define (bill sub-total)
    (+ (* sub-total 0.0825 sub-total))
      
(b) (+ (* sub-total 0.0825) 82.01))

(c) (define (bill sub-total tax)
    (+ (* sub-total tax) sub-total))
    
(d) (define bill sub-total) 
    (* sub-total 0.0825)
    
(e) None of the above
```
Before we do anything else, we can rule out answer choice B. We can rule out this answer choice because the answer is asking for a definition, and answer choice B does not contain a definition.

After that, we can rule out answer choice D. We can rule this answer choice out because the expressions inside the definition does not match up with the expressions inside the question.

This leaves us with answer choices A and C. The correct answer choice would be A. Answer A would be correct because the definition and expressions in the answer match with the definitions and expressions in the question. In addition, the sub-total value is changing over all of the expressions, and this is defined as a variable in the definition.

Now that the correct answers have been explained, I will be moving on to the other parts of the question.

This question falls under Mastery Skill 5. Mastery Skill 5 talks about solving problems. It also talks about designing a function, identifying variables, and interpreting test cases.

This question is on the skill level of Practicioner (Level 3). I know that because it is a complex question that takes three or more steps to solve.

The majority of students got this question right (34.9%). The second most chosen answer was answer choice C (19.8%). I think they chose this answer because they didn't read the question carefully and they didn't notice that it has an extra parenthesis.
