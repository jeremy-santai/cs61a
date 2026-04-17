---
course: CS61A
term: Fall 2025
assessment: Final
source_pdf: 61a-fa25-final_sol.pdf
exam_slug: 61a-fa25-final
problem_number: 8
problem_title: "Students in SQL"
page_range: [21, 22]
points: "6.0 points"
topics: ["sql"]
concepts: ["sql"]
question_types: ["mixed"]
difficulty: "medium"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 8 — Students in SQL

## Semantic summary

- **Summary:** CS61A exam problem with extracted prompt, answers, and supporting context.
- **Topics:** sql
- **Concepts:** sql
- **Question types:** mixed
- **Difficulty:** medium
- **Source pages:** 21-22

## Source

- Course: CS61A
- Term: Fall 2025
- Assessment: Final
- Source PDF: `61a-fa25-final_sol.pdf`

## Visual note

This problem includes visual material on page(s): 21. For exact diagram geometry or pointer placement, consult the source PDF alongside this markdown.

## Full extracted content

## Page 21

8. (6.0 points)
Students in SQL
The students table has one row per student and columns for their name (string), the discussion_id (int)
of their discussion, and a keyword (string) chosen by the student. The keyword was used to place the student
in a discussion with other students who selected the same keyword.
The discussions table has one row per discussion and columns for the discussion’s unique id (int), the ta
(string) who leads the discussion, and the room (string) where the discussion is located.
The first few rows in each table are shown below. Not all rows are shown.
(a) (3.0 points)
Select the most frequently used keyword, and the total number of students with that keyword. Assume
there is one keyword used more than any other (no ties).
SELECT keyword, _______ AS total FROM students _______;
(a)
(b)
i. (1.0 pt) Fill in blank (a).
# 1
# name
COUNT(*)
# MAX(keyword)
# MAX(name)
# MAX(COUNT(*))
ii. (2.0 pt) Fill in blank (b).
# GROUP BY keyword;
# GROUP BY keyword HAVING MAX(COUNT(*));
# GROUP BY keyword HAVING COUNT(*) = MAX(COUNT(*));
# GROUP BY keyword LIMIT MAX(COUNT(*));
# GROUP BY keyword ORDER BY keyword DESC LIMIT 1;
GROUP BY keyword ORDER BY COUNT(*) DESC LIMIT 1;
# AS s1 JOIN students AS s2 ON s1.keyword = s2.keyword LIMIT 1;
# ORDER BY COUNT(*) DESC;
# ORDER BY keyword DESC;
# ORDER BY keyword DESC LIMIT MAX(COUNT(*));
# ORDER BY keyword DESC LIMIT 1;

## Page 22

(b) (3.0 points)
Create a new table big with one row for each discussion that has more than 20 students. The columns
give the ta name and discussion id for each of these discussions.
An example big result is shown on the previous page. The first row indicates that the discussion with ID
1 taught by Rhys has more than 20 students in it (even though only 1 of these students is shown in the
example rows of the students table).
CREATE TABLE big AS
SELECT ta, id FROM students JOIN discussions _______;
(c)
i. (3.0 pt) Fill in blank (c).
ON discussion_id = id GROUP BY id HAVING COUNT(*) > 20
ii. (0.0 pt) Optional: Draw a picture of you experience as a student in CS 61A.
See the other side of this page for the A+ questions.


---

## Same Semester

- [61a-fa25-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa25-final / P02-DO-YOU-COPY](p02-do-you-copy.md)
- [61a-fa25-final / P03-MATH-PLACEMENT-EXAM](p03-math-placement-exam.md)
- [61a-fa25-final / P04-TRIM-THE-TREE](p04-trim-the-tree.md)
- [61a-fa25-final / P05-DOWNLOADS](p05-downloads.md)
- [61a-fa25-final / P06-SCHEME-VS-PYTHON](p06-scheme-vs-python.md)
- [61a-fa25-final / P07-STUDENTS](p07-students.md)
- [61a-fa25-final / P09-FINAL-BOSS](p09-final-boss.md)
- [61a-fa25-mt1 / P01-WHAT-WOULD-PYTHON-DO-OT](../61a-fa25-mt1/p01-what-would-python-do-ot.md)
- [61a-fa25-mt1 / P02-SILKSONG](../61a-fa25-mt1/p02-silksong.md)
- [61a-fa25-mt1 / P03-SAJA-BOYS](../61a-fa25-mt1/p03-saja-boys.md)
- [61a-fa25-mt1 / P04-WE-RE-GOING-UP-UP-UP](../61a-fa25-mt1/p04-we-re-going-up-up-up.md)
