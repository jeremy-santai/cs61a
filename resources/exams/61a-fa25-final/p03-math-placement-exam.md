---
course: CS61A
term: Fall 2025
assessment: Final
source_pdf: 61a-fa25-final_sol.pdf
exam_slug: 61a-fa25-final
problem_number: 3
problem_title: "Math Placement Exam"
page_range: [6, 11]
points: "21.0 points"
topics: ["generators", "iterators", "lists", "dictionaries"]
concepts: ["generators", "iterators", "lists"]
question_types: ["implementation", "predicate"]
difficulty: "hard"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 3 — Math Placement Exam

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** generators, iterators, lists, dictionaries
- **Concepts:** generators, iterators, lists
- **Question types:** implementation, predicate
- **Difficulty:** hard
- **Source pages:** 6-11

## Source

- Course: CS61A
- Term: Fall 2025
- Assessment: Final
- Source PDF: `61a-fa25-final_sol.pdf`

## Full extracted content

## Page 6

3. (21.0 points)
Math Placement Exam
Definition. An equation is a list of numbers and operators. A number is either an integer or a ?. An operator
is either +, -, or =. Equations start and end with a number, alternate between numbers and operators, and
contain exactly one =.
(a) (5.0 points)
Implement is_equation, which takes a list s. It returns whether s is an equation.
def is_equation(s):
"""Return whether the list s contains a well-formed equation.
>>> is_equation([7, '+', 2, '=', '?', '+', 6])
True
>>> is_equation([-7, '+', '?', '=', '?', '-', 6])
True
>>> is_equation([-7, '+', 2, '=', '?', '-'])
# No number at the end
False
>>> is_equation(['-', 7, '+', 2, '=', '?', '-', 6])
# No number at the start
False
>>> is_equation([-7, '+', 2, '?', '+', 6, '=', 9])
# Two adjacent numbers (2 and ?)
False
>>> is_equation([-7, '+', 2, '+', '-', 6, '=', 9])
# Two adjacent operators (+ and -)
False
>>> is_equation([-7, '+', 2, '=', '?', '=', 6])
# More than one =
False
"""
number, equals = True, 0
for x in s:
ok = (number and (_______)) or (_______ ['+', '-', '='])
if not ok:
(a)
(b)
return False
if x == '=':
equals += 1
number = not number
return _______
(c)
i. (1.0 pt) Fill in blank (a).
# isinstance(x, int) or x == ?
# isinstance(x, int) and x == ?
isinstance(x, int) or x == '?'
# isinstance(x, int) and x == '?'
ii. (2.0 pt) Fill in blank (b).
not number and x in
iii. (2.0 pt) Fill in blank (c).
not number and equals == 1

## Page 7

(b) (5.0 points)
Definition. A list of integers answers satisfies an equation if there is one integer per placeholder ? in the
equation, and after replacing each ? with the corresponding integer from answers, the expression on the
left of = has an equal value to the expression on the right of =.
Implement tally to complete the implementation of evaluate. The evaluate function takes an equation
and a list of integers called answers that contains one value for each ? in the equation. It returns True if
answers satisfies the equation and False otherwise.
The count method of a list takes a value and returns the number of items in the list that are equal to the
value.
def evaluate(equation, answers):
"""Return whether the equation is true once each ? is filled by the corresponding answer.
>>> evaluate([7, '-', 2, '=', '?', '+', 4], [1])
# 7 - 2 == 1 + 4
True
>>> evaluate([7, '-', 2, '=', '?', '-', 4], [3])
# 7 - 2 != 3 - 4
False
>>> evaluate([7, '-', 2, '=', 1, '+', 4], [])
# 7 - 2 == 1 + 4
True
>>> evaluate([7, '-', '?', '=', '?', '-', 4], [2, 9])
# 7 - 2 == 9 - 4
True
"""
assert is_equation(equation) and len(answers) == equation.count('?')
eq_iter, ans_iter = iter(equation), iter(answers)
return tally(eq_iter, ans_iter) == tally(eq_iter, ans_iter)
def tally(eq, ans):
"""A helper function for evaluate that computes the value of one side of an equation,
stopping either at an = sign or the end of the equation."""
number, total = True, 0
multiplier = 1
# should always be either 1 or -1
for x in eq:
if _______:
(d)
if x == '?':
_______
(e)
total += multiplier * x
else:
if x == '=':
_______
(f)
else:
multiplier = _______[x]
# Hint: use a dictionary
(g)
number = not number
return total

## Page 8

