
---
layout: post
title: "Flag Project - Final Submission"
date: 2018-12-21
---

# Flag of _Australia_ by _Brandon Morgenstein_

## Program Description
**1. What country did you design for?**  
I designed my flag for Australia.
  
**2. What grade do you expect?**  
I expect a 3 out of 4 because while my flag is scaleable and geometrically accurate, it does not 100% use definitions.

## Current program output

* * *
![Flag of Australia - Final](/img/Flag_of_Australia_final.png)
* * *

## Development Process
**1. What are some questions, strategies, help from peers or teachers, or thinking that got you to this point?**  
**1a. Questions**  
How do I scale this image?  
Is this line two lines or one?  

**1b. Strategies**  
A strategy I used was to copy and paste the code for a star and change the coordinates, as most of my stars had the same size.  

**1c. Help fom others**  
I got help from Mr. Allatta. He helped teach me how to scale an image, and he helped me by explaining some ideas I had for the project.  

## Explaining the Code
* * *
```scheme
(define FLAG1 (overlay/align "left" "top"
                             UNION
                             BACKDROP))

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

(put-image 
 (rotate 3 (radial-star 7 (/ w 30) (* h 0.15) "solid" australia-white))
 (/ w 4) (/ h 4) 
 (put-image
  (rotate -7 (radial-star 5 (* (* h 0.04166666666) 0.4444444444) (* h 0.04166666666) "solid" australia-white))
  (* w 0.8) (* h 0.45833333333)
  (put-image
   (rotate 3 (radial-star 7 (* (* h 0.07142857142) 0.4444444444) (* h 0.07142857142) "solid" australia-white))
   (* w 0.75) (* h 0.16666666666)
   (put-image 
    (rotate 3 (radial-star 7 (* (* h 0.07142857142) 0.4444444444) (* h 0.07142857142) "solid" australia-white))
    (/ w 1.6) (/ h 1.77777777778)
    (put-image 
     (rotate 3 (radial-star 7 (* (* h 0.07142857142) 0.4444444444) (* h 0.07142857142) "solid" australia-white))
     516.666666666 188.749999998
     (put-image 
      (rotate 3 (radial-star 7 (* (* h 0.07142857142) 0.4444444444) (* h 0.07142857142) "solid" australia-white))
      (/ w 1.3333333333) (/ h 1.2)
      FLAG1))))))
```
* * *

**Code Explanation**
The code above has two parts. The first part (overlay/align) overlays the Union Jack flag in the top left of the blue background (Canton).  

The bottom part of the code (seperated by a line of comments) is for the stars. It puts one star ontop of another star putting itself on another star, and so on. The way the math for the star works is that it multiplies the scale of the star by the flag width to get the outer diameter. Then I multiply that value by the scale of the inner diameter.

This code is independent from the rest of the flag. While it creates the stars for the flag, by itself it only creates stars.

## Program code
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

(define australia-blue (make-color 0 0 139))
(define australia-red (make-color 255 0 0))
(define australia-white (make-color 255 255 255))

(define text-scale (* 50 australian-scale))
(define image-scale (* australian-scale 0.47))

;UNION JACK DEFINITIONS
(define big-cross-y (rectangle (/ w 20) (/ h 2) "solid" australia-red))
(define big-cross-x (rectangle (/ w 2) (/ h 10) "solid" australia-red))
(define white-cross-x (rectangle (/ w 2) (/ h 6) "solid" australia-white))
(define white-cross-y (rectangle (/ w 12) (/ h 2) "solid" australia-white))

(define red-left-diagonal-bottom (rotate 25 (rectangle (/ w 2) (/ h 30) "solid" australia-red)))
(define red-right-diagonal-top (rotate 25 (rectangle (/ w 2) (/ h 30) "solid" australia-red))) 
(define red-right-bottom (rotate -25 (rectangle (/ w 2) (/ h 30) "solid" australia-red)))

;; PART 2: CODE 
; The second part of the program is the code. There are multiple "subsections" inside this part.
; The flag is made up of three parts. The backdrop (blue flag), the Union Jack (British Flag inside 
; the canton), and the stars.

;; PART 2A: BACKDROP
; The blue flag.
(text "Australian Flag" text-scale australia-blue)
(define BACKDROP (rectangle w h "solid" australia-blue))

;; PART 2B: UNION JACK (CANTON)
; The British Flag located in the canton (top left).
(define UNION (put-image big-cross-y
                         (/ w 4) (/ h 4)
                         (put-image 
                          big-cross-x
                          (/ w 4) (/ h 4)
                          (put-image 
                           white-cross-x
                           (/ w 4) (/ h 4)
                           (put-image
                            white-cross-y
                            (/ w 4) (/ h 4)
                            (put-image 
                             red-left-diagonal-bottom
                             (/ w 20) (/ h 26)
                             (put-image
                              red-right-diagonal-top
                              (/ w 2) (/ h 2)
                              (put-image
                               red-right-bottom 
                               (/ w 2) (/ h 26)
                               (put-image
                                (rotate -25 (rectangle (/ w 2) (/ h 30) "solid" australia-red))
                                (/ w 26) (/ h 2.3)
                                (put-image
                                 (rotate 25 (rectangle w (/ h 10) "solid" australia-white))    
                                 (/ w 4) (/ h 4)
                                 (put-image
                                  (rotate -25 (rectangle w (/ h 10) "solid" australia-white))  
                                  (/ w 4) (/ h 4)
                                  (rectangle (/ w 2) (/ h 2) "solid" australia-blue))))))))))))

;; PART 2C: COMBING PARTS
; This part puts the Union Jack in the canton area of the backdrop.
(define FLAG1 (overlay/align "left" "top"
                             UNION
                             BACKDROP))

;; PART 2D: STARS
; This final part is just creating the stars for the flag and then putting them ontop of the backdrop.
(put-image 
 (rotate 3 (radial-star 7 (/ w 30) (* h 0.15) "solid" australia-white))
 (/ w 4) (/ h 4) 
 (put-image
  (rotate -7 (radial-star 5 (* (* h 0.04166666666) 0.4444444444) (* h 0.04166666666) "solid" australia-white))
  (* w 0.8) (* h 0.45833333333)
  (put-image
   (rotate 3 (radial-star 7 (* (* h 0.07142857142) 0.4444444444) (* h 0.07142857142) "solid" australia-white))
   (* w 0.75) (* h 0.16666666666)
   (put-image 
    (rotate 3 (radial-star 7 (* (* h 0.07142857142) 0.4444444444) (* h 0.07142857142) "solid" australia-white))
    (/ w 1.6) (/ h 1.77777777778)
    (put-image 
     (rotate 3 (radial-star 7 (* (* h 0.07142857142) 0.4444444444) (* h 0.07142857142) "solid" australia-white))
     516.666666666 188.749999998
     (put-image 
      (rotate 3 (radial-star 7 (* (* h 0.07142857142) 0.4444444444) (* h 0.07142857142) "solid" australia-white))
      (/ w 1.3333333333) (/ h 1.2)
      FLAG1))))))

(rectangle 0 50 "solid" australia-white)


;; PART 3: THE REAL FLAG
; I put a version of the real Australian flag. It was mainly for reference while coding, but I 
; am leaving it here for comparison.
(text "Real Australia Flag" text-scale australia-blue)
(scale image-scale (bitmap/url "https://upload.wikimedia.org/wikipedia/en/b/b9/Flag_of_Australia.svg"))
```
