# QA report after

Command run in the repo root after the assessment-designer agent and the module 1 files. Output is pasted as the terminal printed it.

```
python scripts/check_package.py intro-python-lists-hs --through production --no-pdf
```

```
check_package: intro-python-lists-hs through production
  MINOR    HEADING-CASE           02-deck/deck-m01.md:276: heading looks like Title Case; use sentence case  -> deck-writer
metrics:
  claims in source pack: 33, citations: 157
  deck m01: 22 slides, longest abstract run 2, notes 2337 words vs budget 2340, narration gap -0.0 min
  lab m01: step minutes 29 vs hands-on 29
result: 0 blocking, 1 minor
```

The deck `HEADING-CASE` line is the known false positive. It is kept as printed. The deck was not changed.

No `MANIFEST-MISSING` for `03-assessments`. No blocking `QUIZ-*` or `KEY-*`. No `WALL-LEAK`. No `TA-ANSWER-LEAK`.

Hand-checked question ids: Q2, Q5, Q7.
