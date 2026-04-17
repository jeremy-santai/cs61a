---
course: CS61A
term: Fall 2024
assessment: Final
source_pdf: 61a-fa24-final_sol.pdf
exam_slug: 61a-fa24-final
problem_number: 8
problem_title: "Arcane Jobs"
page_range: [20, 21]
points: "5.0 points"
topics: ["lists"]
concepts: ["lists"]
question_types: ["mixed"]
difficulty: "easy"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 8 — Arcane Jobs

## Semantic summary

- **Summary:** CS61A exam problem with extracted prompt, answers, and supporting context.
- **Topics:** lists
- **Concepts:** lists
- **Question types:** mixed
- **Difficulty:** easy
- **Source pages:** 20-21

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: Final
- Source PDF: `61a-fa24-final_sol.pdf`

## Visual note

This problem includes visual material on page(s): 20. For exact diagram geometry or pointer placement, consult the source PDF alongside this markdown.

## Full extracted content

## Page 20

8. (5.0 points)
Arcane Jobs
The Council of Piltover wants a list of all the people living in regions it governs that have unique jobs. Create a
table with columns labeled name and job that contains one row for each person living in a region governed by
the "council" who is the only person with their job among everybody living in regions ruled by the council.
The who table has one row per person and columns for their name (string; each row has a unique value), the
region (string) they live in, and their job (string). The gov table has one row per region and columns for
its name called place (string; each row has a unique value) and the group that rules over it called ruler
(string).
Here’s an example of the contents of the who and gov tables and the expected result for a query based on these.
SELECT name, job FROM _______ WHERE _______ AND ruler = "council" _______ ;
(a)
(b)
(c)
(a) (1.0 pt) Fill in blank (a).
# who
# who AS a, who AS b
who, gov
# who AS a, who AS b, gov
(b) (2.0 pt) Fill in blank (b).
# COUNT(*) = 1
# place = "council"
# a.job = b.job
# a.job != b.job
region = place
# a.region = place
# a.region = b.region AND a.region = place
# a.job = b.job AND a.region = place

## Page 21

(c) (2.0 pt) Fill in blank (c). You may write AND to continue the WHERE clause (but you don’t have to). You
may also include other clauses such as GROUP BY, ORDER BY, HAVING, and LIMIT (but you don’t have to).
GROUP BY job HAVING COUNT(*) = 1


---

## Same Semester

- [61a-fa24-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa24-final / P02-LINE-DIAGRAM](p02-line-diagram.md)
- [61a-fa24-final / P03-MAKE-TENS](p03-make-tens.md)
- [61a-fa24-final / P04-COUNT-MISSES](p04-count-misses.md)
- [61a-fa24-final / P05-PROMOTION-TO-CS-61B](p05-promotion-to-cs-61b.md)
- [61a-fa24-final / P06-FRESH-PRODUCE](p06-fresh-produce.md)
- [61a-fa24-final / P07-A-PAIR-OF-SCHEMES](p07-a-pair-of-schemes.md)
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
