---
course: CS61A
term: Fall 2024
assessment: Final
source_pdf: 61a-fa24-final_sol.pdf
exam_slug: 61a-fa24-final
problem_number: 9
problem_title: "Ape Pull Us"
page_range: [22, 24]
points: "0.0 points"
topics: ["generators", "lists"]
concepts: ["generators", "lists"]
question_types: ["implementation", "predicate"]
difficulty: "easy"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 9 — Ape Pull Us

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** generators, lists
- **Concepts:** generators, lists
- **Question types:** implementation, predicate
- **Difficulty:** easy
- **Source pages:** 22-24

## Source

- Course: CS61A
- Term: Fall 2024
- Assessment: Final
- Source PDF: `61a-fa24-final_sol.pdf`

## Full extracted content

## Page 22

9. (0.0 points)
Ape Pull Us
These two A+ questions are not worth any points. They can only affect your course grade if you
have a high A and might receive an A+. Finish the rest of the exam first!
(a)
Implement all-next, a macro that takes an expression x-expr and a list of numbers. It returns #t if
every element in s besides the first is equal to the value of x-expr when x is bound to the previous element
in s. It returns #f otherwise. Assume x-expr does not contain the symbol y.
You may call all-pairs from Q6. Important: The template has a quasiquote before the blank.
;;; Return whether every value in s that follows another value x is equal
;;; to the x-expr evaluated when x is the previous value.
;;;
;;; scm> (all-next (+ x 2) '(3 5 7 9 11 13))
;;; #t
;;; scm> (all-next (* x 2) '(2 4 8 16 32 64))
;;; #t
;;; scm> (all-next (+ x 2) '(3 5 7 8 11 13))
;;; #f
;;; scm> (all-next (+ x 4) '(3 5 7 9 11 13))
;;; #f
(define-macro (all-next x-expr s) ` _______ )
(all-pairs (lambda (x y) (= ,x-expr y)) ,s)

## Page 23

(b)
Implement make_tens by filling in the blank in repromote. The make_tens function takes a list of
numbers s. It returns a list t of the same elements reordered so that tens(t) returns True. Return an
order that requires the fewest promotions to reorder s into t. You may use tens from Q2 and promote
from Q4.
def make_tens(s):
"""Return a list t for which tens(t) is true and promotions(s, t) is as small as possible.
If there is no reordering t of s for which tens(t) is true, return None.
>>> make_tens([4, 2, 2, 2, 4, 6, 1, 3, 3, 2, 5]) # promote (6, 7), (7, 9), and (8, 10)
[4, 2, 2, 2, 4, 6, 3, 2, 5, 1, 3]
>>> make_tens([4, 2, 2, 2, 4, 5, 1, 4, 3, 4]) # promote (2, 4), (4, 7), (5, 9), and (8, 9)
[4, 2, 4, 2, 4, 4, 2, 5, 3, 1]
"""
for t in promute(s):
if tens(t):
return t
def promute(s):
for k in range(len(s)):
yield from repromote(s, k)
def repromote(s, k):
if k == 0:
yield s
elif len(s) > 1:
for j in range(len(s)):
for rest in _______:
yield [s[j]] + rest
repromote(s[:j] + s[j+1:], k - min(1, j))

## Page 24

No more questions.


---

## Same Semester

- [61a-fa24-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa24-final / P02-LINE-DIAGRAM](p02-line-diagram.md)
- [61a-fa24-final / P03-MAKE-TENS](p03-make-tens.md)
- [61a-fa24-final / P04-COUNT-MISSES](p04-count-misses.md)
- [61a-fa24-final / P05-PROMOTION-TO-CS-61B](p05-promotion-to-cs-61b.md)
- [61a-fa24-final / P06-FRESH-PRODUCE](p06-fresh-produce.md)
- [61a-fa24-final / P07-A-PAIR-OF-SCHEMES](p07-a-pair-of-schemes.md)
- [61a-fa24-final / P08-ARCANE-JOBS](p08-arcane-jobs.md)
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
