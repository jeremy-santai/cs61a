---
course: CS61A
term: Fall 2025
assessment: Final
source_pdf: 61a-fa25-final_sol.pdf
exam_slug: 61a-fa25-final
problem_number: 5
problem_title: "Downloads"
page_range: [15, 15]
points: "4.0 points"
topics: ["oop", "lists"]
concepts: ["oop", "lists"]
question_types: ["implementation"]
difficulty: "easy"
santai_chunk_type: "exam_problem"
conversion: "pdf_to_markdown"
fidelity: "high"
---

# Problem 5 — Downloads

## Semantic summary

- **Summary:** Implementation problem centered on core CS61A abstraction patterns and recursive or iterative reasoning.
- **Topics:** oop, lists
- **Concepts:** oop, lists
- **Question types:** implementation
- **Difficulty:** easy
- **Source pages:** 15-15

## Source

- Course: CS61A
- Term: Fall 2025
- Assessment: Final
- Source PDF: `61a-fa25-final_sol.pdf`

## Full extracted content

## Page 15

5. (4.0 points)
Downloads
The coroutine function download fetches a file with the given name. Its implementation is not shown.
async def download(filename: str):
...
class Downloader():
def __init__(self, filenames):
self.filenames = filenames
self.current_index = 0
async def download_files(self):
while self.current_index < len(self.filenames):
filename = self.filenames[self.current_index]
self.current_index += 1
await download(filename)
async def download_all(self):
await asyncio.gather(self.download_files(), self.download_files())
d = Downloader(["a", "b", "c", "d"])
asyncio.run(d.download_all())
(a) (3.0 pt) The code above initializes a Downloader with a list of 4 files ["a", "b", "c", "d"]. Which of
the following statements are true? Select all that apply.
■The function download will be called exactly 4 times.
2 The function download may be called more than 4 times.
2 The function download may be called fewer than 4 times.
■The function download will be called on each file exactly once.
2 The function download may not be called on all of the files.
2 The function download may be called more than once on the same file.
2 The code above may error because the index self.current_index is out of range.
(b) (1.0 pt) Assume that the function download takes one second to run, and spends all of that time waiting
for the file to be downloaded. During that wait time, it gives up control so that other coroutines can run.
How many seconds does the code above take to run?
2 seconds


---

## Same Semester

- [61a-fa25-final / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa25-final / P02-DO-YOU-COPY](p02-do-you-copy.md)
- [61a-fa25-final / P03-MATH-PLACEMENT-EXAM](p03-math-placement-exam.md)
- [61a-fa25-final / P04-TRIM-THE-TREE](p04-trim-the-tree.md)
- [61a-fa25-final / P06-SCHEME-VS-PYTHON](p06-scheme-vs-python.md)
- [61a-fa25-final / P07-STUDENTS](p07-students.md)
- [61a-fa25-final / P08-STUDENTS-IN-SQL](p08-students-in-sql.md)
- [61a-fa25-final / P09-FINAL-BOSS](p09-final-boss.md)
- [61a-fa25-mt1 / P01-WHAT-WOULD-PYTHON-DO-OT](../61a-fa25-mt1/p01-what-would-python-do-ot.md)
- [61a-fa25-mt1 / P02-SILKSONG](../61a-fa25-mt1/p02-silksong.md)
- [61a-fa25-mt1 / P03-SAJA-BOYS](../61a-fa25-mt1/p03-saja-boys.md)
- [61a-fa25-mt1 / P04-WE-RE-GOING-UP-UP-UP](../61a-fa25-mt1/p04-we-re-going-up-up-up.md)
