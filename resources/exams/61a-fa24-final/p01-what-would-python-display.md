---
course: CS61A
term: Fall 2024
assessment: Final
source_pdf: 61a-fa24-final_sol.pdf
exam_slug: 61a-fa24-final
problem_number: 1
problem_title: "What Would Python Display?"
page_range: [3, 3]
points: "6.0 points"
topics: ["python-evaluation", "generators", "lists"]
concepts: ["python-evaluation", "generators", "lists"]
question_types: ["trace"]
difficulty: "medium"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 1 — What Would Python Display?

## Semantic summary

- **Summary:** Tracing and evaluation problem focused on execution order, closures, iterators, or object behavior.
- **Topics:** python-evaluation, generators, lists
- **Concepts:** python-evaluation, generators, lists
- **Question types:** trace
- **Difficulty:** medium
- **Source pages:** 3-3

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: Final
- Source PDF: `61a-fa24-final_sol.pdf`

## Full extracted content

## Page 3

1. (6.0 points)
What Would Python Display?
Assume the following code has been executed.
def cut(s):
this = 1
for x in s:
if this:
this = x
yield this
else:
this = True
def paste(n):
yield n
for x in paste(n + 1):
yield 2 * x
yield n
def copy(t, k):
return [next(t) for x in range(k)]
nums = [0, 2, 4, 6, 8]
Write the output that would be displayed by printing the result of each expression. If an error occurs, write
ERROR.
(a) (2.0 pt) list(cut(nums))
# [0, 2, 4, 6, 8]
[0, 4, 6, 8]
# [1, 0, 2, 4, 6, 8]
# [1, 0, 4, 6, 8]
# [1, 2, 4, 6, 8]
# [2, 4, 6, 8]
(b) (2.0 pt) list(cut(map(lambda x: x - 4, cut(nums))))
[-4, 0, 4]
(c) (2.0 pt) copy(paste(0), 3)
[0, 2, 8]


---

## Same Semester

- [61a-fa24-final / P02-LINE-DIAGRAM](p02-line-diagram.md)
- [61a-fa24-final / P03-MAKE-TENS](p03-make-tens.md)
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
