---
course: intro-python-lists-hs
stage: 03-assessments/instructor
module: 01
author: assessment-designer
date: 2026-11-08
outcomes: LO-1, LO-2, LO-3, LO-4, LO-5
---

# TA feedback pack: module 01

Safe for a TA to use with a student. Criteria and confusions only. No solutions.

## What each quiz item measures

| Item | Outcome | What it checks | Common confusion, explained without the answer |
| --- | --- | --- | --- |
| Q1 | LO-2 | Naming the first song by its index in playlist.py | Learners count the first item as position 1, or they write parentheses instead of brackets |
| Q2 | LO-2 | The last valid index of a four-song list, and an index equal to the count | Learners treat the count as a position that still holds a song |
| Q3 | LO-3 | What append changes, and what the call gives back | Learners expect the call to hand back the new list, and they assign that result |
| Q4 | LO-3 | remove matches a title, not a position | Learners pass a position because brackets and numbers already mean a position |
| Q5 | LO-5 | Judging a remove line in playlist.py whose title is one letter off | Learners treat a near title as a match, or they expect the print lines under that line to run |
| Q6 | LO-4 | What the loop variable holds on the first pass | Learners expect a number, because a loop feels like counting |
| Q7 | LO-4 | Numbered playlist lines that start at 0 | Learners copy the first index into the displayed number, even when the count line looks fine |
| Q8 | LO-1 | The same steps on a homework list the capstone never uses | Learners reuse song titles, start the display at 0, or put the appended item first |

## Lab rubric criteria

- `playlist.py` runs to the end with no error and prints the six specified lines and nothing else.
- The count line equals the number of songs left after one song is added and one song is removed.
- The first-song line is the item at index 0 of that finished list.
- The numbered lines start at 1 and follow the finished list order, one line per song.
- A remove line that names a missing song is fixed by editing that name so it matches a title in the list. The list is not edited to fit the typo.

## Hints that do not give the answer

- How many steps from the start of the list is the first item?
- When append runs, what changes in the list, and what does the call give back?
- Does remove look for a title or for a position?
- If the run stops on the remove line, do the print lines under it still run?
- On the first pass of the for loop, is the loop variable a title or a number?
- If the first numbered line shows 0, where did the counter start?
- For a list of homework tasks, which of those rules stay the same?
