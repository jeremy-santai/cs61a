---
course: CS61A
term: Fall 2023
assessment: MT2
exam_slug: 61a-fa23-mt2
problem_number: 5
problem_title: "Only Paths"
topics: ["higher-order-functions", "lists", "trees", "oop"]
---

# Problem 5 — Only Paths

## Full Extracted Content
## Page 13

5. (7.0 points)
Only Paths
Implement only_paths, which takes a Tree of numbers t and a number n. It returns a new Tree with only the
nodes of t on a path from the root to a leaf with labels that sum to n, or None if no path sums to n. Do not
mutate t.
The Tree class appears on the midterm 2 study guide. Here is an illustration of the doctest examples involving
t.
def only_paths(t, n):
"""Return a Tree with only the nodes of t along paths from the root to a leaf of t
for which the node labels of the path sum to n. If no paths sum to n, return None.
>>> print(only_paths(Tree(5, [Tree(2), Tree(1, [Tree(2)]), Tree(1, [Tree(1)])]), 7))
>>> t = Tree(3, [Tree(4), Tree(1, [Tree(3, [Tree(2)]), Tree(2, [Tree(1)]), Tree(5), Tree(3)])])
>>> print(only_paths(t, 7))
>>> print(only_paths(t, 9))
>>> print(only_paths(t, 3))
None
"""
if _______:
(a)
return t
new_branches = [_______ for b in t.branches]
(b)
if _______(new_branches):
(c)
return Tree(t.label, [b for b in new_branches if _______])
(d)

## Page 14

(a) (2.0 pt) Fill in blank (a).
t.is_leaf() and n == t.label
This is a tree with a path to a leaf with sum of labels being n as specified.
And no recursive call
is needed.
(b) (3.0 pt) Fill in blank (b).
only_paths(b, n - t.label)
The sum of labels along a path to any leaf is the sum in a branch plus the label. Thus, we wish to
find a solution for each branch with sum n-t.label.
(c) (1.0 pt) Fill in blank (c).
# all
any
# has
# only_paths
The function returns None if a branch has no valid path. Thus, if all the entries of the list of solutions for
branches are None, the procedure is done. Otherwise it should return a tree.
(d) (1.0 pt) Fill in blank (d).
# only_paths(b, n)
# b.label == n
# b.label != n
# b is None
b is not None
Only keep the results that are trees, not None.

## Page 15

(e) This A+ question is not worth any points. It can only affect your course grade if you have a
high A and might receive an A+. Finish the rest of the exam first! Fill in the blank to implement
only_long_paths, which takes a Tree of numbers t and a number n. It returns a new Tree containing
only the nodes of t that lie on a path from the root to a leaf for which the sum of the labels plus the
length of the path is n. Do not mutate t. You may not write and, or, if, [ or ]. Assume only_paths
is implemented correctly.
only_paths = _____________
def only_long_paths(t, n):
"""Return a Tree with only the nodes of t along paths from the root to a leaf of t
for which the sum of node labels plus the length of the path is n.
>>> example = Tree(5, [Tree(3), Tree(1, [Tree(2)]), Tree(1, [Tree(1)])])
>>> only_long_paths(example, 10)
# Result has paths 5-3 (length 2) and 5-1-1 (length 3)
Tree(5, [Tree(3), Tree(1, [Tree(1)])])
"""
return only_paths(t, n)
(lambda f: lambda t, n: f(t, n-1))(only_paths)
Like memo from lecture, this lambda function takes a function and returns a similar function.
This
similar function calls the original only_paths on n-1 rather than n to account for the length of the path.


---

## Same Semester

- [61a-fa23-final / P01-COPYING-COPIES](../61a-fa23-final/p01-copying-copies.md)
- [61a-fa23-final / P02-PATH-MATH](../61a-fa23-final/p02-path-math.md)
- [61a-fa23-final / P03-TALK-LIKE-A-PIRATE-DAY](../61a-fa23-final/p03-talk-like-a-pirate-day.md)
- [61a-fa23-final / P04-SIX-PAGES-OF-PAIRINGS-SO-PLEASE-READ-THE-DEFINITION-CAREFULLY](../61a-fa23-final/p04-six-pages-of-pairings-so-please-read-the-definition-carefully.md)
- [61a-fa23-final / P05-WHAT-WOULD-SCHEME-DO](../61a-fa23-final/p05-what-would-scheme-do.md)
- [61a-fa23-final / P06-HOW-TO-GET-PROMOTED](../61a-fa23-final/p06-how-to-get-promoted.md)
- [61a-fa23-final / P07-DON-T-SKIP-THIS](../61a-fa23-final/p07-don-t-skip-this.md)
- [61a-fa23-final / P08-CHEAP-DONUTS](../61a-fa23-final/p08-cheap-donuts.md)
- [61a-fa23-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa23-mt1/p01-what-would-python-display.md)
- [61a-fa23-mt1 / P02-AN-ODD-IMPLEMENTATION-OF-EVEN](../61a-fa23-mt1/p02-an-odd-implementation-of-even.md)
- [61a-fa23-mt1 / P03-IN-YOUR-PRIME](../61a-fa23-mt1/p03-in-your-prime.md)
- [61a-fa23-mt1 / P04-CHOOSE-WISELY](../61a-fa23-mt1/p04-choose-wisely.md)
- [61a-fa23-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa23-mt2 / P02-MAKING-A-LIST-CHECKING-IT-TWICE](p02-making-a-list-checking-it-twice.md)
- [61a-fa23-mt2 / P03-24-HOUR-LIBRARY](p03-24-hour-library.md)
- [61a-fa23-mt2 / P04-A-PERFECT-QUESTION](p04-a-perfect-question.md)
- [61a-fa23-mt2 / P06-AFTER-PARTY](p06-after-party.md)
