---
course: CS61A
term: Fall 2023
assessment: MT2
exam_slug: 61a-fa23-mt2
problem_number: 3
problem_title: "24-Hour Library"
topics: ["lists", "oop"]
---

# Problem 3 — 24-Hour Library

## Full Extracted Content
## Page 6

3. (6.0 points)
24-Hour Library
Anyone can check out a book from a library and then bring that book back. Implement the Library and
Book classes. A Library takes a list of unique strings called titles and constructs a books dictionary that
has strings as keys and Book objects as values. Its checkout method takes a string title and returns the
corresponding Book object if that title is not checked out, or prints a message. After bring_back is invoked
on that book, it can be checked out again.
class Library:
"""A library with one copy of each title that can be checked out.
>>> cs = Library(['Composing Programs', 'Python Docs', 'Berkeley Academic Guide'])
>>> bs = [cs.checkout('Composing Programs'), cs.checkout('Python Docs')]
>>> cs.checkout('Composing Programs')
# This time, no Book is returned
Composing Programs is checked out
>>> bs[0].bring_back()
>>> cs.checkout('Composing Programs').title
# This time, a Book is returned
'Composing Programs'
"""
def __init__(self, titles):
self.books = {t: Book(t, _______) for t in titles}
(a)
self.out = []
# A list of Book objects
def checkout(self, title):
assert title in self.books, title + " isn't in this library's collection"
book = _______
(b)
if book not in self.out:
_______
(c)
return book
else:
print(book, 'is checked out')
class Book:
def __init__(self, title, library):
self.title = title
# a string
self.library = library
# a Library object
def bring_back(self):
_______.remove(_______)
(d)
(e)
def __str__(self):
return _______
(f)

## Page 7

(a) (1.0 pt) Fill in blank (a).
self
# self.books
# Library
# Library()
# Library(titles)
The book takes a library. The libary that the book is in is the ‘self“ object that is being created with this
dictionary of books.
(b) (1.0 pt) Fill in blank (b).
self.books[title]
Get the relevant book from the dictionary of books.
(c) (1.0 pt) Fill in blank (c).
# out.append(book)
# out.extend(book)
# Library.append(book)
# Library.extend(book)
self.out.append(book)
# self.out.extend(book)
We wish to add the book to the list of checked out books. Append adds an element to a list. (Extend
extends a list with another list.)
(d) (1.0 pt) Fill in blank (d).
# self.
# self.out
# library
# library.out
self.library.out
Remove the book from the list of checked out books.
(e) (1.0 pt) Fill in blank (e).
self
# title
# library
# self.title
# self.library
The name self is bound to the book we’re removing.

## Page 8

(f) (1.0 pt) Fill in blank (f).
# self
# title
self.title
# repr(self)
# repr(title)
# repr(self.title)
One needs to return a string with the title in it. The repr would return a string with quotes in it.


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
- [61a-fa23-mt2 / P04-A-PERFECT-QUESTION](p04-a-perfect-question.md)
- [61a-fa23-mt2 / P05-ONLY-PATHS](p05-only-paths.md)
- [61a-fa23-mt2 / P06-AFTER-PARTY](p06-after-party.md)
