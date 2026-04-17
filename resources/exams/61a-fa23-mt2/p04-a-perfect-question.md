---
course: CS61A
term: Fall 2023
assessment: MT2
exam_slug: 61a-fa23-mt2
problem_number: 4
problem_title: "A Perfect Question"
topics: ["generators", "lists"]
---

# Problem 4 — A Perfect Question

## Full Extracted Content
## Page 9

4. (16.0 points)
A Perfect Question
Definition. A perfect square is k*k for some integer k.
(a) (7.0 points)
Implement fit, which takes positive integers total and n. It returns True or False indicating whether
there are n positive perfect squares that sum to total. The perfect squares need not be unique.
def fit(total, n):
"""Return whether there are n positive perfect squares that sums to total.
>>> [fit(4, 1), fit(4, 2), fit(4, 3), fit(4, 4)]
# 1*(2*2) for n=1; 4*(1*1) for n=4
[True, False, False, True]
>>> [fit(12, n) for n in range(3, 8)]
# 3*(2*2), 3*(1*1)+3*3, 4*(1*1)+2*(2*2)
[True, True, False, True, False]
>>> [fit(32, 2), fit(32, 3), fit(32, 4), fit(32, 5)] # 2*(4*4), 3*(1*1)+2*2+5*5
[True, False, False, True]
"""
def f(total, n, k):
if _______:
(a)
return True
elif _______:
(b)
return False
else:
return _______
(c)
return f(total, n, 1)
i. (2.0 pt) Select all of the options that could fill blank (a).
2 total == 0
2 n == k
■total == 0 and n == 0
2 total == k * k
■total == k * k and n == 1
■total == n * k * k
The final condition is ideal, but the other two would still provide the correct answer after additional
recursive calls.
ii. (2.0 pt) Fill in blank (b).
total < k * k
At this point, one can only use terms that are larger than k*k and thus there can’t be a solution if
total is smaller than that.

## Page 10

iii. (3.0 pt) Fill in blank (c) with an expression of the form f(___, ___, ___) ___ f(___, ___, ___).
f(total - k * k, n - 1, k) or f(total, n, k + 1)
You either use k*k at least once or you only use larger perfect squares.

## Page 11

(b) (9.0 points)
Implement the generator function squares, which takes positive integers total and k. It yields all lists
of perfect squares greater or equal to k*k that sum to total. Each list is in non-increasing order (large to
small).
def squares(total, k):
"""Yield the ways in which perfect squares greater or equal to k*k sum to total.
>>> list(squares(10, 1))
# All lists of perfect squares that sum to 10
[[1, 1, 1, 1, 1, 1, 1, 1, 1, 1], [4, 1, 1, 1, 1, 1, 1], [4, 4, 1, 1], [9, 1]]
>>> list(squares(20, 2))
# Only use perfect squares greater or equal to 4 (2*2).
[[4, 4, 4, 4, 4], [16, 4]]
"""
assert total > 0 and k > 0
if total == k * k:
yield _______
(d)
elif total > k * k:
for s in _______:
(e)
yield _______
(f)
yield from squares(total, k + 1)
i. (2.0 pt) Fill in blank (d).
[k * k]
ii. (3.0 pt) Fill in blank (e).
squares(total - k * k, k)
This gives a generator that yields solutions whose total area is total - k*k.
And adding one
more square of k*k gives a solution for total.
iii. (1.0 pt) Select all of the options that could fill in blank (f).
2 s + k*k
2 s.append(k*k)
■s + [k*k]
2 [s] + [k*k]
Each s is a list whose elements add to total - k*k, and adding k*k gives a desired solution.

## Page 12

iv. (3.0 pt) Write an expression containing a that evaluates to the shortest list of perfect squares that
sum to an integer a. For example, if a = 32, your expression should evaluate to [16, 16] (not [25,
4, 1, 1, 1]). If there are two or more such lists that are both shortest, it can evaluate to any of
them. Assume squares is implemented correctly.
min(squares(a, 1), key=len)


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
- [61a-fa23-mt2 / P05-ONLY-PATHS](p05-only-paths.md)
- [61a-fa23-mt2 / P06-AFTER-PARTY](p06-after-party.md)
