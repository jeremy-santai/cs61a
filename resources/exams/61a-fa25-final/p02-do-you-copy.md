---
course: CS61A
term: Fall 2025
assessment: Final
source_pdf: 61a-fa25-final_sol.pdf
exam_slug: 61a-fa25-final
problem_number: 2
problem_title: "Do You Copy?"
page_range: [4, 5]
points: "5.0 points"
topics: ["environment-diagrams", "lists"]
concepts: ["environment-diagrams", "lists"]
question_types: ["trace", "environment-diagram"]
difficulty: "easy"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 2 — Do You Copy?

## Semantic summary

- **Summary:** CS61A exam problem with extracted prompt, answers, and supporting context.
- **Topics:** environment-diagrams, lists
- **Concepts:** environment-diagrams, lists
- **Question types:** trace, environment-diagram
- **Difficulty:** easy
- **Source pages:** 4-5

## Source

- Course: CS61A
- Term: Fall 2025
- Assessment: Final
- Source PDF: `61a-fa25-final_sol.pdf`

## Full extracted content

## Page 4

2. (5.0 points)
Do You Copy?
Draw an environment diagram to answer the following questions. Only the questions will be scored.
1: def copy(s):
2:
return s[:1] + s[1:]
3: inner = [5, [6]]
4: first = copy(inner)
5: second = inner[1]
6: inner[0] = 7
7: inner.append(7)
8: inner[1].append(7)
9: inner[1] = 8
10: print(first)
11: print(second)
(a) (2.0 pt) What is displayed by print(first) on line 10?
# [5, [6]]
# [5, [6], 7]
# [5, [6], 7, 7]
[5, [6, 7]]
# [5, [6, 7], 7]
# [7, [6], 7]
# [7, [6, 7]]
# [7, [6, 7], 7]
# [7, 8]
# [7, 8, 7]
# [[6]]
# [[6, 7]]
# [[6], 7]
# [[6, 7], 7]
# [8]
# [8, 7]
(b) (2.0 pt) What is displayed by print(second) on line 11?
# 8
# [6]
# [[6]]
[6, 7]
# [[6, 7]]
# [[6], 7]
# [8]
# [8, 7]

## Page 5

(c) (1.0 pt) What is the order of growth of the time it takes to evaluate [sum(s[:i]) for i in range(len(s))]
in terms of the length of s for a list of numbers s. The sum function takes linear time in the length of its
input. Slicing a list takes linear time in the length of the slice. Creating a range and calling len on a list
both take constant time (one step each).
# logarithmic
# linear
quadratic
# exponential


---

## Same Semester

- [61a-fa25-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
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
