---
course: CS61A
term: Fall 2024
assessment: MT2
source_pdf: 61a-fa24-mt2_sol.pdf
exam_slug: 61a-fa24-mt2
problem_number: 4
problem_title: "Almost a Perfect Question"
page_range: [7, 10]
points: "18.0 points"
topics: ["generators", "lists"]
concepts: ["generators", "lists"]
question_types: ["implementation", "predicate", "generator"]
difficulty: "hard"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 4 — Almost a Perfect Question

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** generators, lists
- **Concepts:** generators, lists
- **Question types:** implementation, predicate, generator
- **Difficulty:** hard
- **Source pages:** 7-10

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: MT2
- Source PDF: `61a-fa24-mt2_sol.pdf`

## Full extracted content

## Page 7

4. (18.0 points)
Almost a Perfect Question
Definition. A proper divisor of an integer n is an integer d less than n that evenly divides n, and so n divided
by d has no remainder. A semiperfect number is a positive integer that is the sum of some (or all) of its proper
divisors. For example, 24 = 2 + 4 + 6 + 12 and so it is semiperfect. The sum of divisors cannot contain
repeated numbers.
(a) (6.0 points)
Implement semiperfect, which takes a positive integer n. It returns True if n is semiperfect and False
otherwise.
def semiperfect(n):
"""Return whether positive integer n is a sum of some (or all) of its proper divisors.
>>> [k for k in range(1, 40) if semiperfect(k)]
[6, 12, 18, 20, 24, 28, 30, 36]
"""
def f(s, d):
if _______:
(a)
return True
if d >= n:
return False
if _______ and f(_______, d + 1):
(b)
(c)
return True
return _______
(d)
return f(n, 1)
i. (1.0 pt) Fill in blank (a).
# n == 0
s == 0
# s == d
# n == d
ii. (1.0 pt) Fill in blank (b).
n % d == 0
# s % d == 0
# n % d > 0
# s % d > 0
iii. (2.0 pt) Fill in blank (c).
s - d
iv. (2.0 pt) Fill in blank (d).
f(s, d + 1)

## Page 8

(b) (6.0 points)
Implement subsums, a generator function that takes a list of unique (no repeats) positive integers s and
a positive integer n. It yields all sublists of s that sum to n. A sublist of s is a list containing some of the
elements of s in order. The subsums function should not yield the same list twice. The lists may appear
in any order.
def subsums(s, n):
"""Yield all sublists of s that sum to n.
>>> list(subsums([1, 2, 3, 6, 9], 18))
[[1, 2, 6, 9], [3, 6, 9]]
>>> list(subsums([1, 2, 3, 4, 6], 16))
[[1, 2, 3, 4, 6]]
>>> list(subsums([1, 2, 3, 4, 6, 8, 12], 12))
[[1, 2, 3, 6], [1, 3, 8], [2, 4, 6], [4, 8], [12]]
"""
if s:
if _______:
(e)
yield [n]
for t in _______:
(f)
yield _______
(g)
yield from _______
(h)
i. (1.0 pt) Fill in blank (e).
# n == s
n == s[0]
# n in s
# [n] == s
ii. (3.0 pt) Fill in blank (f).
subsums(s[1:], n-s[0])
iii. (1.0 pt) Fill in blank (g).
# s + t
# [s] + t
# s[1:] + t
s[:1] + t

## Page 9

iv. (1.0 pt) Fill in blank (h).
# subsums(s, n)
subsums(s[1:], n)
# subsums(s, n - 1)
# subsums(s[1:], n - 1)

## Page 10

(c) (6.0 points)
Implement semisums, which takes a positive integer n. It returns a list of all lists of unique (no repeats)
proper divisors of n that sum to n. You may call semiperfect and subsums.
def semisums(n):
"""Return a list of all lists (with no repeats) of
proper divisors of n that sum to n.
>>> semisums(22)
# 22 is not semiperfect, so there are no sums.
[]
>>> semisums(30)
# 30 is semiperfect. It has three different sums.
[[1, 3, 5, 6, 15], [2, 3, 10, 15], [5, 10, 15]]
"""
return list( _______ ([k for k in range(1, n) if _______ ], _______ ))
(i)
(j)
(k)
i. (1.0 pt) Fill in blank (i).
# map
# filter
# sorted
subsums
# semiperfect
ii. (1.0 pt) Fill in blank (j).
# semiperfect(n)
# semiperfect(k)
# semiperfect(n) or semiperfect(k)
n % k == 0
iii. (1.0 pt) Fill in blank (k).
n
iv. (3.0 pt) Fill in blank (l) of primitive_semiperfect, a function that takes a positive integer n. It
returns True if n is semiperfect and no smaller semiperfect number is a divisor of n. Your answer
should have two expressions separated by a comma.
def primitive_semiperfect(n):
"""Return whether n is semiperfect and has no semiperfect proper divisors.
>>> [k for k in range(1, 300) if primitive_semiperfect(k)]
[6, 20, 28, 88, 104, 272]
"""
return semiperfect(n) and not any(map(semiperfect, filter(_______)))
(l)
lambda k: n % k == 0, range(1, n)


---

## Same Semester

- [61a-fa24-final / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa24-final/p01-what-would-python-display.md)
- [61a-fa24-final / P02-LINE-DIAGRAM](../61a-fa24-final/p02-line-diagram.md)
- [61a-fa24-final / P03-MAKE-TENS](../61a-fa24-final/p03-make-tens.md)
- [61a-fa24-final / P04-COUNT-MISSES](../61a-fa24-final/p04-count-misses.md)
- [61a-fa24-final / P05-PROMOTION-TO-CS-61B](../61a-fa24-final/p05-promotion-to-cs-61b.md)
- [61a-fa24-final / P06-FRESH-PRODUCE](../61a-fa24-final/p06-fresh-produce.md)
- [61a-fa24-final / P07-A-PAIR-OF-SCHEMES](../61a-fa24-final/p07-a-pair-of-schemes.md)
- [61a-fa24-final / P08-ARCANE-JOBS](../61a-fa24-final/p08-arcane-jobs.md)
- [61a-fa24-final / P09-APE-PULL-US](../61a-fa24-final/p09-ape-pull-us.md)
- [61a-fa24-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa24-mt1/p01-what-would-python-display.md)
- [61a-fa24-mt1 / P02-WHICH-ONE](../61a-fa24-mt1/p02-which-one.md)
- [61a-fa24-mt1 / P03-FINAL-DIGIT](../61a-fa24-mt1/p03-final-digit.md)
- [61a-fa24-mt1 / P04-CLOSE-ENOUGH](../61a-fa24-mt1/p04-close-enough.md)
- [61a-fa24-mt1 / P05-SHIFTY](../61a-fa24-mt1/p05-shifty.md)
- [61a-fa24-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa24-mt2 / P02-PIZZA-BY-THE-SLICE](p02-pizza-by-the-slice.md)
- [61a-fa24-mt2 / P03-CS-61A-SOFTWARE-STORE](p03-cs-61a-software-store.md)
- [61a-fa24-mt2 / P05-HOW-LONG-IS-THIS-EXAM](p05-how-long-is-this-exam.md)
- [61a-fa24-mt2 / P06-NICE-PATH](p06-nice-path.md)
