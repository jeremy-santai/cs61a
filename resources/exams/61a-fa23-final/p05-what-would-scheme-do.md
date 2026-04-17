---
course: CS61A
term: Fall 2023
assessment: Final
exam_slug: 61a-fa23-final
problem_number: 5
problem_title: "What Would Scheme Do?"
topics: ["higher-order-functions", "lists", "scheme"]
---

# Problem 5 — What Would Scheme Do?

## Full Extracted Content
## Page 15

5. (6.0 points)
What Would Scheme Do?
Assume the following code has been evaluated.
(define (shrink k t)
(lambda (s)
(if (null? s) t
( (if
(= (car s) k)
(shrink (+ k 1) t)
(shrink k (cons (car s) t)))
(cdr s)) )))
(define-macro (wait expr) `(lambda () ,expr))
(define (double wait-list)
(if (null? wait-list) nil
(cons (* 2 (car wait-list)) (wait (double ((cdr wait-list)))))))
(define twos (cons 2 (wait (double twos))))
(a) (2.0 pt) What does this expression evaluate to? ((shrink 3 nil) '(3 1 4 1 5 9 2 6))
(2 9 1 1)
(b) (1.0 pt) What is the order of growth of the run time of ((shrink 1 nil) s) in terms of the length of
list s?
# constant
linear
# quadratic
# exponential
(c) (1.0 pt) Which of the following evaluates to 4?
# (cdr twos)
# ((cdr twos))
# (car (cdr twos))
# ((car (cdr twos)))
(car ((cdr twos)))
# ((car ((cdr twos))))

## Page 16

(d) (2.0 pt) Which of the following evaluates to 8?
# (cdr (cdr twos))
# ((cdr (cdr twos)))
# (cdr ((cdr twos)))
# (car (cdr (cdr twos)))
# ((car (cdr (cdr twos))))
# (car (cdr ((cdr twos))))
# (car ((cdr (cdr twos))))
(car ((cdr ((cdr twos)))))


---

## Same Semester

- [61a-fa23-final / P01-COPYING-COPIES](p01-copying-copies.md)
- [61a-fa23-final / P02-PATH-MATH](p02-path-math.md)
- [61a-fa23-final / P03-TALK-LIKE-A-PIRATE-DAY](p03-talk-like-a-pirate-day.md)
- [61a-fa23-final / P04-SIX-PAGES-OF-PAIRINGS-SO-PLEASE-READ-THE-DEFINITION-CAREFULLY](p04-six-pages-of-pairings-so-please-read-the-definition-carefully.md)
- [61a-fa23-final / P06-HOW-TO-GET-PROMOTED](p06-how-to-get-promoted.md)
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
