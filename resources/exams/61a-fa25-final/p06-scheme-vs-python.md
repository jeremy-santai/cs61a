---
course: CS61A
term: Fall 2025
assessment: Final
source_pdf: 61a-fa25-final_sol.pdf
exam_slug: 61a-fa25-final
problem_number: 6
problem_title: "Scheme VS Python"
page_range: [16, 18]
points: "15.0 points"
topics: ["scheme", "linked-lists", "oop", "lists"]
concepts: ["scheme", "linked-lists", "oop", "lists"]
question_types: ["implementation"]
difficulty: "hard"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 6 — Scheme VS Python

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** scheme, linked-lists, oop, lists
- **Concepts:** scheme, linked-lists, oop, lists
- **Question types:** implementation
- **Difficulty:** hard
- **Source pages:** 16-18

## Source

- Course: CS61A
- Term: Fall 2025
- Assessment: Final
- Source PDF: `61a-fa25-final_sol.pdf`

## Full extracted content

## Page 16

6. (15.0 points)
Scheme VS Python
(a) (5.0 points)
Implement match, which takes a linked list of numbers s (a Link instance or Link.empty) and a positive
integer k. It returns the number of pairs of equal elements that are k positions apart in s. Hint: You
may use multiple assignment in your solution: ___ , ___ = ___ , ___
The Link class appears on the left side of Page 2 of the Midterm 2 study guide.
def match(s, k):
"""Return how many pairs of values in linked list s that are k positions apart are equal.
>>> nums = Link(3, Link(1, Link(4, Link(1, Link(5, Link(2, Link(5, Link(3, Link(5)))))))))
>>> match(nums, 2)
# 1 and 1; 5 and 5; 5 and 5
>>> {k: match(nums, k) for k in range(1, 8)}
# k=4: 5 and 5; k=7: 3 and 3
{1: 0, 2: 3, 3: 0, 4: 1, 5: 0, 6: 0, 7: 1}
"""
t, count = s, 0
_______:
(a)
if t is not Link.empty:
_______
(b)
while t is not Link.empty:
if _______:
(c)
count += 1
_______
(d)
return count
i. (1.0 pt) Fill in blank (a).
# def f(t)
# if s is not Link.empty
# while s is not Link.empty
for x in range(k)
ii. (1.0 pt) Fill in blank (b).
t = t.rest
iii. (1.0 pt) Fill in blank (c).
s.first == t.first
iv. (2.0 pt) Fill in blank (d).
s, t = s.rest, t.rest

## Page 17

(b) (5.0 points)
Implement zip-map, a Scheme procedure that takes a two-argument procedure f and lists s and t. It
returns a list containing the results of calling f on pairs of values from s and t that appear in the same
position (index) within s and t. For example, the first value in the returned list is the return value of
calling f on the first value in s and the first value in t. The length of the returned list is the minimum of
the length of s and the length of t.
;;; Return a list of results from calling f on pairs of co-indexed values from s and t
;;;
;;; scm> (zip-map + '(10 30 20 40) '(5 6 7))
;;; (15 36 27)
;;; scm> (zip-map list '(10 30 20 40) '(9 8 7 6 5 4))
;;; ((10 9) (30 8) (20 7) (40 6))
(define (zip-map f s t)
(if (or (null? s) (null? t)) nil
(_______ _______ _______)))
(e)
(f)
(g)
i. (1.0 pt) Fill in blank (e).
cons
# list
# append
# zip-map
ii. (2.0 pt) Fill in blank (f).
# (car s)
# (car t)
# (cons (car s) (car t))
# (list (car s) (car t))
# (f (cons (car s) (car t)))
# (f (list (car s) (car t)))
(f (car s) (car t))
# (apply f (car s) (car t))
iii. (2.0 pt) Fill in blank (g).
(zip-map f (cdr s) (cdr t))

## Page 18

(c) (5.0 points)
Implement match, a Scheme procedure that takes a list of numbers s and a positive integer k. It returns
the number of pairs of equal elements that are k positions apart in s. You may call advance and zip-map.
;;; Return the elements of list s starting at index k
(define (advance s k) (if (or (zero? k) (null? s)) s (advance (cdr s) (- k 1))))
;;; Return how many pairs of values in list s which are k positions apart are equal
;;; scm> (define nums '(3 1 4 1 5 2 5 3 5))
;;; nums
;;; scm> (match nums 2)
;;; 3
;;; scm> (map (lambda (k) (list k ': (match nums k))) '(1 2 3 4 5 6 7))
;;; ((1 : 0) (2 : 3) (3 : 0) (4 : 1) (5 : 0) (6 : 0) (7 : 1))
(define (match s k)
(_______ (_______ (lambda (a b) _______ ) s _______ )))
(h)
(i)
(j)
(k)
i. (1.0 pt) Fill in blank (h).
# +
# sum
# len
# cons '+
apply +
ii. (1.0 pt) Fill in blank (i).
# advance
zip-map
# map
# filter
# apply
iii. (2.0 pt) Fill in blank (j). Hint: Write an expression that evaluates to a number.
(if (= a b) 1 0)
iv. (1.0 pt) Fill in blank (k).
# s
# k
# (cdr s)
(advance s k)


---

## Same Semester

- [61a-fa25-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa25-final / P02-DO-YOU-COPY](p02-do-you-copy.md)
- [61a-fa25-final / P03-MATH-PLACEMENT-EXAM](p03-math-placement-exam.md)
- [61a-fa25-final / P04-TRIM-THE-TREE](p04-trim-the-tree.md)
- [61a-fa25-final / P05-DOWNLOADS](p05-downloads.md)
- [61a-fa25-final / P07-STUDENTS](p07-students.md)
- [61a-fa25-final / P08-STUDENTS-IN-SQL](p08-students-in-sql.md)
- [61a-fa25-final / P09-FINAL-BOSS](p09-final-boss.md)
- [61a-fa25-mt1 / P01-WHAT-WOULD-PYTHON-DO-OT](../61a-fa25-mt1/p01-what-would-python-do-ot.md)
- [61a-fa25-mt1 / P02-SILKSONG](../61a-fa25-mt1/p02-silksong.md)
- [61a-fa25-mt1 / P03-SAJA-BOYS](../61a-fa25-mt1/p03-saja-boys.md)
- [61a-fa25-mt1 / P04-WE-RE-GOING-UP-UP-UP](../61a-fa25-mt1/p04-we-re-going-up-up-up.md)
