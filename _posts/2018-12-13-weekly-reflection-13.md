---
layout: post
title: "Flag Project Documentaton (Weekly Reflection #13)"
date: 2018-12-13
---

This learning blog will focus on the documentation of my Flag Project. The Flag Project is a program on the website WeScheme. Your task is to create a scaleable verison of a assigned Flag. 

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

There are coments inside the code that document what each part means.

