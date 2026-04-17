---
course: CS61A
term: Fall 2023
assessment: MT1
exam_slug: 61a-fa23-mt1
problem_number: 4
problem_title: "Choose Wisely"
topics: ["higher-order-functions"]
---

# Problem 4 — Choose Wisely

## Full Extracted Content
## Page 11

4. (15.0 points)
Choose Wisely
Definition: A digit test is a function that takes a non-negative integer less than 10 and returns True or False.
(a) (9.0 points)
Implement only which takes a non-negative integer n and a digit test t. It returns a non-negative integer
containing only the digits of n for which t returns True when called on each of those digits. The digits
should appear in the same order as they did in n. The number 0 has no digits. You may not use str or
repr or [ or ] or for.
def only(n, t):
"""Return only the digits of n for which t returns True when called on each digit.
>>> only(23344567, lambda d: d % 2 == 0)
>>> only(987654349675, lambda d: d < 7)
>>> only(2023, lambda d: False)
"""
keep = 0
while n:
n, d = n // 10, n % 10
if _______:
(a)
keep = 10 * keep + _______
(b)
_______:
(c)
_______
(d)
return n
i. (2.0 pt) Fill in blank (a).
t(d)
Calls the digit test on the current digit to see if one should include that digit.
ii. (1.0 pt) Fill in blank (b).
d
# d // 10
# n
# n % 10
# keep
# keep % 10
# keep // 10

## Page 12

iii. (2.0 pt) Fill in blank (c)
# if True
# if n
# if keep
# if n > keep
# if keep > n
# while True
# while n
while keep
# while n > keep
# while keep > n
iv. (4.0 pt) Fill in blank (d) with an assignment statement. You are allowed to assign to multiple
names.
n, keep = n * 10 + keep % 10, keep // 10

## Page 13

(b) (6.0 points)
Implement every which takes a digit test t and returns a function digit that takes a positive integer n.
The digit function returns whether t returns True for every digit of n.
def every(t):
"""Return a function of n that returns whether t returns True for every digit of n.
>>> f = every(lambda d: d % 2 == 1)
>>> f(37511)
# every digit is odd
True
>>> f(2023)
# Not every digit is odd
False
"""
def digit(n):
assert n > 0
while n:
if _______:
(e)
_______
(f)
n = n // 10
return _______
(g)
return _______
(h)
i. (3.0 pt) Fill in blank (e).
not t(n % 10)
ii. (1.0 pt) Fill in blank (f).
return False
iii. (1.0 pt) Fill in blank (g).
# every
# digit
True
# False
# n > 0
iv. (1.0 pt) Fill in blank (h).
digit
# digit()
# digit(n)
# lambda n: digit

## Page 14

(c) This A+ question is not worth any points. It can only affect your course grade if you have a
high A and might receive an A+. Finish the rest of the exam first!
Implement even_odd, which takes a positive integer n that has both even and odd digits. It returns True
if all of the odd digits of n are larger than the last (right-most) even digit of n. Otherwise, it returns
False. You may call only and every. You may not use str or repr or [ or ] or for.
def even_odd(n):
"""Return whether all odd digits of n are larger than n's last even digit.
>>> even_odd(8023) # 3 (the only odd digit) is larger than 2 (the last even digit)
True
>>> even_odd(5237679) # 3 (an odd digit) is smaller than 6 (the last even digit)
False
>>> even_odd(7297679) # All odd digits (7 & 9) are larger than 6 (the last even digit)
True
"""
return _______
i. Fill in the blank. You may only write one return expression, but if it’s long you can use multiple lines.
every(lambda d: d % 2 == 0 or d > only(n, lambda d: d % 2 == 0) % 10)(n)
every(lambda d: d > only(n, lambda d: d % 2 == 0) % 10)(only(n, lambda
d: d % 2 == 1))

## Page 15

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
- [61a-fa23-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa23-mt1 / P02-AN-ODD-IMPLEMENTATION-OF-EVEN](p02-an-odd-implementation-of-even.md)
- [61a-fa23-mt1 / P03-IN-YOUR-PRIME](p03-in-your-prime.md)
- [61a-fa23-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa23-mt2/p01-what-would-python-display.md)
- [61a-fa23-mt2 / P02-MAKING-A-LIST-CHECKING-IT-TWICE](../61a-fa23-mt2/p02-making-a-list-checking-it-twice.md)
- [61a-fa23-mt2 / P03-24-HOUR-LIBRARY](../61a-fa23-mt2/p03-24-hour-library.md)
- [61a-fa23-mt2 / P04-A-PERFECT-QUESTION](../61a-fa23-mt2/p04-a-perfect-question.md)
- [61a-fa23-mt2 / P05-ONLY-PATHS](../61a-fa23-mt2/p05-only-paths.md)
- [61a-fa23-mt2 / P06-AFTER-PARTY](../61a-fa23-mt2/p06-after-party.md)
