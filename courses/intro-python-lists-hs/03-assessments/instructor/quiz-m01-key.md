---
course: intro-python-lists-hs
stage: 03-assessments/instructor
module: 01
author: assessment-designer
date: 2026-11-08
outcomes: LO-1, LO-2, LO-3, LO-4, LO-5
---

# Instructor key: quiz-m01

Instructor only. Never copy into the student tree.

## Q1 - Answer: B

- A: a student choosing this thinks the first item is index 1, the way people count in daily life.
- **B is correct.** The first item is index 0, so `songs[0]` is Sunrise Walk (SP-1.1).
- C: a student choosing this uses the count, 4, as if it were an index.
- D: a student choosing this writes a call with parentheses instead of an index in brackets.

## Q2 - Answer: B

- A: a student choosing this treats `len(songs)` as the last index and expects `songs[4]` to return an item.
- **B is correct.** Four items use indexes 0, 1, 2, and 3. An index equal to the length, here 4, raises `IndexError` (SP-1.2, SP-1.3).
- C: a student choosing this names `ValueError`, which is the error for a missing `remove` value, not a bad index.
- D: a student choosing this subtracts one from the count and then treats that result as the length.

## Q3 - Answer: B

- A: a student choosing this thinks `append` returns the new list, so the assignment is how you keep the change.
- **B is correct.** `append` changes `songs` in place and returns `None`, so `x` is `None` and Garden Song is now the last item (SP-1.4).
- C: a student choosing this thinks the method returns the value it was given, and that the list itself does not change.
- D: a student choosing this confuses `append` with indexing and expects an error when no index is passed.

## Q4 - Answer: C

- A: a student choosing this thinks `remove(1)` means position 1, the second song.
- B: a student choosing this thinks `remove` takes an index and that the index starts at 0.
- **C is correct.** `remove` matches by value, not by position. The number 1 is not equal to any title, so Python raises `ValueError` (SP-1.5).
- D: a student choosing this thinks `remove` with no matching title deletes the last item instead of stopping.

## Q5 - Answer: B

Source of truth: a written specification, the four starting titles and the rule that `remove` deletes a title only when it equals an item.
Requirement quoted from the item: "remove() deletes a title only when that title equals an item in the list."
Boundary check: "Blue Windows" is not equal to "Blue Window". One extra letter is not a match, so this is a missing value, not a near miss. The prints sit under the failing line, so they do not run. They would not print `Songs: 4`, because the remove did not succeed, and they would not print `Songs: 5`, because they do not run at all.

The exact words after `ValueError` are not in this key. That message text is unsourced for this Python version (SP-U1). The item shows the code, not an invented message (SP-1.5).

- A: a student choosing this names `IndexError`, the error for a bad index, and thinks later lines still run.
- **B is correct.** A missing title raises `ValueError`, and Python stops on that line, so the two print lines do not run (SP-1.5).
- C: a student choosing this treats a one-letter difference as close enough and expects the count after the append, which is 5, to print.
- D: a student choosing this names the right error type but still expects a successful count of 4 to print.

## Q6 - Answer: C

- A: a student choosing this thinks the loop variable is the index, starting at 0.
- B: a student choosing this thinks the loop variable is a count starting at 1.
- **C is correct.** `for song in songs` sets `song` to each title in order, so the first value is Sunrise Walk, not an index (SP-1.6).
- D: a student choosing this thinks the loop variable is the length of the list.

## Q7 - Answer: B

Source of truth: a written specification, the expected-output block, which numbers songs from 1 to the count.
Requirement quoted from the item: "the written specification for playlist.py numbers the songs from 1 up to the count."
Boundary check: a first numbered line of 0 is not a first numbered line of 1. The count line and the first-song line can be right while the numbers are wrong. Index 0 is still the first song, and that fact does not set the displayed number.

- A: a student choosing this copies the first index into the displayed number.
- **B is correct.** The list order and the count 4 follow from one append and one remove. The displayed numbers must start at 1, so a counter that starts at 0 does not match (SP-1.7).
- C: a student choosing this thinks `append` inserts at the front, so Garden Song would be first.
- D: a student choosing this thinks `append` and `remove` leave the length at 5, forgetting that one title was removed.

## Q8 - Answer: B

Source of truth: a written specification, the same rules as the class playlist, applied to a new list.
Requirement quoted from the item: "You append Flash cards and remove Worksheet. You print the count, the first item by its index, and every item numbered from 1."
Boundary check: one append and one remove leave four items, not five and not three. The first item stays Read chapter 2, at index 0. The numbers start at 1, not 0. Flash cards is last, not first.
What a learner who pattern-matched the capstone would answer instead: they would reuse the song titles, or start the numbers at 0 because the playlist's first index is 0.

- A: a student choosing this forgets the remove, keeps a count of 5, and starts numbering at 0.
- **B is correct.** Start with four tasks, append one, remove Worksheet. Left: Read chapter 2, Lab notes, Review quiz, Flash cards. Count 4, first item at index 0, numbers 1 to 4 (SP-1.1, SP-1.3, SP-1.4, SP-1.5).
- C: a student choosing this thinks `append` puts the new item at the front.
- D: a student choosing this thinks `remove` deletes by position and also drops the next item, the skip that this module only mentions and does not test as a skill.
