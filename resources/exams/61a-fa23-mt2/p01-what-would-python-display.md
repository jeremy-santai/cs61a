---
course: CS61A
term: Fall 2023
assessment: MT2
exam_slug: 61a-fa23-mt2
problem_number: 1
problem_title: "What Would Python Display?"
topics: ["higher-order-functions", "generators"]
---

# Problem 1 — What Would Python Display?

## Full Extracted Content
## Page 3

1. (4.0 points)
What Would Python Display?
Assume the following code has been executed.
s = range(3, 7)
t = iter(s)
u = map(lambda x: 2 * x, t)
v = [next(t), next(t)]
# This line does not cause an error
Choose the output displayed by the interactive Python interpreter when each expression below is evaluated
or Error if an error occurs. These expressions are evaluated in order and the value of later expressions may be
affected by evaluating previous expressions.
(a) (1.0 pt) [-k for k in v if k in s]
# []
# [3, 4]
[-3, -4]
# Error
v contains 3 and 4 (the first two elements of the range 3 through 7), and both are in the range.
(b) (1.0 pt) tuple(u)
# (3, 4, 5, 6)
# (3, 4, 5, 6, 7)
# (6, 8, 10, 12)
# (6, 8, 10, 12, 14)
(10, 12)
# (10, 12, 14)
# Error
The map object does not apply its function until tuple is called. Making v already iterated over 3 and 4.
Thus, the map will begin at 5. The iterator t stops after 6.
(c) (1.0 pt) next(t)
# 3
# 5
# range(3, 7)
# range(5, 7)
Error
The tuple call used up the values in t. StopIteration occurs.

## Page 4

(d) (1.0 pt) next(iter(s)) + next(iter(s))
# 7
# 10
# 11
# Error
One makes a new iterator out of the iterable, range(3,7) in each call, and thus each call to next yields a 3.


---

## Same Semester

- [61a-fa23-final / P01-COPYING-COPIES](../61a-fa23-final/p01-copying-copies.md)
- [61a-fa23-final / P02-PATH-MATH](../61a-fa23-final/p02-path-math.md)
- [61a-fa23-final / P03-TALK-LIKE-A-PIRATE-DAY](../61a-fa23-final/p03-talk-like-a-pirate-day.md)
- [61a-fa23-final / P04-SIX-PAGES-OF-PAIRINGS-SO-PLEASE-READ-THE-DEFINITION-CAREFULLY](../61a-fa23-final/p04-six-pages-of-pairings-so-please-read-the-definition-carefully.md)
- [61a-fa23-final / P05-WHAT-WOULD-SCHEME-DO](../61a-fa23-final/p05-what-would-scheme-do.md)
- [61a-fa23-final / P06-HOW-TO-GET-PROMOTED](../61a-fa23-final/p06-how-to-get-promoted.md)
- [61a-fa23-final / P07-DON-T-SKIP-THIS](../61a-fa23-final/p07-don-t-skip-this.md)
- [61a-fa23-final / P08-CHEAP-DONUTS](../61a-fa23-final/p08-cheap-donuts.md)
- [61a-fa23-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa23-mt1/p01-what-would-python-display.md)
- [61a-fa23-mt1 / P02-AN-ODD-IMPLEMENTATION-OF-EVEN](../61a-fa23-mt1/p02-an-odd-implementation-of-even.md)
- [61a-fa23-mt1 / P03-IN-YOUR-PRIME](../61a-fa23-mt1/p03-in-your-prime.md)
- [61a-fa23-mt1 / P04-CHOOSE-WISELY](../61a-fa23-mt1/p04-choose-wisely.md)
- [61a-fa23-mt2 / P02-MAKING-A-LIST-CHECKING-IT-TWICE](p02-making-a-list-checking-it-twice.md)
- [61a-fa23-mt2 / P03-24-HOUR-LIBRARY](p03-24-hour-library.md)
- [61a-fa23-mt2 / P04-A-PERFECT-QUESTION](p04-a-perfect-question.md)
- [61a-fa23-mt2 / P05-ONLY-PATHS](p05-only-paths.md)
- [61a-fa23-mt2 / P06-AFTER-PARTY](p06-after-party.md)
