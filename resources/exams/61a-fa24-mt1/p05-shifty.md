---
course: CS61A
term: Fall 2024
assessment: MT1
source_pdf: 61a-fa24-mt1_sol.pdf
exam_slug: 61a-fa24-mt1
problem_number: 5
problem_title: "Shifty"
page_range: [9, 13]
points: "10.0 points"
topics: ["cs61a"]
concepts: ["cs61a"]
question_types: ["implementation"]
difficulty: "medium"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 5 — Shifty

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** cs61a
- **Concepts:** cs61a
- **Question types:** implementation
- **Difficulty:** medium
- **Source pages:** 9-13

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: MT1
- Source PDF: `61a-fa24-mt1_sol.pdf`

## Full extracted content

## Page 9

5. (10.0 points)
Shifty
(a) (4.0 points)
Implement shift, which takes a number k and a one-argument function f. It returns a one-argument
function g that takes a number x. For all numbers x, g(x) is equal to f(x + k).
def shift(k, f):
"""Return a function of x that returns f(x+k).
>>> square = lambda x: x * x
>>> g = shift(2, square)
>>> g(3)
# square(3 + 2)
"""
return _______
(a)
i. (2.0 pt) Fill in blank (a).
# f(x) + k
# f(x + k)
# f(lambda x: x + k)
# f(lambda x: x) + k
# lambda x: f(x) + k
lambda x: f(x + k)
# (lambda x: f(x))(x + k)
# g(x) + k
# g(x + k)
# g(lambda x: x + k)
# g(lambda x: x) + k
# lambda x: g(x) + k
# lambda x: g(x + k)
# (lambda x: g(x))(x + k)
ii. (2.0 pt) Provide an alternate solution for blank (a) . This time, your solution must call compose
(defined below), and f may not be the operator of a call expression. In other words, you can’t write
f( in your answer. You may not write [ or if.
def compose(f, g):
"""Return a function that takes x and calls f on g of x."""
return lambda x: f(g(x))
compose(f, lambda x: x + k)

## Page 10

(b) (6.0 points)
Implement sum_range, which takes positive integers p and q with p <= q, as well as a one-argument
function term. It returns the sum of the return values of term called on each consecutive integer starting
with p and ending with q (including both p and q). You may call shift, summation, and compose. Assume
shift is implemented correctly.
def summation(n, term):
"""Sum the first n terms of a sequence: term(1) + term(2) + ... + term(n).
>>> summation(5, lambda x: x*x)
# 1*1 + 2*2 + 3*3 + 4*4 + 5*5
"""
total, k = 0, 1
while k <= n:
total, k = total + term(k), k + 1
return total
def sum_range(p, q, term):
"""Sum terms p through q of a sequence: term(p) + term(p+1) + ... + term(q).
>>> sum_range(1, 5, lambda x: x*x)
# 1*1 + 2*2 + 3*3 + 4*4 + 5*5
>>> sum_range(4, 5, lambda x: x*x)
# 4*4 + 5*5
>>> sum_range(5, 5, lambda x: x*x)
# 5*5
"""
assert p <= q
return _______ ( _______ , _______ )
(a)
(b)
(c)
i. (1.0 pt) Fill in blank (a).
summation
# shift
# compose
# term
ii. (2.0 pt) Fill in blank (b).
# p - q - 1
# p - q
# p - q + 1
# q - p - 1
# q - p
q - p + 1

## Page 11

iii. (3.0 pt) Fill in blank (c).
shift(p - 1, term)

## Page 12

(c) (0.0 points)
This A+ question is not worth any points. It can only affect your course grade if you have a
high A and might receive an A+. Finish the rest of the exam first!
The shifter function below is a curried version of shift.
Implement unshift, which takes the result of shifter(k) for some number k. It returns a function that
takes the result of shifter(k)(f) for some function f and returns a function equivalent to f. That is:
f(x) == unshift(shifter(k))(shifter(k)(f))(x)
You can write your answer on multiple lines if it’s long. You can abbreviate lambda using the greek symbol
lambda.
Your answer must be a call to shift. You may also call any of compose, summation, or sum_range.
Hint: If you can compute k, then you can shift backward by k to undo the original shift.
def shifter(k):
def shifted(f):
return shift(k, f)
return shifted
def unshift(shifted):
"""Assume shifted is the return value of shifter(k) for some k.
>>> cubic = lambda x: x*x*x - 5*x*x + 1
# Some complicated function
>>> cubic(2.0)
-11.0
>>> cubic(9.0)
325.0
>>> do = shifter(4)
>>> do(cubic)(2.0)
# same as cubic(6.0)
37.0
>>> do(cubic)(9.0)
# same as cubic(13.0)
1353.0
>>> undo = unshift(do)
>>> undo(do(cubic))(2.0)
# same as cubic(2.0)
-11.0
>>> undo(do(cubic))(9.0)
# same as cubic(9.0)
325.0
"""
return lambda g: _______
i. (0.0 pt) Fill in the blank with a single call to shift.
shift(-shifted(lambda x: x)(0), g)
-OR-
shifter(-shifted(lambda x:
x)(0))(g)

## Page 13

No more questions.


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
- [61a-fa24-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa24-mt1 / P02-WHICH-ONE](p02-which-one.md)
- [61a-fa24-mt1 / P03-FINAL-DIGIT](p03-final-digit.md)
- [61a-fa24-mt1 / P04-CLOSE-ENOUGH](p04-close-enough.md)
- [61a-fa24-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa24-mt2/p01-what-would-python-display.md)
- [61a-fa24-mt2 / P02-PIZZA-BY-THE-SLICE](../61a-fa24-mt2/p02-pizza-by-the-slice.md)
- [61a-fa24-mt2 / P03-CS-61A-SOFTWARE-STORE](../61a-fa24-mt2/p03-cs-61a-software-store.md)
- [61a-fa24-mt2 / P04-ALMOST-A-PERFECT-QUESTION](../61a-fa24-mt2/p04-almost-a-perfect-question.md)
- [61a-fa24-mt2 / P05-HOW-LONG-IS-THIS-EXAM](../61a-fa24-mt2/p05-how-long-is-this-exam.md)
- [61a-fa24-mt2 / P06-NICE-PATH](../61a-fa24-mt2/p06-nice-path.md)
