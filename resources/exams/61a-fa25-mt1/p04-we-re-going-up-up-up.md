---
course: CS61A
term: Fall 2025
assessment: MT1
source_pdf: 61a-fa25-mt1_sol.pdf
exam_slug: 61a-fa25-mt1
problem_number: 4
problem_title: "We’re Going Up, Up, Up"
page_range: [8, 14]
points: "16.0 points"
topics: ["cs61a"]
concepts: ["cs61a"]
question_types: ["implementation"]
difficulty: "hard"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 4 — We’re Going Up, Up, Up

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** cs61a
- **Concepts:** cs61a
- **Question types:** implementation
- **Difficulty:** hard
- **Source pages:** 8-14

## Source

- Course: CS61A
- Term: Fall 2025
- Assessment: MT1
- Source PDF: `61a-fa25-mt1_sol.pdf`

## Full extracted content

## Page 8

4. (16.0 points)
We’re Going Up, Up, Up
Definitions. An up-sequence is a sequence of positive integers in which each term is larger than the last. The
next function f for an up-sequence takes a non-negative integer t and encodes the sequence as follows: If t is
any term of the sequence except the last one, then f(t) returns the next term in the sequence after t. If t is
the last term of the sequence or not a term in the sequence, f(t) returns 0. Finally, when t is 0, then f(0)
returns the first term of the sequence. For example, fifty_evens below is a next function for the sequence 2, 4,
6, 8, . . . , 98, 100.
def fifty_evens(t):
"The next function for the finite sequence of the first 50 positive even numbers."
if t % 2 == 0 and t < 100:
return t + 2
return 0
(a) (6.0 points)
Implement sum_sequence, which takes a next function f for a finite up-sequence. It returns the sum of
the terms of that sequence.
def sum_sequence(f):
"""Return the sum of terms in a finite sequence.
>>> sum_sequence(fifty_evens)
# 2 + 4 + 6 + 8 + ... + 98 + 100 = 2550
"""
t = _______
(a)
total = 0
while t:
t, total = _______ , _______
(b)
(c)
return total
i. (2.0 pt) Fill in blank (a).
f(0)
ii. (2.0 pt) Fill in blank (b).
f(t)
iii. (2.0 pt) Fill in blank (c).
# total + 1
total + t
# total + f
# total + fifty_evens
# total + f(t)
# total + fifty_evens(t)

## Page 9

(b) (6.0 points)
Here is the next function for the infinite up-sequence of positive perfect squares: 1, 4, 9, 16, 25, . . .
def next_square(t):
"""Compute the next perfect square.
>>> next_square(0)
>>> next_square(16)
>>> next_square(17)
# Not a perfect square
"""
sqrt_t = t ** 0.5
# The square root of t
if sqrt_t == round(sqrt_t):
# Make sure t was a perfect square
return (round(sqrt_t) + 1) ** 2
# Return the next perfect square
return 0
Implement cap, which takes a next function f for an infinite up-sequence and a positive integer n. It
returns a next function for the finite up-sequence containing the terms of f that are less than or equal to n.
If n is a term of the up-sequence for f, then it is included in the result’s sequence.
def cap(f, n):
"""Return the next function for the up-sequence for f up to (and possibly including) n.
>>> squares_up_to_25 = cap(next_square, 30)
# 30 is not in the next_square sequence
>>> squares_up_to_25(4)
>>> squares_up_to_25(16)
>>> squares_up_to_25(25)
>>> squares_up_to_25(17)
# 17 is not in the next_square sequence
>>> cap(next_square, 81)(64)
# 81 is in the next_square sequence
"""
def capped(t):
if _______:
(d)
_______
(e)
else:
return _______
(f)
return capped

## Page 10

i. (2.0 pt) Fill in blank (d).
f(t) > n
ii. (2.0 pt) Fill in blank (e).
# t = 0
# n += 1
# n -= 1
# t += 1
# t -= 1
# t = f(t)
# t = next_square(t)
# return n
# return t
return 0
iii. (2.0 pt) Fill in blank (f).
# n
# t
# f
f(t)
# next_square
# next_square(t)

