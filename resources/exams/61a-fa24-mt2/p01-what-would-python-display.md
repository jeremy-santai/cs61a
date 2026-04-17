---
course: CS61A
term: Fall 2024
assessment: MT2
source_pdf: 61a-fa24-mt2_sol.pdf
exam_slug: 61a-fa24-mt2
problem_number: 1
problem_title: "What Would Python Display?"
page_range: [3, 3]
points: "5.0 points"
topics: ["python-evaluation", "trees", "oop"]
concepts: ["python-evaluation", "trees", "oop"]
question_types: ["trace"]
difficulty: "easy"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 1 — What Would Python Display?

## Semantic summary

- **Summary:** Tracing and evaluation problem focused on execution order, closures, iterators, or object behavior.
- **Topics:** python-evaluation, trees, oop
- **Concepts:** python-evaluation, trees, oop
- **Question types:** trace
- **Difficulty:** easy
- **Source pages:** 3-3

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: MT2
- Source PDF: `61a-fa24-mt2_sol.pdf`

## Full extracted content

## Page 3

1. (5.0 points)
What Would Python Display?
Assume the following code has been executed. The Tree class appears on the midterm 2 study guide (page 2,
left side).
scare = Tree(0, [Tree(4), Tree(5, [Tree(10)]), Tree(2)])
crow = Tree(9, [scare, Tree(7, [Tree(6)])])
def climb(t, f):
if t.is_leaf():
return [t.label]
return [t.label] + climb(max(t.branches, key=f), f)
def run(t):
if t.is_leaf():
return t.label
else:
return max(map(run, t.branches))
def hide(t):
return t.label
jump = {(2 * x - 1): x for x in range(50)}
Write the value of each expression below or Error if an error occurs.
(a) (1.0 pt) crow.branches[0].label
(b) (1.0 pt) [hide(b) for b in scare.branches]
[4, 5, 2]
(c) (1.0 pt) climb(crow, hide)
[9, 7, 6]
(d) (1.0 pt) climb(crow, run)
[9, 0, 5, 10]
(e) (1.0 pt) jump[jump[13]]


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
- [61a-fa24-mt2 / P02-PIZZA-BY-THE-SLICE](p02-pizza-by-the-slice.md)
- [61a-fa24-mt2 / P03-CS-61A-SOFTWARE-STORE](p03-cs-61a-software-store.md)
- [61a-fa24-mt2 / P04-ALMOST-A-PERFECT-QUESTION](p04-almost-a-perfect-question.md)
- [61a-fa24-mt2 / P05-HOW-LONG-IS-THIS-EXAM](p05-how-long-is-this-exam.md)
- [61a-fa24-mt2 / P06-NICE-PATH](p06-nice-path.md)
