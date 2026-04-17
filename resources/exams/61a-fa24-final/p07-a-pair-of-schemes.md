---
course: CS61A
term: Fall 2024
assessment: Final
source_pdf: 61a-fa24-final_sol.pdf
exam_slug: 61a-fa24-final
problem_number: 7
problem_title: "A Pair of Schemes"
page_range: [17, 19]
points: "14.0 points"
topics: ["scheme", "lists"]
concepts: ["scheme", "lists"]
question_types: ["implementation"]
difficulty: "hard"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 7 — A Pair of Schemes

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** scheme, lists
- **Concepts:** scheme, lists
- **Question types:** implementation
- **Difficulty:** hard
- **Source pages:** 17-19

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: Final
- Source PDF: `61a-fa24-final_sol.pdf`

## Full extracted content

## Page 17

7. (14.0 points)
A Pair of Schemes
(a) (4.0 points)
Implement the Scheme procedure all-pairs, which takes a procedure f and a list s. It returns #t if (f x
y) is #t for every pair of adjacent elements x and y in s. Assume f always returns either #t or #f.
(define (inc x y) (= (+ x 1) y))
; Whether x+1 equals y
;;; Return #t if (f x y) is #t for every pair of adjacent values (x, y) in list s.
;;;
;;; scm> (all-pairs inc '(3 4 5 6 7 8))
;;; #t
;;; scm> (all-pairs inc '(3 4 5 8 7 8))
;;; #f
;;; scm> (all-pairs inc '(3))
;;; #t
(define (all-pairs f s)
(or (null? s) (null? (cdr s))
(and _______ (all-pairs f _______ ))))
(a)
(b)
i. (3.0 pt) Fill in blank (a). Select all correct answers.
2 (car s) (cdr s)
2 (car s) (car (cdr s))
2 f (car s) (cdr s)
2 f (car s) (car (cdr s))
2 f((car s) (cdr s))
2 f((car s) (car (cdr s)))
2 (f (car s) (cdr s))
■(f (car s) (car (cdr s)))
2 (apply f (car s) (cdr s))
2 (apply f (car s) (car (cdr s)))
ii. (1.0 pt) Fill in blank (b).
# s
(cdr s)
# (cdr (cdr s))
# (cons (car s) (cdr s))
# (cons (car s) (cdr (cdr s)))

## Page 18

(b) (6.0 points)
Implement the Scheme procedure show-pairs, which takes a list s and returns a list of every pair of
adjacent elements in s. A pair is a two-element list.
;;; Return a list of every pair of adjacent elements in list s.
;;;
;;; scm> (show-pairs '(3 5 7 9 11 13))
;;; ((3 5) (5 7) (7 9) (9 11) (11 13))
(define (show-pairs s)
(if (or (null? s) (null? (cdr s))) nil
( _______ _______ (show-pairs _______ ))))
(a)
(b)
(c)
i. (1.0 pt) Fill in blank (a).
# car
# cdr
cons
# list
# append
ii. (3.0 pt) Fill in blank (b).
(list (car s) (car (cdr s)))
iii. (1.0 pt) Fill in blank (c).
# s
(cdr s)
# (cdr (cdr s))
# (cons (car s) (cdr s))
# (cons (car s) (cdr (cdr s)))
iv. (1.0 pt) What order of growth describes the time it takes to execute (unpair s) in terms of the
length of the input list s, assuming that car, cdr, cons, and null? are all constant-time operations?
(define (unpair s) (cond ((null? s) nil)
((null? (cdr s)) (car s))
(else (cons (car (car s)) (unpair (cdr s))))))
# constant
# logarithmic
linear
# quadratic
# exponential

## Page 19

(c) (4.0 points)
Implement the Scheme procedure all-pairs-exp, which takes a procedure name proc-name (a symbol)
and a list s. It returns an and expression that calls the procedure named by proc-name on every adjacent
pair of elements in s. Assume show-pairs is implemented correctly.
;;; Return an and expression that calls the procedure called proc-name on
;;; every adjacent pair of elements in s.
;;;
;;; scm> (all-pairs-exp 'inc '(3 4 5 6 7 8))
;;; (and (inc 3 4) (inc 4 5) (inc 5 6) (inc 6 7) (inc 7 8))
;;; scm> (eval (all-pairs-exp 'inc '(3 4 5 6 7 8 )))
;;; #t
(define (all-pairs-exp proc-name s)
( _______ (map _______ (show-pairs s))))
(a)
(b)
i. (1.0 pt) Fill in blank (a).
# and
# 'and
# cons and
cons 'and
ii. (3.0 pt) Fill in blank (b).
(lambda (pair) (cons proc-name pair))
or
(lambda (pair) (list proc-name
(car pair) (car (cdr pair))))


---

## Same Semester

- [61a-fa24-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa24-final / P02-LINE-DIAGRAM](p02-line-diagram.md)
- [61a-fa24-final / P03-MAKE-TENS](p03-make-tens.md)
- [61a-fa24-final / P04-COUNT-MISSES](p04-count-misses.md)
- [61a-fa24-final / P05-PROMOTION-TO-CS-61B](p05-promotion-to-cs-61b.md)
- [61a-fa24-final / P06-FRESH-PRODUCE](p06-fresh-produce.md)
- [61a-fa24-final / P08-ARCANE-JOBS](p08-arcane-jobs.md)
- [61a-fa24-final / P09-APE-PULL-US](p09-ape-pull-us.md)
- [61a-fa24-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa24-mt1/p01-what-would-python-display.md)
- [61a-fa24-mt1 / P02-WHICH-ONE](../61a-fa24-mt1/p02-which-one.md)
- [61a-fa24-mt1 / P03-FINAL-DIGIT](../61a-fa24-mt1/p03-final-digit.md)
- [61a-fa24-mt1 / P04-CLOSE-ENOUGH](../61a-fa24-mt1/p04-close-enough.md)
- [61a-fa24-mt1 / P05-SHIFTY](../61a-fa24-mt1/p05-shifty.md)
- [61a-fa24-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa24-mt2/p01-what-would-python-display.md)
- [61a-fa24-mt2 / P02-PIZZA-BY-THE-SLICE](../61a-fa24-mt2/p02-pizza-by-the-slice.md)
- [61a-fa24-mt2 / P03-CS-61A-SOFTWARE-STORE](../61a-fa24-mt2/p03-cs-61a-software-store.md)
- [61a-fa24-mt2 / P04-ALMOST-A-PERFECT-QUESTION](../61a-fa24-mt2/p04-almost-a-perfect-question.md)
- [61a-fa24-mt2 / P05-HOW-LONG-IS-THIS-EXAM](../61a-fa24-mt2/p05-how-long-is-this-exam.md)
- [61a-fa24-mt2 / P06-NICE-PATH](../61a-fa24-mt2/p06-nice-path.md)
