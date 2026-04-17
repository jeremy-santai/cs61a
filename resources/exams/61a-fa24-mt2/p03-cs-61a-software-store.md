---
course: CS61A
term: Fall 2024
assessment: MT2
source_pdf: 61a-fa24-mt2_sol.pdf
exam_slug: 61a-fa24-mt2
problem_number: 3
problem_title: "CS 61A Software Store"
page_range: [5, 6]
points: "6.0 points"
topics: ["trees", "oop", "lists"]
concepts: ["trees", "oop", "lists"]
question_types: ["mixed"]
difficulty: "medium"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 3 — CS 61A Software Store

## Semantic summary

- **Summary:** CS61A exam problem with extracted prompt, answers, and supporting context.
- **Topics:** trees, oop, lists
- **Concepts:** trees, oop, lists
- **Question types:** mixed
- **Difficulty:** medium
- **Source pages:** 5-6

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: MT2
- Source PDF: `61a-fa24-mt2_sol.pdf`

## Full extracted content

## Page 5

3. (6.0 points)
CS 61A Software Store
A Store instance has a list of branches, and each branch is also a Store instance, forming a tree of stores.
Each Store instance also has a list of programs (strings) called its inventory. For a Store:
• The copies(s) method returns the number of times s appears in the inventories of all nodes in its tree of
stores.
• The add_to(k) method returns a function that takes a string and appends it to the inventory of its kth
branch. Assume that k is non-negative and less than the number of branches.
class Store:
"""A Store selling programs has branches forming a tree of Stores.
>>> north, south = Store(['Cats', 'Ants']), Store(['Cats', 'Cats', 'Hog'])
>>> east, west = Store(['Cats', 'Hog', 'Hog'], [north, south]), Store(['Cats', 'Cats', 'Ants'])
>>> main = Store(['Ants', 'Ants', 'Hog'], [east, west])
>>> east.copies('Cats')
# 1 in north, 2 in south, 1 in east
>>> main.copies('Ants')
# 2 in main, 1 in north, 1 in west
>>> main.add_to(1)('Ants') # Add 'Ants' to the inventory of west, the branch of main at index 1
>>> [main.copies('Ants'), west.copies('Ants')]
# increased copies in both main and west
[5, 2]
"""
def __init__(self, programs, branches=[]):
assert all([isinstance(b, Store) for b in branches])
self.branches = branches
self.inventory = programs
def copies(self, s):
"""Return the number of times s (string) appears in all inventories of this tree."""
return sum([_______ for p in self.inventory if p == s] + [_______ for b in self.branches])
(a)
(b)
def add_to(self, k):
"""Return a function that appends a string to the inventory of the branch at index k."""
return _______
(c)
(a) (1.0 pt) Fill in blank (a).
# p
# len(p)
# len(self.inventory)
(b) (2.0 pt) Fill in blank (b).
b.copies(s)

## Page 6

(c) (3.0 pt) Fill in blank (c).
self.branches[k].inventory.append


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
- [61a-fa24-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa24-mt2 / P02-PIZZA-BY-THE-SLICE](p02-pizza-by-the-slice.md)
- [61a-fa24-mt2 / P04-ALMOST-A-PERFECT-QUESTION](p04-almost-a-perfect-question.md)
- [61a-fa24-mt2 / P05-HOW-LONG-IS-THIS-EXAM](p05-how-long-is-this-exam.md)
- [61a-fa24-mt2 / P06-NICE-PATH](p06-nice-path.md)
