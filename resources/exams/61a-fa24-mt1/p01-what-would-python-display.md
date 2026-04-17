---
course: CS61A
term: Fall 2024
assessment: MT1
source_pdf: 61a-fa24-mt1_sol.pdf
exam_slug: 61a-fa24-mt1
problem_number: 1
problem_title: "What Would Python Display?"
page_range: [3, 3]
points: "8.0 points"
topics: ["python-evaluation"]
concepts: ["python-evaluation"]
question_types: ["trace"]
difficulty: "medium"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 1 — What Would Python Display?

## Semantic summary

- **Summary:** Tracing and evaluation problem focused on execution order, closures, iterators, or object behavior.
- **Topics:** python-evaluation
- **Concepts:** python-evaluation
- **Question types:** trace
- **Difficulty:** medium
- **Source pages:** 3-3

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: MT1
- Source PDF: `61a-fa24-mt1_sol.pdf`

## Full extracted content

## Page 3

1. (8.0 points)
What Would Python Display?
Answer the following questions about the output printed by this code.
def mad(max):
g = lambda: (print(1) or 2) or (print(3) or 4)
print(max(5, 6))
return g
print(mad(print)(), 7, print(8))
(a) (2.0 pt) What is the last line printed?
# 1 7 8
# 2 7 8
2 7 None
# 4 7 8
# 4 7 None
# None 7 8
# None 7 None
(b) (4.0 pt) Which of these whole lines appear somewhere in the printed output? Select all that apply.
■1
2 1 2
2 1 2 3
2 1 2 3 4
2 3
2 5
■5 6
2 6
2 7
■8
■None
2 None None
2 True
(c) (2.0 pt) What order do 1, 6, and 8 appear in the printed output? These numbers may appear as part of
longer lines. If a number appears twice, consider just the first occurence.
# 1 6 8
# 1 8 6
6 1 8
# 6 8 1
# 8 1 6
# 8 6 1


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
- [61a-fa24-mt1 / P02-WHICH-ONE](p02-which-one.md)
- [61a-fa24-mt1 / P03-FINAL-DIGIT](p03-final-digit.md)
- [61a-fa24-mt1 / P04-CLOSE-ENOUGH](p04-close-enough.md)
- [61a-fa24-mt1 / P05-SHIFTY](p05-shifty.md)
- [61a-fa24-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa24-mt2/p01-what-would-python-display.md)
- [61a-fa24-mt2 / P02-PIZZA-BY-THE-SLICE](../61a-fa24-mt2/p02-pizza-by-the-slice.md)
- [61a-fa24-mt2 / P03-CS-61A-SOFTWARE-STORE](../61a-fa24-mt2/p03-cs-61a-software-store.md)
- [61a-fa24-mt2 / P04-ALMOST-A-PERFECT-QUESTION](../61a-fa24-mt2/p04-almost-a-perfect-question.md)
- [61a-fa24-mt2 / P05-HOW-LONG-IS-THIS-EXAM](../61a-fa24-mt2/p05-how-long-is-this-exam.md)
- [61a-fa24-mt2 / P06-NICE-PATH](../61a-fa24-mt2/p06-nice-path.md)
