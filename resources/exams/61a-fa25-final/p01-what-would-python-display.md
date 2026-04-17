---
course: CS61A
term: Fall 2025
assessment: Final
source_pdf: 61a-fa25-final_sol.pdf
exam_slug: 61a-fa25-final
problem_number: 1
problem_title: "What Would Python Display?"
page_range: [3, 3]
points: "5.0 points"
topics: ["python-evaluation"]
concepts: ["python-evaluation"]
question_types: ["trace"]
difficulty: "easy"
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
- **Difficulty:** easy
- **Source pages:** 3-3

## Source

- Course: CS61A
- Term: Fall 2025
- Assessment: Final
- Source PDF: `61a-fa25-final_sol.pdf`

## Full extracted content

## Page 3

1. (5.0 points)
What Would Python Display?
Assume the following code has been executed.
square = lambda x: x * x
def times(a, b, c):
x = a
f = lambda y: x * y
x = b
g = (lambda q: lambda r: q * r)(x)
x = c
print(f(g(x)))
def delay(s):
last = None
for x in s:
if last:
print(x)
return last
last = x
w = [print, abs, square, print]
Write the output that would be displayed by evaluating each expression below. If an error occurs, write ERROR,
but also write any output that is displayed before the error occurs.
Example: For print(square(5)) you should answer 25.
(a) (2.0 pt) times(2, 3, 10)
(b) (3.0 pt) print(delay(map(lambda f: f(-2), w)))
2-2


---

## Same Semester

- [61a-fa25-final / P02-DO-YOU-COPY](p02-do-you-copy.md)
- [61a-fa25-final / P03-MATH-PLACEMENT-EXAM](p03-math-placement-exam.md)
- [61a-fa25-final / P04-TRIM-THE-TREE](p04-trim-the-tree.md)
- [61a-fa25-final / P05-DOWNLOADS](p05-downloads.md)
- [61a-fa25-final / P06-SCHEME-VS-PYTHON](p06-scheme-vs-python.md)
- [61a-fa25-final / P07-STUDENTS](p07-students.md)
- [61a-fa25-final / P08-STUDENTS-IN-SQL](p08-students-in-sql.md)
- [61a-fa25-final / P09-FINAL-BOSS](p09-final-boss.md)
- [61a-fa25-mt1 / P01-WHAT-WOULD-PYTHON-DO-OT](../61a-fa25-mt1/p01-what-would-python-do-ot.md)
- [61a-fa25-mt1 / P02-SILKSONG](../61a-fa25-mt1/p02-silksong.md)
- [61a-fa25-mt1 / P03-SAJA-BOYS](../61a-fa25-mt1/p03-saja-boys.md)
- [61a-fa25-mt1 / P04-WE-RE-GOING-UP-UP-UP](../61a-fa25-mt1/p04-we-re-going-up-up-up.md)
