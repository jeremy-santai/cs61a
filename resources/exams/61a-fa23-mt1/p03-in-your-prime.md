---
course: CS61A
term: Fall 2023
assessment: MT1
exam_slug: 61a-fa23-mt1
problem_number: 3
problem_title: "In Your Prime"
topics: ["higher-order-functions"]
---

# Problem 3 — In Your Prime

## Full Extracted Content
## Page 8

3. (11.0 points)
In Your Prime
Definition: The prime gap of a prime number p is the difference q-p between p and the next larger prime q.
Assume a function is_prime is implemented that takes a positive integer and returns True if it is prime and
False otherwise. You may call is_prime in your implementations below.
def is_prime(n):
"""Return whether positive integer n is a prime number."""
(a) (6.0 points)
Implement smallest_gap, which takes a positive integer k. It returns the smallest prime number that has
a prime gap greater than or equal to k.
def smallest_gap(k):
"""Return the smallest prime number with prime gap greater than or equal to k.
>>> smallest_gap(2) # 5 - 3 = 2
>>> smallest_gap(6) # 29 - 23 = 6
>>> smallest_gap(9) # 127 - 113 = 14, and no prime below 113 has a gap above 8
"""
p, q = 2, 3
# The two smallest prime numbers
while _______:
(a)
p, q = _______
(b)
while _______:
(c)
q = q + 1
return p
i. (2.0 pt) Fill in blank (a).
# q - p == k
# q - p != k
# q - p >= k
# q - p <= k
# q - p > k
q - p < k
The while condition expresses when to keep looking.
ii. (2.0 pt) Fill in blank (b).
q, q + 1
This sets p to be the next prime q, and then initializes q to be the next number so that we can search
for the next prime in the following while loop.

## Page 9

iii. (2.0 pt) Fill in blank (c). You may not use and or or.
not is_prime(q)
Keep incrementing q until it is prime.

## Page 10

(b) (5.0 points)
Implement plus_one, a function that takes two different positive integers a and b. If the larger one is
prime, it returns one more than the smaller one. Otherwise, it returns one more than the average of a and
b.
def plus_one(a, b):
"""Return one more than either the smaller (if larger is prime) or average of a and b.
>>> plus_one(5, 7) # 7 is prime, so return 1 more than 5
>>> plus_one(15, 7) # 15 is not prime, so return 1 more than the average of 15 and 7
12.0
"""
assert a > 0 and b > 0 and a != b
if _______:
(d)
f = _______
(e)
else:
f = _______
(f)
return f(a, b) + 1
i. (2.0 pt) Fill in blank (d).
is_prime(max(a, b))
ii. (1.0 pt) Fill in blank (e).
# max
min
# max()
# min()
# max(a, b)
# min(a, b)
Since the return statement calls the function f, one should assign a function to f. It should be min in
this case according to the spec as the return statement adds 1 to the min of a,b if f is min.
iii. (2.0 pt) Fill in blank (f).
lambda a, b: (a+b)/2
Since there is no built-in averaging function, one must be defined.


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
- [61a-fa23-mt1 / P04-CHOOSE-WISELY](p04-choose-wisely.md)
- [61a-fa23-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa23-mt2/p01-what-would-python-display.md)
- [61a-fa23-mt2 / P02-MAKING-A-LIST-CHECKING-IT-TWICE](../61a-fa23-mt2/p02-making-a-list-checking-it-twice.md)
- [61a-fa23-mt2 / P03-24-HOUR-LIBRARY](../61a-fa23-mt2/p03-24-hour-library.md)
- [61a-fa23-mt2 / P04-A-PERFECT-QUESTION](../61a-fa23-mt2/p04-a-perfect-question.md)
- [61a-fa23-mt2 / P05-ONLY-PATHS](../61a-fa23-mt2/p05-only-paths.md)
- [61a-fa23-mt2 / P06-AFTER-PARTY](../61a-fa23-mt2/p06-after-party.md)
