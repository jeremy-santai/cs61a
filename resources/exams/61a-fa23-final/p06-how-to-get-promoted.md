---
course: CS61A
term: Fall 2023
assessment: Final
exam_slug: 61a-fa23-final
problem_number: 6
problem_title: "How to Get Promoted"
topics: ["higher-order-functions", "lists"]
---

# Problem 6 — How to Get Promoted

## Full Extracted Content
## Page 17

6. (5.0 points)
How to Get Promoted
Implement promote, which takes a one-argument procedure f and a list s. It returns a list that begins with all
of the elements of s for which calling f on the element returns #t, followed by all of the elements of s for which
calling f on the element returns #f. Assume that when f is called on any element of s, it returns either #t or
#f.
;;; Return a list containing all the elements of s, with the elements for which
;;; f returns #t at the front of the list, but otherwise keeping the order the same.
;;;
;;; scm> (promote even? '(1 2 3 4 5 6 7))
;;; (2 4 6 1 3 5 7)
;;; scm> (promote odd?
'(1 2 3 4 5 6 7))
;;; (1 3 5 7 2 4 6)
(define (promote f s)
(_______ _______ (filter _______ s)))
(a)
(b)
(c)
(a) (1.0 pt) Fill in blank (a).
append
# cons
# list
# promote
# map
# filter
(b) (2.0 pt) Fill in blank (b).
(filter f s)
(c) (2.0 pt) Fill in blank (c).
(lambda (x) (not (f x)))

## Page 18

(d)
This is an A+ question. It is not worth any points. It is not the last question on the exam.
Implement bigger-first without writing lambda or define. You may use promote, curry, and
curry-call.
(define (curry f) (lambda (x) (lambda (y) (f x y))))
(define (curry-call f) (lambda (x g) (lambda (y) (f (x (g y)) y))))
;;; (bigger-first s) returns a list with all of the elements of s larger than (car s)
;;; at the front, followed by all of the elements of s smaller or equal to (car s).
;;;
;;; scm> (bigger-first '(3 1 4 1 5 9 2 6))
;;; (4 5 9 6 3 1 1 2)
(define bigger-first _______)
((curry-call promote) (curry <) car)


---

## Same Semester

- [61a-fa23-final / P01-COPYING-COPIES](p01-copying-copies.md)
- [61a-fa23-final / P02-PATH-MATH](p02-path-math.md)
- [61a-fa23-final / P03-TALK-LIKE-A-PIRATE-DAY](p03-talk-like-a-pirate-day.md)
- [61a-fa23-final / P04-SIX-PAGES-OF-PAIRINGS-SO-PLEASE-READ-THE-DEFINITION-CAREFULLY](p04-six-pages-of-pairings-so-please-read-the-definition-carefully.md)
- [61a-fa23-final / P05-WHAT-WOULD-SCHEME-DO](p05-what-would-scheme-do.md)
- [61a-fa23-final / P07-DON-T-SKIP-THIS](p07-don-t-skip-this.md)
- [61a-fa23-final / P08-CHEAP-DONUTS](p08-cheap-donuts.md)
- [61a-fa23-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa23-mt1/p01-what-would-python-display.md)
- [61a-fa23-mt1 / P02-AN-ODD-IMPLEMENTATION-OF-EVEN](../61a-fa23-mt1/p02-an-odd-implementation-of-even.md)
- [61a-fa23-mt1 / P03-IN-YOUR-PRIME](../61a-fa23-mt1/p03-in-your-prime.md)
- [61a-fa23-mt1 / P04-CHOOSE-WISELY](../61a-fa23-mt1/p04-choose-wisely.md)
- [61a-fa23-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa23-mt2/p01-what-would-python-display.md)
- [61a-fa23-mt2 / P02-MAKING-A-LIST-CHECKING-IT-TWICE](../61a-fa23-mt2/p02-making-a-list-checking-it-twice.md)
- [61a-fa23-mt2 / P03-24-HOUR-LIBRARY](../61a-fa23-mt2/p03-24-hour-library.md)
- [61a-fa23-mt2 / P04-A-PERFECT-QUESTION](../61a-fa23-mt2/p04-a-perfect-question.md)
- [61a-fa23-mt2 / P05-ONLY-PATHS](../61a-fa23-mt2/p05-only-paths.md)
- [61a-fa23-mt2 / P06-AFTER-PARTY](../61a-fa23-mt2/p06-after-party.md)
