### Code and Notes from First Day of Class (Sept. 4th, 2019)

#### See Admin Notes on Website (https://www.students.cs.ubc.ca/~cs-311)

``` scheme
#lang plai

; Lecture 01.
; Welcome to CPSC 311!!
; Our goal is to refresh on Racket, getting to a sorting function.

; Numbers:

1
12
12.4
(/ 1 2) ; -> 1/2 fraction type


; (Racket has EXPRESSIONS, not statements.  Everything can nest.)

;other data:  symbols, strings, booleans
; SYMBOLS allow fast checking of string-like tokens - will be useful later on
'hello
'hi123

"This is a string"

#t
#f

; Tons of equality tests, with slightly different semantics (meaning).

(= 1 2) ; only works for numbers (decimals and ints are fine)

(equal? #t #f)

(equal? "string" 'symbol)


; How does it work?
; (a b c): apply (eval of..) a to b and c.

; FIRST COOL THING, procs are values:


+
-
=


; Control flow:
(if  _condition_   _then_   _else_)
; _else_ expression ONLY evaluated if _condition_ is #f


; Sorting needs a list!  
; LISP = list processing
; Compare linked lists: cons constructs list cell; empty is final tail

empty
(cons 1 empty)
(list 1 2 3)

; SECOND COOL THING: heart of syntax also core data structure!


'(1 2 3)

(list 1 (+ 2 3) 4)

'(1 (+ 2 3) 4)


; Back to lists.

; Sort?  Need functions!


(define f
  (lambda (x) x))

(define (my-or a b)
  (or a b))


; x is not a variable in the sense that we "vary" its value
; from the initial value. (Mostly, we won't use mutation!)


(or #f (/ 1 0)) ; RESULT: #t (division does not need to be evaluated)
(my_or #t (/ 1 0)) ; ERROR: division by zero (evald then passed to function)


; Our style for functions:
; CONTRACT/PURPOSE/TESTS/SKELETON

;; sort : (listof number) -> (listof number)
;; Consumes a list of numbers and generates a list of the same numbers,
;; except in sorted order.
(define (sort nums)
  nums)

; And tests:
(test (sort '(1 2 3 4)) '(1 2 3 4))
(test (sort empty) empty)
(test (sort '(3 2 1 0)) '(0 1 2 3))
(test (sort '(1)) (sort '(1)))
(test (sort '(-9 5 2 15)) '(-9 2 5 15))


; Why COOL: procs are values?

;; sort : (X X -> boolean) (listof X) -> (listof X)
;; Consumes a procedure to compare X's and a list of X's and
;; generates a new list of the same X's, sorted by comparator.
(define (sortX comparator lox)
  lox)  ;stub!!!

;; insert : (X X -> boolean) X (listof X) -> (listof X)
;; Consumes a comparator, an X and a sorted list of X's and 
;; generates a sorted list of all the things in the original list plus the extra thing.
(define (insertX comparator x lox)
  (cons lox x)) ;stub!!!

; Now, let's go back up and redefine sort.

; How about sort by closest to a given value?

;; sort-closest-to : number (listof number) -> (listof number)
;; Consumes a target value and a list of numbers and generates
;; a list of the same numbers sorted by increasing absolute 
;; distance from the target.
(define (sort-closest-to x lon)
  (sortX
   (lambda (a b)
     (< (abs (- a x))
        (abs (- b x))))
   lon))

; LAMBDA! 
; WHERE is x COMING FROM inside the lambda?
```