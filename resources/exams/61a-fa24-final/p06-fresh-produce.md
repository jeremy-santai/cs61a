---
course: CS61A
term: Fall 2024
assessment: Final
source_pdf: 61a-fa24-final_sol.pdf
exam_slug: 61a-fa24-final
problem_number: 6
problem_title: "Fresh Produce"
page_range: [14, 16]
points: "12.0 points"
topics: ["trees", "oop"]
concepts: ["trees", "oop"]
question_types: ["implementation", "predicate"]
difficulty: "hard"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 6 — Fresh Produce

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** trees, oop
- **Concepts:** trees, oop
- **Question types:** implementation, predicate
- **Difficulty:** hard
- **Source pages:** 14-16

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: Final
- Source PDF: `61a-fa24-final_sol.pdf`

## Full extracted content

## Page 14

6. (12.0 points)
Fresh Produce
(a) (5.0 points)
Implement products, which takes a Tree instance t with positive integer labels and a positive integer n.
It returns True if every path from the root of t to a leaf has labels that equal n when multiplied together.
The Tree class appears on Page 2 (left side) of the Midterm 2 Study Guide.
def products(t, n):
"""Return whether the product of labels along every root-to-leaf path is n.
>>> products(Tree(1, [Tree(2, [Tree(3)]), Tree(6)]), 6)
True
>>> products(Tree(1, [Tree(2, [Tree(3)]), Tree(6)]), 12)
False
>>> products(Tree(1, [Tree(2, [Tree(3)]), Tree(5)]), 6)
False
>>> products(Tree(1, [Tree(5, [Tree(2)]), Tree(12)]), 12)
False
"""
assert type(n) == int
if t.is_leaf():
return _______
(a)
if _______:
(b)
return False
return _______
(c)
i. (1.0 pt) Fill in blank (a).
# True
# False
n == t.label
# n % t.label == 0
# n % t.label > 0
ii. (1.0 pt) Fill in blank (b).
# n != t.label
# n < t.label
# n > t.label
n % t.label > 0
iii. (3.0 pt) Fill in blank (c). Important: The second argument to a call to products must be an integer
(int).
all([products(b, n // t.label) for b in t.branches])

## Page 15

(b) (7.0 points)
Definition. An increasing sequence is a sequence of integers in which each element after the first is larger
than the previous element.
Implement produce, which takes a positive integer n. It returns a Tree of positive integers in which:
• The product of the labels along every root-to-leaf path is n,
• Every increasing sequence of integers starting with 1 that has product n is a root-to-leaf path, and
• Every sequence of siblings (nodes with a common parent) is an increasing sequence.
def produce(n):
"""Return the largest tree in which the labels for every root-to-label path
are increasing and have product n. Put all siblings in increasing order.
>>> produce(12)
Tree(1, [Tree(2, [Tree(6)]), Tree(3, [Tree(4)]), Tree(12)])
>>> print(produce(24))
# Paths are 1-2-3-4, 1-2-12, 1-3-8, 1-4-6, and 1-24
"""
def grow(t, x):
for k in range(_______, x + 1):
(d)
if _______ % k == 0:
(e)
branch = _______
(f)
if _______:
(g)
t.branches.append(branch)
return t
return grow(Tree(1), n)
i. (1.0 pt) Fill in blank (d).
# 0
# 1
# x
# t.label
t.label + 1

## Page 16

ii. (1.0 pt) Fill in blank (e).
x
# n
# t.label
# (t.label // x)
# (t.label // k)
iii. (2.0 pt) Fill in blank (f).
# Tree(k)
# Tree(x)
# grow(Tree(k), x)
# grow(Tree(x), k)
grow(Tree(k), x // k)
# grow(Tree(x), x // k)
iv. (3.0 pt) Fill in blank (g).
not branch.is_leaf() or x == k


---

## Same Semester

- [61a-fa24-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa24-final / P02-LINE-DIAGRAM](p02-line-diagram.md)
- [61a-fa24-final / P03-MAKE-TENS](p03-make-tens.md)
- [61a-fa24-final / P04-COUNT-MISSES](p04-count-misses.md)
- [61a-fa24-final / P05-PROMOTION-TO-CS-61B](p05-promotion-to-cs-61b.md)
- [61a-fa24-final / P07-A-PAIR-OF-SCHEMES](p07-a-pair-of-schemes.md)
- [61a-fa24-final / P08-ARCANE-JOBS](p08-arcane-jobs.md)
- [61a-fa24-final / P09-APE-PULL-US](p09-ape-pull-us.md)
- [61a-fa24-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa24-mt1/p01-what-would-python-display.md)
- [61a-fa24-mt1 / P02-WHICH-ONE](../61a-fa24-mt1/p02-which-one.md)
- [61a-fa24-mt1 / P03-FINAL-DIGIT](../61a-fa24-mt1/p03-final-digit.md)
- [61a-fa24-mt1 / P04-CLOSE-ENOUGH](../61a-fa24-mt1/p04-close-enough.md)
- [61a-fa24-mt1 / P05-SHIFTY](../61a-fa24-mt1/p05-shifty.md)
- [61a-fa24-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa24-mt2/p01-what-would-python-display.md)
- [61a-fa24-mt2 / P02-PIZZA-BY-THE-SLICE](../61a-fa24-mt2/p02-pizza-by-the-slice.md)
- [61a-fa24-mt2 / P03-CS-61A-SOFTWARE-STORE](../61a-fa24-mt2/p03-cs-61a-software-store.md)
- [61a-fa24-mt2 / P04-ALMOST-A-PERFECT-QUESTION](../61a-fa24-mt2/p04-almost-a-perfect-question.md)
- [61a-fa24-mt2 / P05-HOW-LONG-IS-THIS-EXAM](../61a-fa24-mt2/p05-how-long-is-this-exam.md)
- [61a-fa24-mt2 / P06-NICE-PATH](../61a-fa24-mt2/p06-nice-path.md)
