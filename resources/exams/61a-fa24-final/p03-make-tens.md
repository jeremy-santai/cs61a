---
course: CS61A
term: Fall 2024
assessment: Final
source_pdf: 61a-fa24-final_sol.pdf
exam_slug: 61a-fa24-final
problem_number: 3
problem_title: "Make Tens"
page_range: [5, 5]
points: "5.0 points"
topics: ["lists"]
concepts: ["lists"]
question_types: ["implementation", "predicate"]
difficulty: "easy"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 3 — Make Tens

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** lists
- **Concepts:** lists
- **Question types:** implementation, predicate
- **Difficulty:** easy
- **Source pages:** 5-5

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: Final
- Source PDF: `61a-fa24-final_sol.pdf`

## Full extracted content

## Page 5

3. (5.0 points)
Make Tens
A list of numbers is easier for a person to sum up if it can be split into groups that all sum to 10. Implement
tens, which takes a list of positive numbers s. It returns True if, for every positive integer i where 10 * i <=
sum(s), there is a positive k that satisfies sum(s[0:k]) == 10 * i. Otherwise, it returns False.
def tens(s):
"""Return whether every multiple of 10 less than or equal to sum(s) appears as a prefix of s.
>>> tens([3, 2, 2, 3, 6, 2, 2, 4, 1, 5, 2]) # sum(s[:4])==10, sum(s[:7])==20, sum(s[:10])==30
True
>>> tens([3, 2, 2, 3, 6, 2, 6, 1, 5, 2]) # sum(s[:4])==10, but no slice starting at 0 sums to 20
False
"""
t = 0
for x in s:
t += x
if _______:
(g)
return _______
(h)
if t == _______:
(i)
t = _______
(j)
return True
(a) (1.0 pt) Fill in blank (g).
# t == 10
# t != 10
t > 10
# t < 10
(b) (2.0 pt) Fill in blank (h). Select all correct answers.
■False
2 t % 10 == 0
2 t % 10 != 0
2 sum(s) % 10 == 0
2 sum(s) % 10 != 0
(c) (1.0 pt) Fill in blank (i).
# 0
# x
(d) (1.0 pt) Fill in blank (j).


---

## Same Semester

- [61a-fa24-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa24-final / P02-LINE-DIAGRAM](p02-line-diagram.md)
- [61a-fa24-final / P04-COUNT-MISSES](p04-count-misses.md)
- [61a-fa24-final / P05-PROMOTION-TO-CS-61B](p05-promotion-to-cs-61b.md)
- [61a-fa24-final / P06-FRESH-PRODUCE](p06-fresh-produce.md)
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
