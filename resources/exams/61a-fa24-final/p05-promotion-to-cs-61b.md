---
course: CS61A
term: Fall 2024
assessment: Final
source_pdf: 61a-fa24-final_sol.pdf
exam_slug: 61a-fa24-final
problem_number: 5
problem_title: "Promotion to CS 61B"
page_range: [10, 13]
points: "16.0 points"
topics: ["linked-lists", "oop", "lists"]
concepts: ["linked-lists", "oop", "lists"]
question_types: ["trace", "implementation", "mutation"]
difficulty: "hard"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 5 — Promotion to CS 61B

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** linked-lists, oop, lists
- **Concepts:** linked-lists, oop, lists
- **Question types:** trace, implementation, mutation
- **Difficulty:** hard
- **Source pages:** 10-13

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: Final
- Source PDF: `61a-fa24-final_sol.pdf`

## Full extracted content

## Page 10

5. (16.0 points)
Promotion to CS 61B
Definition. Given a sequence s and positions (indices) i and j in s with i < j, promoting an element to
i from j means reordering s so that the element originally at position j is now at position i, all elements
originally positioned between i and j increase their position (index) by one, and all other elements stay where
they are. The beginning of s is position 0. For example, in the list [30, 60, 90, 120, 150, 180], promoting
to 2 from 4 would place the number 150 (original position 4) just before 90 (originally position 2) and increases
the positions of both 90 and 120 by one, resulting in [30, 60, 150, 90, 120, 180].
(a) (4.0 points)
Implement promote, which takes a list of numbers s and two non-negative integers i and j. It returns a
new list promoting to i from j in s. Do not mutate s.
Hint: For any list s, s[len(s):] evaluates to [].
def promote(s, i, j):
"""Return a list in which s[j] is at index i without mutating s.
>>> promote([3, 6, 9, 12, 15, 18], 2, 4)
[3, 6, 15, 9, 12, 18]
>>> promote([3, 6, 9, 12, 15, 18], 0, 4)
[15, 3, 6, 9, 12, 18]
"""
assert i >= 0 and i < j and j < len(s)
return s[:i] + _______ + _______ + s[_______:]
(a)
(b)
(c)
i. (2.0 pt) Fill in blank (a). Select all correct answers.
2 s[j]
■[s[j]]
2 list(s[j])
2 s[j:j]
■s[j:j+1]
ii. (1.0 pt) Fill in blank (b).
s[i:j]
# s[i+1:j]
# s[i:j+1]
# s[i+1:j+1]
iii. (1.0 pt) Fill in blank (c).
# i
# i+1
# j
j+1

## Page 11

(b) (4.0 points)
Implement promotions, which takes two lists of numbers s and t that have the same elements, possibly in
different orders. It returns the minimum number of promotions that must be applied to s so that it has
the same order as t. Assume promote is implemented correctly.
def promotions(s, t):
"""Return the minimum times promote must be called to start from s and return t.
>>> promotions([2, 4, 6, 8, 10, 12],
...
[2, 6, 8, 4, 12, 10])
# promote (1, 2) then (2, 3) then (4, 5)
>>> promotions([6, 1, 6, 1, 6, 1],
...
[1, 1, 6, 6, 1, 6])
# promote (0, 1) then (1, 5)
>>> promotions([1, 2, 3], [1, 2, 3])
# no promotions needed
>>> promotions([1, 2, 1, 2], [2, 1, 2, 1])
# promote (0, 3)
"""
assert sorted(s) == sorted(t)
# Check that s & t have the same elements (disregarding order)
if len(s) == 0:
return 0
elif _______:
(d)
return promotions(s[1:], t[1:])
else:
return 1 + min([promotions(_______, t[1:]) for j in range(1, len(s)) if _______])
(e)
(f)
i. (1.0 pt) Fill in blank (d).
# s == t
# s != t
s[0] == t[0]
# s[0] != t[0]
# sorted(s) == t
# s == sorted(t)
ii. (2.0 pt) Fill in blank (e).
promote(s, 0, j)[1:] OR s[:j] + s[j+1:]
iii. (1.0 pt) Fill in blank (f).
# s[0] == t[j]
# s[1] == t[j]
s[j] == t[0]
# s[j] == t[1]

## Page 12

(c) (8.0 points)
Implement promote_link, which takes a Link instance s (a non-empty linked list) and two non-negative
integers i and j with i<j and j less than the length of s. It mutates s by promoting to i from j and then
returns s.
The Link class appears on Page 2 (left side) of the Midterm 2 Study Guide.
def promote_link(s, i, j):
"""Mutate linked list s so that the item at index j is at index i.
>>> a = Link(3, Link(6, Link(9, Link(12, Link(15, Link(18))))))
>>> print(promote_link(a, 2, 4))
<3 6 15 9 12 18>
>>> print(promote_link(a, 0, 4))
<12 3 6 15 9 18>
>>> promote_link(a, 1, 3) is a
True
"""
assert i >= 0 and i < j
if i > 0:
_______
(g)
else:
insert, tail = s.first, s.rest
while j > 0:
_______
# Hint: use multiple assignment: ___ , ___ = ___ , ___
(h)
tail, j = tail.rest, j-1
_______ = insert
(i)
return _______
(j)
i. (2.0 pt) Fill in blank (g).
# promote_link(s.rest, i-1, j)
# return promote_link(s.rest, i-1, j)
# promote_link(s.rest, i, j-1)
# return promote_link(s.rest, i, j-1)
promote_link(s.rest, i-1, j-1)
# return promote_link(s.rest, i-1, j-1)
ii. (2.0 pt) Fill in blank (h). Hint: Use multiple assignment: ___ , ___ = ___ , ___
insert, tail.first = tail.first, insert

## Page 13

iii. (1.0 pt) Fill in blank (i).
s.first
# s.rest.first
# tail.first
# tail.rest.first
iv. (1.0 pt) Fill in blank (j).
s
# tail
# Link(insert, tail.rest)
# Link(s.first, tail.rest)
v. (2.0 pt) What is displayed by the call to print in this code?
odds = Link(3, Link(5, Link(7, Link(9))))
for i in range(3):
promote_link(odds, 0, 3)
print(odds)
# <3 5 7 9>
# <3 9 7 5>
<5 7 9 3>
# <5 9 7 3>
# <9 7 5 3>
# <9 3 5 7>


---

## Same Semester

- [61a-fa24-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa24-final / P02-LINE-DIAGRAM](p02-line-diagram.md)
- [61a-fa24-final / P03-MAKE-TENS](p03-make-tens.md)
- [61a-fa24-final / P04-COUNT-MISSES](p04-count-misses.md)
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
