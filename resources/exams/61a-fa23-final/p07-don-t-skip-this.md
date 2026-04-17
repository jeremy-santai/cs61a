---
course: CS61A
term: Fall 2023
assessment: Final
exam_slug: 61a-fa23-final
problem_number: 7
problem_title: "Don’t Skip This"
topics: ["higher-order-functions", "lists", "scheme"]
---

# Problem 7 — Don’t Skip This

## Full Extracted Content
## Page 19

7. (8.0 points)
Don’t Skip This
Definition. A skip-partition of a positive integer n is a list of positive integers in increasing order that sums to
n and does not contain any duplicates or consecutive numbers.
Implement part, which takes positive integers n and m. It returns a list of all skip-partitions of n that contain
elements greater than or equal to m. The provided cons-me procedure is used in the implementation.
(define (cons-me first) (lambda (rest) (cons first rest)))
;;; Return a list of all skip-partitions of n with elements greater than or equal to m.
;;;
;;; scm> (part 12 2)
;;; ((2 4 6) (2 10) (3 9) (4 8) (5 7) (12))
(define (part n m)
(cond ((= m n) _______)
(a)
((> m n) nil)
(else (append
(_______ (cons-me m) _______)
(b)
(c)
(part n (+ m 1))))))
(a) (2.0 pt) Fill in blank (a).
(list (list m))
(b) (1.0 pt) Fill in blank (b).
# cons
# list
# append
map
(c) (2.0 pt) Fill in blank (c).
(part (- n m) (+ m 2))
(d) (3.0 pt) Which expressions are passed to scheme_eval when evaluating (if (> 1 2) (+ 1 2) 2)?
Check all that apply.
2 if
■(> 1 2)
■>
■1
■2
2 (+ 1 2)
2 +


---

## Same Semester

- [61a-fa23-final / P01-COPYING-COPIES](p01-copying-copies.md)
- [61a-fa23-final / P02-PATH-MATH](p02-path-math.md)
- [61a-fa23-final / P03-TALK-LIKE-A-PIRATE-DAY](p03-talk-like-a-pirate-day.md)
- [61a-fa23-final / P04-SIX-PAGES-OF-PAIRINGS-SO-PLEASE-READ-THE-DEFINITION-CAREFULLY](p04-six-pages-of-pairings-so-please-read-the-definition-carefully.md)
- [61a-fa23-final / P05-WHAT-WOULD-SCHEME-DO](p05-what-would-scheme-do.md)
- [61a-fa23-final / P06-HOW-TO-GET-PROMOTED](p06-how-to-get-promoted.md)
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
