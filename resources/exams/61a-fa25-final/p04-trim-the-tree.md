---
course: CS61A
term: Fall 2025
assessment: Final
source_pdf: 61a-fa25-final_sol.pdf
exam_slug: 61a-fa25-final
problem_number: 4
problem_title: "Trim the Tree"
page_range: [12, 14]
points: "10.0 points"
topics: ["trees", "oop", "lists", "dictionaries"]
concepts: ["trees", "oop", "lists"]
question_types: ["implementation", "mutation"]
difficulty: "medium"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 4 — Trim the Tree

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** trees, oop, lists, dictionaries
- **Concepts:** trees, oop, lists
- **Question types:** implementation, mutation
- **Difficulty:** medium
- **Source pages:** 12-14

## Source

- Course: CS61A
- Term: Fall 2025
- Assessment: Final
- Source PDF: `61a-fa25-final_sol.pdf`

## Full extracted content

## Page 12

4. (10.0 points)
Trim the Tree
(a) (5.0 points)
Implement sums, which takes a Tree of integers t. It returns a dictionary in which each node of t is a key
and the corresponding value is the sum of the labels of the tree rooted at that node.
The Tree class appears on the left side of Page 2 of the Midterm 2 study guide.
def sums(t):
"""Return a dictionary from nodes to their label sums.
>>> t = Tree(2, [Tree(4, [Tree(5)]), Tree(3), Tree(5, [Tree(6), Tree(7)])])
>>> d = sums(t)
>>> nodes = [t, t.branches[0], t.branches[0].branches[0], t.branches[2]]
>>> [d[n] for n in nodes]
[32, 9, 5, 18]
"""
result = {}
def insert(t):
for b in t.branches:
_______
(a)
result[t] = _______
(b)
insert(t)
return result
i. (2.0 pt) Fill in blank (a).
insert(b)
# sums(b)
# result += sums(b)
# result[b] = insert(b)
# result[b] += insert(b)
# result[t] += insert(b)
# result[t] += result[b]
# result[b] = sums(t)
# result[b] += sums(t)
ii. (3.0 pt) Fill in blank (b).
t.label + sum([result[b] for b in t.branches])

## Page 13

(b) (5.0 points)
Implement one_cut, which takes a Tree of integers t and a number n. It returns a new tree that has the
same labels and structure as t but with one sub-tree excluded. In other words, the returned tree looks
like t with a non-root node and its descendents removed. Exclude the non-root node that makes the sum
of the remaining labels of the tree as close to n as possible (in absolute value). Do not mutate t. Assume t
has at least 2 nodes.
def one_cut(t, n):
"""Return a tree like t but omit a node so that the sum of remaining labels is close to n.
>>> t = Tree(2, [Tree(4, [Tree(5)]), Tree(3), Tree(5, [Tree(6), Tree(7)])])
# sums to 32
>>> one_cut(t, 30)
# cuts just the 3 to get 29
Tree(2, [Tree(4, [Tree(5)]), Tree(5, [Tree(6), Tree(7)])])
>>> one_cut(t, 26)
# cuts just the 6 to get 26
Tree(2, [Tree(4, [Tree(5)]), Tree(3), Tree(5, [Tree(7)])])
>>> one_cut(t, 15)
# cuts the 5 node with 6 and 7 below it to get 14
Tree(2, [Tree(4, [Tree(5)]), Tree(3)])
>>> one_cut(t, 1)
# 14 is the smallest possible sum after one cut
Tree(2, [Tree(4, [Tree(5)]), Tree(3)])
"""
d = sums(t)
total = d.pop(t) # remove the root node from the dictionary; total is the sum of its labels
target = min(d.keys(), key=lambda node: _______)
(c)
def cut(t):
_______
(d)
_______
(e)
i. (2.0 pt) Fill in blank (c).
abs(n - (total - d[node]))
ii. (2.0 pt) Fill in blank (d).
# t.branches.remove(target)
# t.branches = [b for b in t.branches if b is not target]
# t.branches = [cut(b) for b in t.branches if b is not target]
# t = Tree(t.label, [b for b in t.branches if b is not target])
# t = Tree(t.label, [cut(b) for b in t.branches if b is not target])
# return Tree(t.label, [b for b in t.branches if b is not target])
return Tree(t.label, [cut(b) for b in t.branches if b is not target])

## Page 14

iii. (1.0 pt) Fill in blank (e).
# return t
return cut(t)
# return Tree(t.label, list(map(cut, t.branches)))
# return [cut(t), t][1]


---

## Same Semester

- [61a-fa25-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa25-final / P02-DO-YOU-COPY](p02-do-you-copy.md)
- [61a-fa25-final / P03-MATH-PLACEMENT-EXAM](p03-math-placement-exam.md)
- [61a-fa25-final / P05-DOWNLOADS](p05-downloads.md)
- [61a-fa25-final / P06-SCHEME-VS-PYTHON](p06-scheme-vs-python.md)
- [61a-fa25-final / P07-STUDENTS](p07-students.md)
- [61a-fa25-final / P08-STUDENTS-IN-SQL](p08-students-in-sql.md)
- [61a-fa25-final / P09-FINAL-BOSS](p09-final-boss.md)
- [61a-fa25-mt1 / P01-WHAT-WOULD-PYTHON-DO-OT](../61a-fa25-mt1/p01-what-would-python-do-ot.md)
- [61a-fa25-mt1 / P02-SILKSONG](../61a-fa25-mt1/p02-silksong.md)
- [61a-fa25-mt1 / P03-SAJA-BOYS](../61a-fa25-mt1/p03-saja-boys.md)
- [61a-fa25-mt1 / P04-WE-RE-GOING-UP-UP-UP](../61a-fa25-mt1/p04-we-re-going-up-up-up.md)
