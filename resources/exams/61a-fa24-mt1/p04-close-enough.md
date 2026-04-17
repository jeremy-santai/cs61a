---
course: CS61A
term: Fall 2024
assessment: MT1
source_pdf: 61a-fa24-mt1_sol.pdf
exam_slug: 61a-fa24-mt1
problem_number: 4
problem_title: "Close Enough"
page_range: [7, 8]
points: "8.0 points"
topics: ["cs61a"]
concepts: ["cs61a"]
question_types: ["implementation", "predicate"]
difficulty: "medium"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 4 — Close Enough

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** cs61a
- **Concepts:** cs61a
- **Question types:** implementation, predicate
- **Difficulty:** medium
- **Source pages:** 7-8

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: MT1
- Source PDF: `61a-fa24-mt1_sol.pdf`

## Full extracted content

## Page 7

4. (8.0 points)
Close Enough
Implement close, which takes two non-negative integers m and n. It returns whether m can be changed into n
by either inserting one digit, removing one digit, or changing one digit. If m and n are the same number, they
are not close.
def close(m, n):
"""Return whether m can result from starting with n and adding, removing,
or changing one digit.
>>> close(3756, 3456) and close(3456, 346) and close(346, 3456) and close(456, 56)
True
>>> close(5, 5) or close(3456, 3546) or close(3456, 36) or close(34, 3456) or close(345, 456)
False
"""
if m < n:
m, n = n, m
while m or n:
if _______:
(a)
m, n = _______
(b)
else:
return _______ or _______
# Hint: check here that just one change is enough
(c)
(d)
return _______
(e)
(a) (1.0 pt) Fill in blank (a).
# m == n
# m // 10 == n // 10
# m // 10 == n
# m == n // 10
m % 10 == n % 10
(b) (2.0 pt) Fill in blank (b).
# n, m
m // 10, n // 10
# m // 10, n
# m, n // 10
# m % 10, n % 10

## Page 8

(c) (2.0 pt) Fill in blank (c).
# m == n
# m - n < 10
# n == 0
m // 10 == n // 10
# m % 10 == n % 10
# m % 100 == n % 100
(d) (2.0 pt) Fill in blank (d).
m // 10 == n
# m // 10 - n < 10
# n == 0
# m // 10 == 0
# m // 100 == n // 10
# (m // 10) % 10 == n % 10
(e) (1.0 pt) Fill in blank (e).
# m == n
# m == 0
# n == 0
# True
False


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
- [61a-fa24-mt1 / P05-SHIFTY](p05-shifty.md)
- [61a-fa24-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa24-mt2/p01-what-would-python-display.md)
- [61a-fa24-mt2 / P02-PIZZA-BY-THE-SLICE](../61a-fa24-mt2/p02-pizza-by-the-slice.md)
- [61a-fa24-mt2 / P03-CS-61A-SOFTWARE-STORE](../61a-fa24-mt2/p03-cs-61a-software-store.md)
- [61a-fa24-mt2 / P04-ALMOST-A-PERFECT-QUESTION](../61a-fa24-mt2/p04-almost-a-perfect-question.md)
- [61a-fa24-mt2 / P05-HOW-LONG-IS-THIS-EXAM](../61a-fa24-mt2/p05-how-long-is-this-exam.md)
- [61a-fa24-mt2 / P06-NICE-PATH](../61a-fa24-mt2/p06-nice-path.md)
