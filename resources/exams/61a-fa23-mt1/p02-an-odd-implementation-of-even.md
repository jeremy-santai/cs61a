---
course: CS61A
term: Fall 2023
assessment: MT1
exam_slug: 61a-fa23-mt1
problem_number: 2
problem_title: "An Odd Implementation of Even"
topics: ["environment-diagrams", "higher-order-functions"]
---

# Problem 2 — An Odd Implementation of Even

## Full Extracted Content
## Page 5

2. (8.0 points)
An Odd Implementation of Even
Complete the environment diagram below and then answer the questions that follow. There is one question for
each labeled blank in the diagram. The blanks with no labels have no questions associated with them and are
not scored. Some blanks may be empty or unused. If a blank contains an arrow to a function, write
the function as it would appear in the diagram. Do not add frames for calls to built-in functions.
(a) (1.0 pt) Fill in blank (a).
func lambda(m) <line 11> [parent=Global]
# func lambda(m) <line 11> [parent=f1]
# func lambda(m, n) <line 11> [parent=Global]
# func lambda(m, n) <line 11> [parent=f1]
lambda m: m + n is not defined within another function definition. It is evaluated in the global frame.

## Page 6

(b) (1.0 pt) Fill in blank (b).
# func check(f) [parent=Global]
# func check(f) [parent=f1]
# func check(h) [parent=Global]
func check(h) [parent=f1]
The function check is defined in the call to even, and thus its parent frame is the even frame.
(c) (1.0 pt) Fill in blank (c).
# None
# A function named check
# True
False
# Blank: an error occurs before a value is returned.
The name even is still bound to False because the assignment statement in line 6 makes a change in the
check frame (f2), not the even frame (f1).
(d) (1.0 pt) Fill in blank (d).
# f is bound to a lambda function.
h is bound to a lambda function.
# f is bound to a number.
# h is bound to a number.
(e) (1.0 pt) Fill in blank (e).
# n is bound to a number.
# m is bound to a number.
# check is bound to True
# check is bound to False
even is bound to True
# even is bound to False
# Blank: there is no name-value binding here.
Assignment always changes the current frame, and so line 6 adds a binding from even to True here.

## Page 7

(f) (1.0 pt) Fill in blank (f).
# 2
# 4
# 8
# Blank: an error occurs before a value is returned.
The lambda frame’s parent is the lambda function’s parent, which is the global frame. Therefore, n
evaluates to 2.
(g) (2.0 pt) What problems are there in the even function’s implementation? Select all that apply.
2 It does not call f on n for its original arguments f and n.
2 It does not correctly test whether f(n) is an even number.
2 It always stops without returning due to an error.
■It always returns False regardless of the value of f(n).
2 None of the above, but there is some other error in the implementation.
2 None of the above because there is no error in the implementation.
Since even in the even frame is never reassigned, the even function will always return False.


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
- [61a-fa23-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa23-mt1 / P03-IN-YOUR-PRIME](p03-in-your-prime.md)
- [61a-fa23-mt1 / P04-CHOOSE-WISELY](p04-choose-wisely.md)
- [61a-fa23-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa23-mt2/p01-what-would-python-display.md)
- [61a-fa23-mt2 / P02-MAKING-A-LIST-CHECKING-IT-TWICE](../61a-fa23-mt2/p02-making-a-list-checking-it-twice.md)
- [61a-fa23-mt2 / P03-24-HOUR-LIBRARY](../61a-fa23-mt2/p03-24-hour-library.md)
- [61a-fa23-mt2 / P04-A-PERFECT-QUESTION](../61a-fa23-mt2/p04-a-perfect-question.md)
- [61a-fa23-mt2 / P05-ONLY-PATHS](../61a-fa23-mt2/p05-only-paths.md)
- [61a-fa23-mt2 / P06-AFTER-PARTY](../61a-fa23-mt2/p06-after-party.md)
