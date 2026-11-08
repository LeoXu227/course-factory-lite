# Report: assessment-designer for module 1

## Problem

The starter ships seven agents and no `assessment-designer`. For `intro-python-lists-hs`, the production check was missing the module 1 quiz, the instructor key, and the TA feedback pack. Agent tests failed on the missing file. The deck `HEADING-CASE` line was already present and is a known false positive.

## Change

`.claude/agents/assessment-designer.md` now writes only `courses/{slug}/03-assessments/student/quiz-m{NN}.md`, `instructor/quiz-m{NN}-key.md`, and `instructor/ta-feedback-pack-m{NN}.md`. It reads `STYLE.md` and the three templates first. Tools are Read, Write, Edit, Glob, and Grep. The model field is `sonnet`, the same choice as deck-writer and lab-engineer: this step is structured course writing with a hard student and instructor wall, not open research. Haiku is an easier place to leak an answer into the TA pack. Opus is more model than the template needs.

`claude` was not installed, so Claude Code did not run. The three module 1 files were written by following the agent file. The syllabus quiz contract fixed eight items: four basic, three standard, one stretch, outcomes LO-1 through LO-5. The mention-only topic, removing items while looping, is not a tested skill.

## Results

`python -m unittest scripts/test_agents.py -v` passed: 11 tests, OK. The production checker ended at `result: 0 blocking, 1 minor`. The only line left is the deck `HEADING-CASE` false positive. There is no `MANIFEST-MISSING` for `03-assessments`, no blocking `QUIZ-*` or `KEY-*`, no `WALL-LEAK`, and no `TA-ANSWER-LEAK`.

## What failed, and the limits

The first Q5 stem gave away the verdict. It was rejected and regenerated. See `ai-usage.md`. Q5 still has no captured traceback, so it cannot ask a learner to read a real line number or message. `SP-U1` stays open. The 3-minute video is not recorded yet.

## Three questions, read against the key

Q2. The key says B: four songs use indexes 0 to 3, and index 4 raises `IndexError` (SP-1.2, SP-1.3). That matches the boundary. Option A is the real mistake, treating the count as an index. Option D is weak: the stem already says `len(songs)` is 4, so "the length is 3" is easy to throw out.

Q5. The key says B: `"Blue Windows"` is not equal to `"Blue Window"`, so `remove` raises `ValueError` and the print lines under it do not run (SP-1.5). The key refuses the unsourced message text (SP-U1). That boundary is right. The item is still weak as a judgement of output: the student sees code, not a captured run, and must recall the error type.

Q7. The key says B. The shown lines start at 0, and the requirement says the numbers start at 1. The count and the first song can be right while the numbers are wrong. The list order in the stem matches one append and one remove. The weakness is that the stem says the counter starts at 0, so the learner compares 0 with 1 instead of finding the cause. The key cites SP-1.7, which is about `enumerate`, while this course numbers with a counter.

## Video

The 3-minute video is not recorded yet.
