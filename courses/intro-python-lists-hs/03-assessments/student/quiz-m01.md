---
course: intro-python-lists-hs
stage: 03-assessments/student
module: 01
author: assessment-designer
date: 2026-11-08
outcomes: LO-1, LO-2, LO-3, LO-4, LO-5
---

# Quiz: build playlist.py

Answer every question. Multiple choice questions have one correct answer unless stated.
An index is a position in a list, counted from 0. A method is a function called with a dot.

The running case is the class playlist in `playlist.py`. It starts as four song titles:

```python
songs = ["Sunrise Walk", "Blue Window", "Paper Planes", "Night Bus"]
```

## Question 1

<!-- item: Q1 | outcome: LO-2 | difficulty: basic -->

In `playlist.py`, which expression is the first song, Sunrise Walk?

A. `songs[1]`
B. `songs[0]`
C. `songs[4]`
D. `songs(0)`

## Question 2

<!-- item: Q2 | outcome: LO-2 | difficulty: basic -->

`playlist.py` starts with those four songs, so `len(songs)` is 4. Which statement is right?

A. The last valid index is 4, and `songs[4]` is Night Bus.
B. The last valid index is 3, and `songs[4]` raises `IndexError`.
C. The last valid index is 4, and `songs[4]` raises `ValueError`.
D. `len(songs)` is 3, so `songs[3]` is past the end.

## Question 3

<!-- item: Q3 | outcome: LO-3 | difficulty: basic -->

In `playlist.py`, the learner writes `x = songs.append("Garden Song")` while `songs` still holds the four titles. What is true after that line?

A. `x` is the new list, and `songs` is unchanged.
B. `x` is `None`, and `songs` now ends with Garden Song.
C. `x` is Garden Song, and `songs` is unchanged.
D. The line raises `ValueError` because `append` needs an index.

## Question 4

<!-- item: Q4 | outcome: LO-3 | difficulty: standard -->

The class playlist still holds the four titles. The learner wants to drop the second song, Blue Window, and writes `songs.remove(1)`. What happens?

A. Blue Window is removed, because 1 means the second song.
B. Sunrise Walk is removed, because `remove` counts from 0.
C. Python raises `ValueError`, because 1 is not equal to any song title.
D. Night Bus is removed, because `remove` always deletes the last item.

## Question 5

<!-- item: Q5 | outcome: LO-5 | difficulty: standard -->

**Requirement:** `remove()` deletes a title only when that title equals an item in the list. The class playlist holds `"Blue Window"`. The program must then show the count and the first song.

`playlist.py` runs these lines in this order:

```python
songs = ["Sunrise Walk", "Blue Window", "Paper Planes", "Night Bus"]
songs.append("Garden Song")
songs.remove("Blue Windows")
print("Songs:", len(songs))
print("First song:", songs[0])
```

No captured error message is shown. Judge the run from the code and the requirement.

A. `IndexError` on the `remove` line, and the two print lines still run.
B. `ValueError` on the `remove` line, and the two print lines do not run.
C. No error, because the titles are close enough, and the program prints `Songs: 5`.
D. `ValueError` on the `remove` line, and the program prints `Songs: 4`.

## Question 6

<!-- item: Q6 | outcome: LO-4 | difficulty: basic -->

`playlist.py` still starts with the four titles, and this loop runs:

```python
for song in songs:
    print(song)
```

What is `song` the first time through the loop?

A. `0`
B. `1`
C. `Sunrise Walk`
D. `4`

## Question 7

<!-- item: Q7 | outcome: LO-4 | difficulty: standard -->

**Requirement:** the written specification for `playlist.py` numbers the songs from 1 up to the count.

After `"Garden Song"` is appended and `"Blue Window"` is removed, the list is Sunrise Walk, Paper Planes, Night Bus, Garden Song. A counter that starts at 0 prints:

```text
Songs: 4
First song: Sunrise Walk
0 Sunrise Walk
1 Paper Planes
2 Night Bus
3 Garden Song
```

Does this match the specification?

A. Yes. The first index is 0, so the first numbered line should be 0.
B. No. The count and the first song are right, but the numbered lines must start at 1.
C. No. Garden Song should be the first song.
D. No. The count should be 5, because `append` and `remove` do not change the length.

## Question 8

<!-- item: Q8 | outcome: LO-1 | difficulty: stretch -->

**Transfer.** This list is homework tasks, not the class playlist. It starts as:

```python
tasks = ["Read chapter 2", "Worksheet", "Lab notes", "Review quiz"]
```

You append `"Flash cards"` and remove `"Worksheet"`. You print the count, the first item by its index, and every item numbered from 1. Which description matches those rules?

A. The count is 5, the first item is Worksheet, and the numbers run from 0 to 4.
B. The count is 4, the first item is Read chapter 2, and the numbers run from 1 to 4 in this order: Read chapter 2, Lab notes, Review quiz, Flash cards.
C. The count is 4, and the first item is Flash cards, because `append` puts the new item first.
D. The count is 3, because `remove` deletes by position and also drops the next item.

## Predict and reflect

**Predict.** Before you turn on the starter `remove` line in `playlist.py`, write the error type you expect, and write whether the print lines under it will run.

**Reflect.** After that run, write the error type you saw, the line it named, and whether your prediction held. Neither answer is graded for being right.
