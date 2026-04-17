---
course: CS61A
term: Fall 2025
assessment: MT1
source_pdf: 61a-fa25-mt1_sol.pdf
exam_slug: 61a-fa25-mt1
problem_number: 3
problem_title: "Saja Boys"
page_range: [6, 7]
points: "8.0 points"
topics: ["cs61a"]
concepts: ["cs61a"]
question_types: ["implementation", "predicate"]
difficulty: "medium"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 3 — Saja Boys

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** cs61a
- **Concepts:** cs61a
- **Question types:** implementation, predicate
- **Difficulty:** medium
- **Source pages:** 6-7

## Source

- Course: CS61A
- Term: Fall 2025
- Assessment: MT1
- Source PDF: `61a-fa25-mt1_sol.pdf`

## Full extracted content

## Page 6

3. (8.0 points)
Saja Boys
Definition. A positive integer is patterned if every odd digit has a larger even digit somewhere before it. For
example, 4123827 is patterned because the odd digit 7 has 8 (which is even and larger than 7) before it, and the
3 and 1 both have 4 before them.
Implement patterned, which takes a positive integer n. It returns True if n is patterned and False otherwise.
Your implementation should iterate through the digits of n just once. The name odd in the implementation
should always be assigned to an integer from 0 to 9 (inclusive).
def patterned(n):
"""Return whether every odd digit of n has a larger even digit somewhere before it.
>>> patterned(4123827)
# 8 is before 7; 4 is before 1 and 3
True
>>> patterned(4412123384137)
True
>>> patterned(2468)
# No odd digits
True
>>> patterned(1)
# No even digits
False
>>> patterned(8192)
# 9 does not have a larger even digit before it (or anywhere)
False
>>> patterned(238)
# 3 does not have a larger even digit before it (8 comes after)
False
>>> patterned(3888)
# 3 does not have a larger even digit before it (8 comes after)
False
>>> patterned(4321587)
# 5 does not have a larger even digit before it (8 comes after)
False
"""
odd = 0
# Hint: use the name odd to keep track of a digit you'll need later
while n:
n, last = n // 10, n % 10
if last % 2 == 1:
_______
(a)
elif _______:
(b)
_______
(c)
return _______
(d)

## Page 7

(a) (2.0 pt) Fill in blank (a).
# return False
# return max(n) > last
# return n % 10 > last
# return n % 2 == 0 and n % 10 > last
# odd = 0
# odd = last
# odd = n % 10
# odd = max(n % 10, last)
odd = max(odd, last)
(b) (2.0 pt) Fill in blank (b). You may not use str or len or [ or ]
last > odd
(c) (2.0 pt) Fill in blank (c).
# return False
# return max(n) > last
# return n % 10 > last
# return n % 2 == 0 and n % 10 > last
odd = 0
# odd = last
# odd = n % 10
# odd = max(n % 10, last)
# odd = max(odd, last)
(d) (2.0 pt) Fill in blank (d).
# True
# False
odd == 0
# odd > 0
# last == 0
# last > 0
# last % 2 == 0
# last % 2 == 1


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
- [61a-fa25-mt1 / P01-WHAT-WOULD-PYTHON-DO-OT](p01-what-would-python-do-ot.md)
- [61a-fa25-mt1 / P02-SILKSONG](p02-silksong.md)
- [61a-fa25-mt1 / P04-WE-RE-GOING-UP-UP-UP](p04-we-re-going-up-up-up.md)
