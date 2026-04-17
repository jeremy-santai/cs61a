---
course: CS61A
term: Fall 2024
assessment: MT2
source_pdf: 61a-fa24-mt2_sol.pdf
exam_slug: 61a-fa24-mt2
problem_number: 6
problem_title: "Nice Path!"
page_range: [14, 15]
points: "0.0 points"
topics: ["trees", "lists"]
concepts: ["trees", "lists"]
question_types: ["mixed"]
difficulty: "easy"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 6 — Nice Path!

## Semantic summary

- **Summary:** CS61A exam problem with extracted prompt, answers, and supporting context.
- **Topics:** trees, lists
- **Concepts:** trees, lists
- **Question types:** mixed
- **Difficulty:** easy
- **Source pages:** 14-15

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: MT2
- Source PDF: `61a-fa24-mt2_sol.pdf`

## Full extracted content

## Page 14

6. (0.0 points)
Nice Path!
This A+ question is not worth any points. It can only affect your course grade if you have a high
A and might receive an A+. Finish the rest of the exam first!
(a) (0.0 pt) Fill in the blank of max_path, which takes a Tree of integers t and a function g. It returns a list
s containing the labels along the path from the root of t to a leaf for which g(s) is as large or larger than
for any other path. In case of a tie, return any path with a maximum g(s) value.
def climb(t, f):
if t.is_leaf():
return [t.label]
return [t.label] + climb(max(t.branches, key=f), f)
def max_path(t, g):
"""Return the path s from the root of t to a leaf for which g(s) is largest.
>>> scare = Tree(0, [Tree(4), Tree(5, [Tree(10)]), Tree(2)])
>>> crow = Tree(4, [Tree(5), Tree(9, [scare, Tree(7, [Tree(6)])]), Tree(8)])
>>> max_path(crow, lambda p: -p[-1])
# The path to the smallest leaf
[4, 9, 0, 2]
>>> max_path(crow, len)
# The longest path
[4, 9, 0, 5, 10]
>>> max_path(crow, lambda p: -abs(p[0]-p[-1]))
# To the leaf closest in value to the root
[4, 9, 0, 4]
"""
x = [t.label]
# You can use x instead of [t.label] to shorten your answer!
return climb(t, lambda b: _______ )
g(x + max_path(b, lambda p: g(x + p)))

## Page 15

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
- [61a-fa24-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa24-mt1/p01-what-would-python-display.md)
- [61a-fa24-mt1 / P02-WHICH-ONE](../61a-fa24-mt1/p02-which-one.md)
- [61a-fa24-mt1 / P03-FINAL-DIGIT](../61a-fa24-mt1/p03-final-digit.md)
- [61a-fa24-mt1 / P04-CLOSE-ENOUGH](../61a-fa24-mt1/p04-close-enough.md)
- [61a-fa24-mt1 / P05-SHIFTY](../61a-fa24-mt1/p05-shifty.md)
- [61a-fa24-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa24-mt2 / P02-PIZZA-BY-THE-SLICE](p02-pizza-by-the-slice.md)
- [61a-fa24-mt2 / P03-CS-61A-SOFTWARE-STORE](p03-cs-61a-software-store.md)
- [61a-fa24-mt2 / P04-ALMOST-A-PERFECT-QUESTION](p04-almost-a-perfect-question.md)
- [61a-fa24-mt2 / P05-HOW-LONG-IS-THIS-EXAM](p05-how-long-is-this-exam.md)
