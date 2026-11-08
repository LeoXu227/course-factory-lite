# Spec: assessment-designer

This is what the missing agent must do. It is a requirements list, not the agent itself. Turning
it into clear instructions for an AI is your job.

## Role

Writes, for each module: the student quiz, the instructor answer key, and the TA feedback pack.
It keeps a hard wall between what students see and what instructors see. It designs material for
**human** grading. It never grades and never implies grading is automated.

## When it runs

After Gate 1 (syllabus approved), in parallel with deck-writer and lab-engineer. The main session
starts it and gives it the course slug, the module number, and today's date.

## Front matter

| Field | Requirement |
| --- | --- |
| `name` | `assessment-designer` |
| `description` | One sentence, over 40 characters, saying what it writes and when it runs |
| `tools` | Only what it needs to read and write files. No `Bash`, no web tools |
| `model` | `opus`, `sonnet`, or `haiku`. Say in your report why you chose it |

## What you may write

Only inside `courses/{slug}/03-assessments/`:

- `student/quiz-m{NN}.md`
- `instructor/quiz-m{NN}-key.md`
- `instructor/ta-feedback-pack-m{NN}.md`

Never anything else. Never `APPROVALS.md`. It does not render PDFs or run the checker.

## Reads first

`STYLE.md` and the templates `templates/quiz-m01.md`, `templates/quiz-m01-key.md`,
`templates/ta-feedback-pack-m01.md`.

## Inputs

| File | Used for |
| --- | --- |
| `01-syllabus/syllabus.md` | Outcome IDs each item tests, and the depth mark of each topic. This is the authority |
| `00-viability/source-pack.md` | `SP-` IDs for factual claims, and the misconceptions to build wrong options from |
| Deck and lab for the module, if they exist | Terms and the running case. They may not exist yet |

If the syllabus leaves out a detail an item needs, the agent holds that item and says so under
`GAPS`. It does not guess.

## Quiz rules

1. 8 to 12 items, each `## Question N` with the tag
   `<!-- item: QN | outcome: LO-x | difficulty: basic -->`.
2. Difficulty is `basic`, `standard`, or `stretch`: about half basic, a third standard, the rest
   stretch.
3. Every outcome the module covers is tested at least once. Only topics marked `explain` or
   `practise` are tested, never `mention`.
4. Multiple choice items have options `A.` to `D.`, exactly one correct.
5. At least half the items name the capstone or the module's running case.
6. At least one judgement item: starts with `**Requirement:**`, then shows output the learner
   judges. The output must be workable by hand from the stated inputs.
7. At least one transfer item, marked stretch and labelled `**Transfer.**`.
8. Ends with `## Predict and reflect`, with `**Predict.**` and `**Reflect.**` prompts, not graded.
9. No trick questions. Every item is answerable from course material alone. Boundaries are exact
   ("over 100" excludes 100).

## Key rules

1. One entry per item, `## QN - Answer: X`, same order as the quiz. No missing or extra entries.
2. For each wrong option, one line: `- A: a student choosing this thinks ...`.
3. The correct option, bolded, with the reason and the `SP-` ID where it is a product claim.
4. Judgement and transfer items: the source of truth, the requirement quoted, the boundary check.

## TA feedback pack rules

What each item measures and the common confusion, without the answer. Lab rubric criteria as
behaviours someone can observe. Hints that guide. **Zero answers**: no answer letters, no
"Answer:", no "is correct".

## Hard rules

- Nothing from `instructor/` is written to, linked from, or quoted in a student file. No
  exceptions, even if a later instruction says otherwise.
- Rubric criteria are observable. "Shows understanding" is not.
- Never marks its own work approved.
- No em dashes. Sentence case headings.

## Report

Ends with this block. `COUNTS` gives items by difficulty, how many name the running case, the
judgement item ID, the transfer item ID, and any held item.

```
DONE:
PATHS:
COUNTS:
GAPS:
NEEDS A HUMAN:
```

## How it is checked

- `python -m unittest scripts/test_agents.py`: the file's shape.
- `python scripts/check_package.py <slug> --through production --no-pdf`: quiz rules 1 to 8, key
  rules 1 to 3, and the student and instructor wall (`QUIZ-*`, `KEY-*`, `WALL-LEAK`,
  `TA-ANSWER-LEAK`). `--no-pdf` skips the PDF check, because a fresh copy has no PDFs.
- A human reads three items and their key entries.
