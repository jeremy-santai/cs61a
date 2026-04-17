---
course: CS61A
term: Fall 2024
assessment: Final
source_pdf: 61a-fa24-final_sol.pdf
exam_slug: 61a-fa24-final
problem_number: 4
problem_title: "Count Misses"
page_range: [6, 9]
points: "13.0 points"
topics: ["oop", "lists", "dictionaries"]
concepts: ["oop", "lists"]
question_types: ["trace", "implementation"]
difficulty: "hard"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 4 — Count Misses

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** oop, lists, dictionaries
- **Concepts:** oop, lists
- **Question types:** trace, implementation
- **Difficulty:** hard
- **Source pages:** 6-9

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: Final
- Source PDF: `61a-fa24-final_sol.pdf`

## Full extracted content

## Page 6

4. (13.0 points)
Count Misses
(a) (6.0 points)
Implement the Counter class. A Counter has a count of the number of times inc has been invoked on
itself or any of its offspring. Its offspring are the Counters created by its spawn method or the spawn
method of any of its offspring.
class Counter:
"""Counts how many times inc has been invoked on itself or any of its offspring.
>>> total = Counter()
>>> odd, even = total.spawn(), total.spawn()
# these are offspring of total
>>> one, three = odd.spawn(), odd.spawn()
# these are offspring of odd and total
>>> for c in [one, even, three, even, odd, even]:
...
c.inc()
>>> [c.count for c in [one, three, even, odd, total]]
[1, 1, 3, 3, 6]
"""
def __init__(self, parent=None):
self.parent = parent
_______
(a)
def inc(self):
self.count += 1
_______:
(b)
_______
(c)
def spawn(self):
return _______
(d)
i. (1.0 pt) Fill in blank (a).
self.count = 0
ii. (1.0 pt) Fill in blank (b).
# if parent is not None:
if self.parent is not None:
# while parent is not None:
# while self.parent is not None:
# for p in parent:
# for p in self.parent:

## Page 7

iii. (2.0 pt) Fill in blank (c).
# p += 1
# p.count += 1
# p.inc()
# p.count.inc()
# parent += 1
# parent.count += 1
# parent.inc()
# parent.count.inc()
# self.parent += 1
# self.parent.count += 1
self.parent.inc()
# self.parent.count.inc()
iv. (2.0 pt) Fill in blank (d).
# self.parent
# self.parent.spawn()
# self.spawn()
# Counter()
# Counter().spawn()
Counter(self)
# Counter(self.count)

## Page 8

(b) (7.0 points)
Implement the MissDict class. A MissDict has a dictionary d. Its get method takes an iterable keys,
returns a list of all values in d that correspond to those keys, and counts the number of keys that did not
appear in d (called misses). Printing a MissDict displays a fraction in which:
• The numerator is the number of misses during all calls to get for that particular MissDict instance.
• The denominator is the number of misses during all calls to get for any MissDict instance.
Assume Counter is implemented correctly.
class MissDict:
"""Has a dict, gets a list of values for an iterable of keys,
and counts the number of keys that are not in the dict.
>>> double = MissDict({1: 2, 2: 4, 3: 6, 5: 10})
>>> half = MissDict({2: 1.0, 3: 1.5, 4: 2.0})
>>> double.get([1, 3, 5, 2, 4])
# No value for key 4 (1 miss)
[2, 6, 10, 4]
>>> double.get([5, 4, 3, 0, 4])
# No value for keys 4 or 0 or 4 (3 misses)
[10, 6]
>>> half.get([1, 3, 5, 2, 4])
# No value for keys 1 or 5 (2 misses)
[1.5, 1.0, 2.0]
>>> print(double)
# double had 4 misses & half had 2 misses
4/6 of the misses
"""
misses = Counter()
def __init__(self, d):
assert isinstance(d, dict)
self.d = d
self.misses = _______
(e)
def get(self, keys):
result = []
for k in keys:
if k in self.d:
_______
(f)
else:
_______
(g)
return result
def __str__(self):
return f'_______ of the misses'
(h)
i. (2.0 pt) Fill in blank (e). Select all correct answers.
2 MissDict.spawn()
■MissDict.misses.spawn()
2 Counter()
2 Counter(MissDict)
■Counter(MissDict.misses)

## Page 9

ii. (2.0 pt) Fill in blank (f).
result.append(self.d[k])
iii. (1.0 pt) Fill in blank (g).
# misses.inc()
# misses.count += 1
self.misses.inc()
# self.misses.count += 1
# MissDict.misses.inc()
# MissDict.misses.count += 1
iv. (2.0 pt) Fill in blank (h).
# {misses.count / MissDict.misses.count}
# {misses.count} / {MissDict.misses.count}
# {misses.count / self.MissDict.misses.count}
# {misses.count} / {self.MissDict.misses.count}
# {self.misses.count / misses.count}
# {self.misses.count} / {misses.count}
# {self.misses.count / MissDict.misses.count}
{self.misses.count} / {MissDict.misses.count}
# {self.misses.count / self.MissDict.misses.count}
# {self.misses.count} / {self.MissDict.misses.count}


---

## Same Semester

- [61a-fa24-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa24-final / P02-LINE-DIAGRAM](p02-line-diagram.md)
- [61a-fa24-final / P03-MAKE-TENS](p03-make-tens.md)
- [61a-fa24-final / P05-PROMOTION-TO-CS-61B](p05-promotion-to-cs-61b.md)
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
