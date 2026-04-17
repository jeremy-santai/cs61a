---
course: CS61A
term: Fall 2025
assessment: Final
source_pdf: 61a-fa25-final_sol.pdf
exam_slug: 61a-fa25-final
problem_number: 7
problem_title: "Students"
page_range: [19, 20]
points: "9.0 points"
topics: ["oop", "lists"]
concepts: ["oop", "lists"]
question_types: ["mixed"]
difficulty: "medium"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 7 — Students

## Semantic summary

- **Summary:** CS61A exam problem with extracted prompt, answers, and supporting context.
- **Topics:** oop, lists
- **Concepts:** oop, lists
- **Question types:** mixed
- **Difficulty:** medium
- **Source pages:** 19-20

## Source

- Course: CS61A
- Term: Fall 2025
- Assessment: Final
- Source PDF: `61a-fa25-final_sol.pdf`

## Full extracted content

## Page 19

7. (9.0 points)
Students
A student has a name (a str) and a discussion group (a DiscGroup instance). Each student is placed into a
discussion group based on a keyword (a str) supplied by the student. When a Student instance is created,
that student is placed into an existing discussion group that has fewer than 6 students and that has the same
keyword that the student supplied. If the student cannot be placed into any existing group, the student will
be placed into a new discussion group. Each discussion group (a DiscGroup instance) has a unique integer id,
starting at 0 for the first discussion group created and counting up, as well as a list of Student instances called
students and a keyword (a str).
class Student():
"""A student has a name and a keyword that is used to place them in a discussion group.
>>> chris = Student("Chris", "kickstart")
>>> pranav = Student("Pranav", "tortilla")
>>> sebastian = Student("Sebastian", "tortilla")
>>> print(chris)
Student Chris is in Disc 0: kickstart (['Chris'])
>>> print(pranav)
Student Pranav is in Disc 1: tortilla (['Pranav', 'Sebastian'])
>>> print(sebastian)
Student Sebastian is in Disc 1: tortilla (['Pranav', 'Sebastian'])
"""
def __init__(self, name, keyword):
"""Initialize the student and place them in a discussion group."""
self.name = name
self.group = _______
(a)
for group in _______:
(b)
if group.keyword == keyword and len(group.students) < 6:
self.group = _______
(c)
if not self.group:
self.group = _______
(d)
_______
(e)
def __str__(self):
return f"Student {self.name} is in {self.group}"
class DiscGroup():
groups = []
# All of the DiscGroup instances
def __init__(self, keyword):
self.students = []
# All of the students in this DiscGroup
self.keyword = keyword
self.id = _______
(f)
_______
(g)
def __str__(self):
return f"Disc {self.id}: {self.keyword} ({[s.name for s in self.students]})"

## Page 20

(a) (1.0 pt) Fill in blank (a).
None
# group
# DiscGroup(keyword)
# DiscGroup(self.keyword)
# DiscGroup(self, keyword)
(b) (1.0 pt) Fill in blank (b).
DiscGroup.groups
(c) (1.0 pt) Fill in blank (c).
# None
group
# DiscGroup(keyword)
# DiscGroup(self.keyword)
# DiscGroup(self, keyword)
(d) (1.0 pt) Fill in blank (d).
# None
# group
DiscGroup(keyword)
# DiscGroup(self.keyword)
# DiscGroup(self, keyword)
(e) (2.0 pt) Fill in blank (e).
self.group.students.append(self)
(f) (1.0 pt) Fill in blank (f).
len(DiscGroup.groups) or len(self.groups)
(g) (2.0 pt) Fill in blank (g).
DiscGroup.groups.append(self) or self.groups.append(self)


---

## Same Semester

- [61a-fa25-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa25-final / P02-DO-YOU-COPY](p02-do-you-copy.md)
- [61a-fa25-final / P03-MATH-PLACEMENT-EXAM](p03-math-placement-exam.md)
- [61a-fa25-final / P04-TRIM-THE-TREE](p04-trim-the-tree.md)
- [61a-fa25-final / P05-DOWNLOADS](p05-downloads.md)
- [61a-fa25-final / P06-SCHEME-VS-PYTHON](p06-scheme-vs-python.md)
- [61a-fa25-final / P08-STUDENTS-IN-SQL](p08-students-in-sql.md)
- [61a-fa25-final / P09-FINAL-BOSS](p09-final-boss.md)
- [61a-fa25-mt1 / P01-WHAT-WOULD-PYTHON-DO-OT](../61a-fa25-mt1/p01-what-would-python-do-ot.md)
- [61a-fa25-mt1 / P02-SILKSONG](../61a-fa25-mt1/p02-silksong.md)
- [61a-fa25-mt1 / P03-SAJA-BOYS](../61a-fa25-mt1/p03-saja-boys.md)
- [61a-fa25-mt1 / P04-WE-RE-GOING-UP-UP-UP](../61a-fa25-mt1/p04-we-re-going-up-up-up.md)
