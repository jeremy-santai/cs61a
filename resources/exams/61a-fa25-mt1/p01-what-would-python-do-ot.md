---
course: CS61A
term: Fall 2025
assessment: MT1
source_pdf: 61a-fa25-mt1_sol.pdf
exam_slug: 61a-fa25-mt1
problem_number: 1
problem_title: "What Would Python Do(ot)?"
page_range: [3, 3]
points: "6.0 points"
topics: ["python-evaluation"]
concepts: ["python-evaluation"]
question_types: ["trace"]
difficulty: "medium"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 1 — What Would Python Do(ot)?

## Semantic summary

- **Summary:** Tracing and evaluation problem focused on execution order, closures, iterators, or object behavior.
- **Topics:** python-evaluation
- **Concepts:** python-evaluation
- **Question types:** trace
- **Difficulty:** medium
- **Source pages:** 3-3

## Source

- Course: CS61A
- Term: Fall 2025
- Assessment: MT1
- Source PDF: `61a-fa25-mt1_sol.pdf`

## Full extracted content

## Page 3

1. (6.0 points)
What Would Python Do(ot)?
Assume the code below has been executed, and no errors occurred.
about = 6-7
about, face = 6, about * 7
def make_something(f):
if f(about):
f = lambda k: about
def something(about):
return print(f(about) or print(about))
return something
f = lambda x: 10 * x
Example Question: What would be displayed by evaluating print(5)? Answer: 5
(a) (2.0 pt) What would be displayed by evaluating print(print(face))
-7
None
(b) (4.0 pt) What would be displayed by evaluating make_something(print)(8)
None


---

## Same Semester

- [61a-fa25-final / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa25-final/p01-what-would-python-display.md)
- [61a-fa25-final / P02-DO-YOU-COPY](../61a-fa25-final/p02-do-you-copy.md)
- [61a-fa25-final / P03-MATH-PLACEMENT-EXAM](../61a-fa25-final/p03-math-placement-exam.md)
- [61a-fa25-final / P04-TRIM-THE-TREE](../61a-fa25-final/p04-trim-the-tree.md)
- [61a-fa25-final / P05-DOWNLOADS](../61a-fa25-final/p05-downloads.md)
- [61a-fa25-final / P06-SCHEME-VS-PYTHON](../61a-fa25-final/p06-scheme-vs-python.md)
- [61a-fa25-final / P07-STUDENTS](../61a-fa25-final/p07-students.md)
- [61a-fa25-final / P08-STUDENTS-IN-SQL](../61a-fa25-final/p08-students-in-sql.md)
- [61a-fa25-final / P09-FINAL-BOSS](../61a-fa25-final/p09-final-boss.md)
- [61a-fa25-mt1 / P02-SILKSONG](p02-silksong.md)
- [61a-fa25-mt1 / P03-SAJA-BOYS](p03-saja-boys.md)
- [61a-fa25-mt1 / P04-WE-RE-GOING-UP-UP-UP](p04-we-re-going-up-up-up.md)
