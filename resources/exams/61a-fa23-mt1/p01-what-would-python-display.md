---
course: CS61A
term: Fall 2023
assessment: MT1
exam_slug: 61a-fa23-mt1
problem_number: 1
problem_title: "What Would Python Display?"
topics: ["environment-diagrams", "higher-order-functions"]
---

# Problem 1 — What Would Python Display?

## Full Extracted Content
## Page 3

1. (6.0 points)
What Would Python Display?
Assume the following code has been executed already.
cat = 3
def dog():
return cat
def hog():
cat = 4
print(cat, dog())
cat = 5
For each expression below, write the output displayed by the interactive Python interpreter when the
expression is evaluated. The output may have multiple lines. If an error occurs, write “Error”, but include all
output displayed before the error. To display a function value, write “Function”.
(a) (1.0 pt) dog(cat)
# 3
# 4
# 5
# Function
Error
The function dog is defined to take no arguments, but this call expression passes an argument.
(b) (1.0 pt) dog()
# 3
# 4
# Function
# Error
The name cat is in the global frame. It is assigned to 5, which overwrites the assignment to 3.
Some might answer 3, as cat is initially bound to 3. But since dog() is being called after cat is bound to
5 and the body of dog is only evaluated when the function is called, it will return 5.
(c) (2.0 pt) print((lambda dog: print(dog()))(lambda: 6))
None
The entire expression is a call expression. The first lambda expression defines a function with an argument
named dog and prints the result of calling dog with no arguments. That function is then called on a
function defined by the second lambda which takes no arguments and always returns 6.
Thus, the result of calling the function lambda: 6 is printed.

## Page 4

(d) (2.0 pt) hog()
4 5
Two values are passed to print, the value of cat which appears in the local frame and is 4, as well
as the result of calling dog() which is 5.
A key thing to note is that the environment of the call to dog() does not include the frame from the call to
hog().


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
- [61a-fa23-mt1 / P02-AN-ODD-IMPLEMENTATION-OF-EVEN](p02-an-odd-implementation-of-even.md)
- [61a-fa23-mt1 / P03-IN-YOUR-PRIME](p03-in-your-prime.md)
- [61a-fa23-mt1 / P04-CHOOSE-WISELY](p04-choose-wisely.md)
- [61a-fa23-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa23-mt2/p01-what-would-python-display.md)
- [61a-fa23-mt2 / P02-MAKING-A-LIST-CHECKING-IT-TWICE](../61a-fa23-mt2/p02-making-a-list-checking-it-twice.md)
- [61a-fa23-mt2 / P03-24-HOUR-LIBRARY](../61a-fa23-mt2/p03-24-hour-library.md)
- [61a-fa23-mt2 / P04-A-PERFECT-QUESTION](../61a-fa23-mt2/p04-a-perfect-question.md)
- [61a-fa23-mt2 / P05-ONLY-PATHS](../61a-fa23-mt2/p05-only-paths.md)
- [61a-fa23-mt2 / P06-AFTER-PARTY](../61a-fa23-mt2/p06-after-party.md)
