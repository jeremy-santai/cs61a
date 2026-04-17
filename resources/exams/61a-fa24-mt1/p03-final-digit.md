---
course: CS61A
term: Fall 2024
assessment: MT1
source_pdf: 61a-fa24-mt1_sol.pdf
exam_slug: 61a-fa24-mt1
problem_number: 3
problem_title: "Final Digit"
page_range: [6, 6]
points: "6.0 points"
topics: ["cs61a"]
concepts: ["cs61a"]
question_types: ["implementation"]
difficulty: "medium"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 3 — Final Digit

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** cs61a
- **Concepts:** cs61a
- **Question types:** implementation
- **Difficulty:** medium
- **Source pages:** 6-6

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: MT1
- Source PDF: `61a-fa24-mt1_sol.pdf`

## Full extracted content

## Page 6

3. (6.0 points)
Final Digit
Implement final_digit, which takes a non-negative integer n. As long as n has more than one digit, replace n
with the sum of the digits of n. This process repeats until n becomes a single-digit number, which is returned.
def final_digit(n):
"""Sum the digits of n repeatedly to reach one digit.
>>> final_digit(321)
# 3 + 2 + 1 = 6
>>> final_digit(987)
# 9 + 8 + 7 = 24, and 2 + 4 = 6
>>> final_digit(989898989) # The digit sum is 77, 7 + 7 = 14, and 1 + 4 = 5
"""
while n >= 10:
s = _______
(a)
_______:
(b)
n, s = n // 10, _______
_______
(c)
(d)
return n
(a) (1.0 pt) Fill in blank (a).
# n
# n % 10
(b) (1.0 pt) Fill in blank (b).
# if s
# if n
# while s
while n
(c) (2.0 pt) Fill in blank (c).
# n
# s // 10
# n % 10
s + n % 10
# 10 * s + n % 10
(d) (2.0 pt) Fill in blank (d).
n = s


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
- [61a-fa24-mt1 / P04-CLOSE-ENOUGH](p04-close-enough.md)
- [61a-fa24-mt1 / P05-SHIFTY](p05-shifty.md)
- [61a-fa24-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa24-mt2/p01-what-would-python-display.md)
- [61a-fa24-mt2 / P02-PIZZA-BY-THE-SLICE](../61a-fa24-mt2/p02-pizza-by-the-slice.md)
- [61a-fa24-mt2 / P03-CS-61A-SOFTWARE-STORE](../61a-fa24-mt2/p03-cs-61a-software-store.md)
- [61a-fa24-mt2 / P04-ALMOST-A-PERFECT-QUESTION](../61a-fa24-mt2/p04-almost-a-perfect-question.md)
- [61a-fa24-mt2 / P05-HOW-LONG-IS-THIS-EXAM](../61a-fa24-mt2/p05-how-long-is-this-exam.md)
- [61a-fa24-mt2 / P06-NICE-PATH](../61a-fa24-mt2/p06-nice-path.md)