## Page 11

(c) (4.0 points)
Definition. The previous function g for an up-sequence takes a non-negative integer t. If t is any other
term than the first, g(t) is the previous term. If t is the first term or not a term at all, g(t) returns 0.
g(0) is the last term.
Implement reverse, which takes a next function f for a finite up-sequence. It returns the previous function
for that same sequence. You may call max_term, which is described below, but you don’t need to implement
max_term.
def max_term(f):
"""Returns the largest term in the finite up-sequence for next function f.
>>> max_term(cap(next_square, 20))
# 16 is the largest square less than or equal to 20.
"""
# Implementation omitted, but you can assume that the function is implemented correctly.
def reverse(f):
"""Return the previous function for the up-sequence encoded by next function f.
>>> rev_squares = reverse(cap(next_square, 30))
# Goes in reverse through 1, 4, 9, 16, 25
>>> print(rev_squares(0), rev_squares(25), rev_squares(16), rev_squares(9), rev_squares(4))
25 16 9 4 1
>>> rev_squares(1)
# 1 is the first term
>>> rev_squares(10)
# 10 is not in the sequence
"""
def previous(t):
if t == 0:
return _______
(g)
x = t - 1
while x > 0 and _______:
(h)
x = x - 1
return x
return previous
i. (2.0 pt) Fill in blank (g).
max_term(f)

## Page 12

ii. (2.0 pt) Fill in blank (h).
f(x) != t

## Page 13

(d) (0.0 points)
This A+ question is not worth any points. It can only affect your course grade if you have a
high A and might receive an A+. Finish the rest of the exam first!
Implement sum_below, which takes a next function f for an infinite up-sequence and a positive integer n
that is a term of the sequence. It returns the sum of the terms of the sequence for f that are less than (but
not including) n.
You may not use cap or max_term or reverse.
You may not use if or else or [ or ].
def sum_below(f, n):
"""Return the sum of the terms of the sequence for f that are below n,
where n is a term in the sequence for f.
>>> sum_below(next_square, 25)
# 1 + 4 + 9 + 16
"""
assert f(n), 'n is not a term of the up-sequence for f'
return sum_sequence(_______)
(i)
i. (0.0 pt) Fill in blank (i).
lambda u: f(u) - n and f(u)
lambda u: (f(u) < n and f(u)) or 0
lambda t: int(f(t) < n)*f(t)

## Page 14

No more questions.


---

## Same Semester

- [61a-fa25-final / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa25-final/p01-what-would-python-display.md)
- [61a-fa25-final / P02-DO-YOU-COPY](../61a-fa25-final/p02-do-you-copy.md)
- [61a-fa25-final / P03-MATH-PLACEMENT-EXAM](../61a-fa25-final/p03-math-placement-exam.md)
- [61a-fa25-final / P04-TRIM-THE-TREE](../61a-fa25-final/p04-trim-the-tree.md)
- [61a-fa25-final / P05-DOWNLOADS](../61a-fa25-final/p05-downloads.md)
- [61a-fa25-final / P06-SCHEME-VS-PYTHON](../61a-fa25-final/p06-scheme-vs-python.md)
- [61a-fa25-final / P07-STUDENTS](../61a-fa25-final/p07-students.md)
- [61a-fa25-final / P08-STUDENTS-IN-SQL](../61a-fa25-final/p08-students-in-sql.md)
- [61a-fa25-final / P09-FINAL-BOSS](../61a-fa25-final/p09-final-boss.md)
- [61a-fa25-mt1 / P01-WHAT-WOULD-PYTHON-DO-OT](p01-what-would-python-do-ot.md)
- [61a-fa25-mt1 / P02-SILKSONG](p02-silksong.md)
- [61a-fa25-mt1 / P03-SAJA-BOYS](p03-saja-boys.md)
