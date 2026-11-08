# Submission: task 5a

Task 5a from the Course Factory learning kit. The starter had no `assessment-designer` agent. This private repo adds that agent and the module 1 quiz, instructor key, and TA feedback pack for `intro-python-lists-hs`.

## What changed

- `.claude/agents/assessment-designer.md`: the missing agent. It may write only the three assessment files, reads `STYLE.md` and the three templates first, and keeps student files off the instructor tree.
- `courses/intro-python-lists-hs/03-assessments/student/quiz-m01.md`
- `courses/intro-python-lists-hs/03-assessments/instructor/quiz-m01-key.md`
- `courses/intro-python-lists-hs/03-assessments/instructor/ta-feedback-pack-m01.md`

The deck was not edited. The known `HEADING-CASE` line on `deck-m01.md` is still in both QA reports.

## Commits

- Before, baseline QA only, no agent change: `e2f34e3209b980cd162b94aa8dd0f5fb16b4e905`
- Agent file, tests passing, before the quiz files: `a07c47d614cce2be08304fe75dd248301fd9223f`
- After, agent tightened and the three module 1 files added: `5fd9fe9e6e847b4f50506cab18b45ddeb7967ae1`

`submission/qa-report-before.md` is in the before commit. `submission/qa-report-after.md` is in the commit that adds this README, on top of the after commit.
