---
layout: post
title: "Flag Project Documentaton (Weekly Reflection #13)"
date: 2018-12-13
---

This learning blog will focus on the documentation of my Flag Project. The Flag Project is a program on the website WeScheme. Your task is to create a scaleable verison of a assigned Flag. 

<h1>Part 1: The Code</h1>
My flag has a lot of code for it. Here is the code now.


```scheme
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;; FLAG OF AUSTRALIA PROJECT ;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; PROJECT DESCRIPTION: This program makes a scaleable ;;;
; version of the flag of Australia. To change the scale ;
; of the flag, change the value of "australian-scale" ;;;
; (the definition below). The higher the value, the ;;;;;
; bigger the flag will be. This will also scale the ;;;;;
; text and the real flag. In addition, you may need to ;;
;zoom out in order to see the whole flag. ;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

(define australian-scale 1)
; NOTE: This value only works between 0.01-5.1 due to the fact that the text needs an integer
; between 1 and 255. To go around this, you must remove the scaleable code ((* 50 australian-scale))
; from the text functions (lines 34 and 106.)

;; PART 1: DEFINITIONS
; These are the two definitions used for the flag. The values have a sort of "chain of command".
; The width is changed by the value of the australian-scale, and the value of the height is changed
; by the value of the width. This is so the whole program can run off of one value.


(define w (* 600 australian-scale))
(define h (/ w 2))

;; PART 2: CODE 
; The second part of the program is the code. There are multiple "subsections" inside this part.
; The flag is made up of three parts. The backdrop (blue flag), the Union Jack (British Flag inside 
; the canton), and the stars.

;; PART 2A: BACKDROP
; The blue flag.
(text "Australian Flag" (* 50 australian-scale) (make-color 0 0 139))
(define BACKDROP (rectangle w h "solid" (make-color 0 0 139)))

;; PART 2B: UNION JACK (CANTON)
; The British Flag located in the canton (top left).
(define UNION (put-image (rectangle (/ w 20) (/ h 2) "solid" (make-color 255 0 0))
                         (/ w 4) (/ h 4)
                         (put-image 
                          (rectangle (/ w 2) (/ h 10) "solid" (make-color 255 0 0))
                          (/ w 4) (/ h 4)
                          (put-image 
                           (rectangle (/ w 2) (/ h 6) "solid" "white")
                           (/ w 4) (/ h 4)
                           (put-image
                            (rectangle (/ w 12) (/ h 2) "solid" "white")
                            (/ w 4) (/ h 4)
                            (put-image 
                             (rotate 25 (rectangle (/ w 2) (/ h 30) "solid" (make-color 255 0 0))) 
                             (/ w 20) (/ h 26)
                             (put-image
                              (rotate 25 (rectangle (/ w 2) (/ h 30) "solid" (make-color 255 0 0)))
                              (/ w 2) (/ h 2)
                              (put-image
                               (rotate -25 (rectangle (/ w 2) (/ h 30) "solid" (make-color 255 0 0))) 
                               (/ w 2) (/ h 26)
                               (put-image
                                (rotate -25 (rectangle (/ w 2) (/ h 30) "solid" (make-color 255 0 0)))
                                (/ w 26) (/ h 2.3)
                                (put-image
                                 (rotate 25 (rectangle w (/ h 10) "solid" "white"))    
                                 (/ w 4) (/ h 4)
                                 (put-image
                                  (rotate -25 (rectangle w (/ h 10) "solid" "white"))  
                                  (/ w 4) (/ h 4)
                                  (rectangle (/ w 2) (/ h 2) "solid" (make-color 0 0 139)))))))))))))

;; PART 2C: COMBING PARTS
; This part puts the Union Jack in the canton area of the backdrop.
(define FLAG1 (overlay/align "left" "top"
                             UNION
                             BACKDROP))

;; PART 2D: STARS
; This final part is just creating the stars for the flag and then putting them ontop of the backdrop.
(put-image 
 (rotate 3 (radial-star 7 (/ w 30) (* h 0.15) "solid" "white"))
 (/ w 4) (/ h 4) 
 (put-image
  (rotate -7 (radial-star 5 (* (* h 0.04166666666) 0.4444444444) (* h 0.04166666666) "solid" "white"))
  (* w 0.8) (* h 0.45833333333)
  (put-image
   (rotate 3 (radial-star 7 (* (* h 0.07142857142) 0.4444444444) (* h 0.07142857142) "solid" "white"))
   (* w 0.75) (* h 0.16666666666)
   (put-image 
    (rotate 3 (radial-star 7 (* (* h 0.07142857142) 0.4444444444) (* h 0.07142857142) "solid" "white"))
    (/ w 1.6) (/ h 1.77777777778)
    (put-image 
     (rotate 3 (radial-star 7 (* (* h 0.07142857142) 0.4444444444) (* h 0.07142857142) "solid" "white"))
     516.666666666 188.749999998
     (put-image 
      (rotate 3 (radial-star 7 (* (* h 0.07142857142) 0.4444444444) (* h 0.07142857142) "solid" "white"))
      (/ w 1.3333333333) (/ h 1.2)
      FLAG1))))))

(rectangle 0 50 "solid" "white")


;; PART 3: THE REAL FLAG
; I put a version of the real Australian flag. It was mainly for reference while coding, but I 
; am leaving it here for comparison.
(text "Real Australia Flag" (* 50 australian-scale) (make-color 0 0 139))
(scale (* australian-scale 0.47) (bitmap/url "https://upload.wikimedia.org/wikipedia/en/b/b9/Flag_of_Australia.svg"))
```


There are coments inside the code that document what each part means. These comments will eventually be transfered to another document and simpler comments will be inserted.

The way the program works is that if you change the value of australian-scale, it will multiply the flag's size by that number. Here is what the flag looks like at a scale of 1 (ratio 1:2).
![Flag of Australia](/img/Flag_of_Australia.png)

<h1>Part 2: Reflection</h1>
I will now answer some reflection questions about this project.

**1a. What are some questions you had during the project or currently have?**  
Some questions I had during the project were:
- How do I scale my image?
- How do I make 7-pointed stars?
- These stripes start at one hight, disappear, and reappear at another hight. Is there a way to make this one rectangle, or do I have to make it two rectangles?

Some questions I have now:
- Do I need to change everything into variables or can I keep the program as is?
- Is there any way to link two programs together. For example, if I have the code for the flag in one program, can I link it to another program and put the variable that makes the flag appear (FLAG) and will it appear without any code being there?

**1b. What are some challenges you had during the project or currently have?**  
Some challenges I had during the project were:
- The function I was using for 7-pointed stars was not making the stars look proper. To get around this I switched from the star-polygon function to the radial-star function.
- There was a stripe I had in the Union Jack that ended at one height, disappeared, and started again at a different height that didn't make sense. I tried to make this one long rectangle, but that did not work. I had to make two rectangles for each of those stripes.

As I have finished, I do not have any challenges anymore.

**1c. What are some opportunites you got during the project?**  
Some opportunities I got during the project were:
- I learned about how to scale an image.
- I further expanded my understanding of ratios.
- I learned new functions like radial-star and overlay/align. 

**2. What are you looking forward to doing next week?**  
Next week I am looking forward to constructing a physical version of my flag. I am also changing some things inside the program, but I am not looking towards that because it will be tedious and repetitive.
