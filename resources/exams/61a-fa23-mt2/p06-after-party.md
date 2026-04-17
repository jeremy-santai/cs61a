---
course: CS61A
term: Fall 2023
assessment: MT2
exam_slug: 61a-fa23-mt2
problem_number: 6
problem_title: "After Party"
topics: ["higher-order-functions", "lists", "oop"]
---

# Problem 6 — After Party

## Full Extracted Content
## Page 16

6. (6.0 points)
After Party
Implement after, which takes a linked list s and values a and b. It returns whether an element of s equal to b
appears after an element of s equal to a. The Link class appears on the Midterm 2 study guide.
def after(s, a, b):
"""Return whether b comes after a in linked list s.
>>> t = Link(3, Link(6, Link(5, Link(4))))
>>> after(t, 6, 4)
True
>>> after(t, 4, 6)
False
>>> after(t, 6, 6)
False
"""
def find(s, n, f):
if s == Link.empty:
return _______
(a)
elif s.first == n:
return f(s.rest)
else:
return find(s.rest, n, f)
return find(s, a, lambda rest: _______)
(b)
(a) (1.0 pt) Fill in blank (a).
# n
# True
False
# a < b
# f(Link.empty)
You have not found n, which is a, yet, and the list is done.
(b) (4.0 pt) Fill in blank (b). You may not use or, and, if, [, or ].
find(rest, b, lambda rest: True)
At this point, you have found a in the list, so you should see if b is in the rest of the list.

## Page 17

(c) (1.0 pt) What is the order of growth of the run time of an efficient implementation of after in terms of
the length of s? Here, efficient means that you have filled in the blanks to give the function the fastest
order of growth.
# Constant
# Logarithmic
Linear
# Quadratic
# Exponential
Each element is considered once since each recursive function call is called on the rest of the current list,
giving linear time. In the best case, a and b could appear at the beginning of the list, which would be
found in constant time, so that answer was accepted as well.

## Page 18

No more questions.


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
- [61a-fa23-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa23-mt2 / P02-MAKING-A-LIST-CHECKING-IT-TWICE](p02-making-a-list-checking-it-twice.md)
- [61a-fa23-mt2 / P03-24-HOUR-LIBRARY](p03-24-hour-library.md)
- [61a-fa23-mt2 / P04-A-PERFECT-QUESTION](p04-a-perfect-question.md)
- [61a-fa23-mt2 / P05-ONLY-PATHS](p05-only-paths.md)
