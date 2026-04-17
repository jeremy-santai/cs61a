---
course: CS61A
term: Fall 2025
assessment: Final
source_pdf: 61a-fa25-final_sol.pdf
exam_slug: 61a-fa25-final
problem_number: 9
problem_title: "Final Boss"
page_range: [23, 25]
points: "0.0 points"
topics: ["scheme", "trees", "lists"]
concepts: ["scheme", "trees", "lists"]
question_types: ["implementation", "mutation"]
difficulty: "easy"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 9 — Final Boss

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** scheme, trees, lists
- **Concepts:** scheme, trees, lists
- **Question types:** implementation, mutation
- **Difficulty:** easy
- **Source pages:** 23-25

## Source

- Course: CS61A
- Term: Fall 2025
- Assessment: Final
- Source PDF: `61a-fa25-final_sol.pdf`

## Full extracted content

## Page 23

9. (0.0 points)
Final Boss
These two A+ questions are not worth any points. They can only affect your course grade if you
have a high A and might receive an A+. Finish the rest of the exam first! If your answers are long, write
on multiple lines.
(a) (0.0 pt) Definition. An infix expression is a list that begins and ends with an integer and alternates
between integers and operators, where each operator is either + or -. For example, (7 + 2 - 1 + 3 - 6
+ 8 - 1 + 4).
Fill in the blank to implement preorder, which takes an infix expression expr and returns a call to + on
all of the integers from expr. Each subtracted number in expr should appear within a one-argument call
to -.
;;; Convert an infix expression to a valid Scheme expression with the same value.
;;; scm> (preorder '(7 + 2 - 1 + 3 - 6 + 8 - 1 + 4))
;;; (+ 7 2 (- 1) 3 (- 6) 8 (- 1) 4)
;;; scm> (preorder '(-7 - -1 - 2 - -3))
;;; (+ -7 (- -1) (- 2) (- -3))
(define (preorder expr)
(define (rest expr f)
(define (helper s)
(cond ((null? s) nil)
((eq? (car s) '+) (helper (cdr s)))
((eq? (car s) '-) (f helper s))
(else
(cons (car s) (helper (cdr s))))))
(helper expr))
_______ )
(cons '+ (rest expr (lambda (h s) (cons (list '- (car (cdr s))) (h (cdr
(cdr s)))))))

## Page 24

(b) (0.0 pt) Implement two_cut, which takes a Tree of positive integers t with at least 3 nodes and an
integer n. It returns a new tree like t but with 2 non-root nodes (and their descendents) removed. It’s ok
if one of the removed nodes is a descendent of the other. Remove the two non-root nodes that change the
label sum of the tree to be as close to n as possible (in absolute value). Do not mutate t. You may call
one_cut from 4(b) but not sums.
def g(t):
return t.label + sum([g(b) for b in t.branches])
def two_cut(t, n):
"""Return a tree like t but omit 2 nodes so that the sum of remaining labels is close to n.
>>> t = Tree(2, [Tree(4, [Tree(5)]), Tree(3, [Tree(1)]), Tree(5, [Tree(6), Tree(7)])])
>>> two_cut(t, 30)
# cut 1 and then 3; result sums to 29
Tree(2, [Tree(4, [Tree(5)]), Tree(5, [Tree(6), Tree(7)])])
>>> two_cut(t, 12)
# cut 3 and then 5; result sums to 11
Tree(2, [Tree(4, [Tree(5)])])
>>> two_cut(t, 6)
# cut 4 and then 5; result sums to 6
Tree(2, [Tree(3, [Tree(1)])])
"""
return _______
min([one_cut(one_cut(t, k), n) for k in range(g(t))], key=lambda t: abs(n -
g(t)))

## Page 25

No more questions.


---

## Same Semester

- [61a-fa25-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa25-final / P02-DO-YOU-COPY](p02-do-you-copy.md)
- [61a-fa25-final / P03-MATH-PLACEMENT-EXAM](p03-math-placement-exam.md)
- [61a-fa25-final / P04-TRIM-THE-TREE](p04-trim-the-tree.md)
- [61a-fa25-final / P05-DOWNLOADS](p05-downloads.md)
- [61a-fa25-final / P06-SCHEME-VS-PYTHON](p06-scheme-vs-python.md)
- [61a-fa25-final / P07-STUDENTS](p07-students.md)
- [61a-fa25-final / P08-STUDENTS-IN-SQL](p08-students-in-sql.md)
- [61a-fa25-mt1 / P01-WHAT-WOULD-PYTHON-DO-OT](../61a-fa25-mt1/p01-what-would-python-do-ot.md)
- [61a-fa25-mt1 / P02-SILKSONG](../61a-fa25-mt1/p02-silksong.md)
- [61a-fa25-mt1 / P03-SAJA-BOYS](../61a-fa25-mt1/p03-saja-boys.md)
- [61a-fa25-mt1 / P04-WE-RE-GOING-UP-UP-UP](../61a-fa25-mt1/p04-we-re-going-up-up-up.md)