i. (1.0 pt) Fill in blank (d).
number
# not number
# isinstance(x, int)
# not isinstance(x, int)
ii. (1.0 pt) Fill in blank (e).
x = next(ans)
iii. (1.0 pt) Fill in blank (f).
return total
# return sum(ans)
# return sum(eq)
# total += sum(ans)
# total += sum(eq)
# total += tally(eq, ans)
# total -= tally(eq, ans)
iv. (2.0 pt) Fill in blank (g). Hint: Use a dictionary.
{'+': 1, '-': -1}

## Page 9

(c) (6.0 points)
Implement feasible, which takes an equation and a range of integers called allowed. It returns True if
it’s possible to satisfy the equation using numbers from allowed and False otherwise. In other words, it
returns whether it is possible to replace each ? in the equation with some number from allowed such that
the expressions to the left and right of = are indeed equal. The same number can replace more than one ?.
Assume evaluate is implemented correctly. You may call evaluate.
def feasible(eq, allowed=range(0, 10)):
"""Return whether it's possible to satisfy the equation eq using numbers from allowed.
>>> feasible([7, '+', 2, '=', '?', '+', 6])
# the ? could be 3
True
>>> feasible(['?', '+', 2, '=', '?', '+', 6])
# the first ? could be 7 and the second 3
True
>>> feasible([-7, '+', 2, '=', '?', '+', 6])
False
>>> feasible(['?', '+', 5, '=', '?', '-', 6])
False
>>> feasible(['?', '+', 5, '=', '?', '-', 6], range(-10, 10))
# -5 and 6, for example
True
"""
if '?' not in eq:
return _______
(h)
n = min([i for i in range(len(eq)) if _______])
# index of the first ?
(i)
return any([_______ for x in allowed])
(j)
i. (2.0 pt) Fill in blank (h).
evaluate(eq, [])
ii. (1.0 pt) Fill in blank (i).
# i == '?'
# i != '?'
eq[i] == '?'
# eq[i] != '?'
iii. (3.0 pt) Fill in blank (j). You may not write for or in or map or range.
feasible(eq[:n] + [x] + eq[n+1:], allowed)

## Page 10

(d) (5.0 points)
Implement solve, which takes an equation and a range of integers called allowed. It returns an iterator
over lists of integers, and each of these lists satisfies the equation. You may call evaluate and feasible.
def print_all(t):
for x in t:
print(x)
def solve(equation, allowed=range(0, 10)):
"""Return an iterator over all answer lists that satisfy an equation.
>>> print_all(solve([7, '+', 2, '=', '?', '+', 6]))
[3]
>>> print_all(solve(['?', '-', 2, '=', '?', '+', 6]))
[8, 0]
[9, 1]
>>> print_all(solve(['?', '=', '?', '+', '?'], range(1, 4)))
[2, 1, 1]
[3, 1, 2]
[3, 2, 1]
"""
def candidates(n):
"""Yield all possible answer lists with n values."""
if n == 0:
yield []
else:
for first in allowed:
for rest in _______:
(k)
yield _______
(l)
blanks = equation.count('?')
# the number of ? in equation
return _______(_______ , candidates(blanks))
(m)
(n)
i. (1.0 pt) Fill in blank (k).
# allowed
# equation
# solve(equation[1:], allowed)
# solve(equation[2:], allowed)
candidates(n-1)
# candidates(n-first)

## Page 11

ii. (1.0 pt) Fill in blank (l).
# first + rest
[first] + rest
# first + [rest]
# [first, rest]
# [[first], rest]
# [first, [rest]]
iii. (1.0 pt) Fill in blank (m).
# map
filter
# any
# all
# zip
iv. (2.0 pt) Fill in blank (n).
lambda a: evaluate(equation, a)


---

## Same Semester

- [61a-fa25-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa25-final / P02-DO-YOU-COPY](p02-do-you-copy.md)
- [61a-fa25-final / P04-TRIM-THE-TREE](p04-trim-the-tree.md)
- [61a-fa25-final / P05-DOWNLOADS](p05-downloads.md)
- [61a-fa25-final / P06-SCHEME-VS-PYTHON](p06-scheme-vs-python.md)
- [61a-fa25-final / P07-STUDENTS](p07-students.md)
- [61a-fa25-final / P08-STUDENTS-IN-SQL](p08-students-in-sql.md)
- [61a-fa25-final / P09-FINAL-BOSS](p09-final-boss.md)
- [61a-fa25-mt1 / P01-WHAT-WOULD-PYTHON-DO-OT](../61a-fa25-mt1/p01-what-would-python-do-ot.md)
- [61a-fa25-mt1 / P02-SILKSONG](../61a-fa25-mt1/p02-silksong.md)
- [61a-fa25-mt1 / P03-SAJA-BOYS](../61a-fa25-mt1/p03-saja-boys.md)
- [61a-fa25-mt1 / P04-WE-RE-GOING-UP-UP-UP](../61a-fa25-mt1/p04-we-re-going-up-up-up.md)
