---
course: CS61A
term: Fall 2024
assessment: MT2
source_pdf: 61a-fa24-mt2_sol.pdf
exam_slug: 61a-fa24-mt2
problem_number: 5
problem_title: "How Long is this Exam?"
page_range: [11, 13]
points: "11.0 points"
topics: ["linked-lists", "oop", "lists"]
concepts: ["linked-lists", "oop", "lists"]
question_types: ["implementation", "mutation"]
difficulty: "hard"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 5 — How Long is this Exam?

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** linked-lists, oop, lists
- **Concepts:** linked-lists, oop, lists
- **Question types:** implementation, mutation
- **Difficulty:** hard
- **Source pages:** 11-13

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: MT2
- Source PDF: `61a-fa24-mt2_sol.pdf`

## Full extracted content

## Page 11

5. (11.0 points)
How Long is this Exam?
(a) (5.0 points)
Implement longer, which takes two linked lists of numbers s and t. It returns the longer of the two. If
they have the same length, it returns s.
A linked list is either a Link instance or Link.empty. The Link class is on page 2 of the midterm 2 study
guide.
def longer(s, t):
"""Return the longer linked list, s or t. (Same length? return s.)
>>> longer(Link(2, Link(3)), Link.empty)
Link(2, Link(3))
>>> longer(Link(2, Link(3)), Link(4, Link(5)))
Link(2, Link(3))
>>> longer(Link(2, Link(3)), Link(4, Link(5, Link(6, Link(7)))))
Link(4, Link(5, Link(6, Link(7))))
>>> longer(Link.empty, Link.empty) is Link.empty
True
"""
a, b = s, t
while b is not Link.empty:
if _______:
(a)
return _______
(b)
_______
(c)
return _______
(d)
i. (2.0 pt) Fill in blank (a).
a is Link.empty
ii. (1.0 pt) Fill in blank (b).
# a
# b
# s
t
# longer(a, b)
# longer(s, t)

## Page 12

iii. (1.0 pt) Fill in blank (c).
# a = a.rest
# a = s.rest
# b = b.rest
# b = t.rest
a, b = a.rest, b.rest
# a, b = s.rest, t.rest
iv. (1.0 pt) Fill in blank (d).
# a
# b
s
# t
# longer(a, b)
# longer(s, t)

## Page 13

(b) (6.0 points)
Implement longest, which takes a linked list of postive integers s and a positive integer n. It returns the
longest sublist of s with elements that sum to a number less than or equal to n. Do not mutate s. In
case of a tie, return any of the longest sublists whose sum is n or less. Assume longer is implemented
correctly.
A sublist of a linked list s is a linked list with some (or none or all) of the elements of s in order.
Assume the sum of the elements of Link.empty is 0. Link.empty is a sublist of any linked list.
def longest(s, n):
"""Return the longest sublist of s that sums to n or less.
>>> longest(Link(5, Link(1, Link(3, Link(4, Link(2, Link(7)))))), 7)
Link(1, Link(3, Link(2)))
>>> longest(Link(5, Link(1, Link(3, Link(4, Link(2, Link(7)))))), 70)
Link(5, Link(1, Link(3, Link(4, Link(2, Link(7))))))
>>> longest(Link(3, Link(4, Link(5))), 2) is Link.empty
True
"""
if s is Link.empty:
return s
t = _______
(e)
if _______:
(f)
return longer( _______ , t)
(g)
else:
return t
i. (1.0 pt) Fill in blank (e).
# longest(s, n)
# longest(s, n - s.first)
longest(s.rest, n)
# longest(s.rest, n - s.first)
ii. (2.0 pt) Fill in blank (f).
s.first <= n
iii. (3.0 pt) Fill in blank (g).
Link(s.first, longest(s.rest, n - s.first))


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
- [61a-fa24-mt2 / P04-ALMOST-A-PERFECT-QUESTION](p04-almost-a-perfect-question.md)
- [61a-fa24-mt2 / P06-NICE-PATH](p06-nice-path.md)
