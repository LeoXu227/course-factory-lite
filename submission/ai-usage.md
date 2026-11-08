# AI usage

`claude` was not installed on this machine, and no Claude Code session ran. Cursor's coding agent (Grok) read the spec, the templates, `STYLE.md`, the sibling agent files, and the quiz checks in `scripts/check_package.py`. It wrote `.claude/agents/assessment-designer.md`, then followed that file to draft the three module 1 assessment files. The agent file names `sonnet` for a later Claude Code run. That model did not run here.

Unit tests and `check_package.py` were run in the terminal. Their output was pasted, not rewritten, into the QA reports.

## One suggestion that was rejected

The first draft of Q5 stated the verdict in the stem: the error type is `ValueError`, and neither print line appears. The correct option then repeated those two facts. That draft was rejected. A learner cannot judge a run that the stem has already decided. The agent instructions now say the stem states the requirement and the evidence, and does not state the verdict. Q5 was regenerated from that rule. It shows the code and asks what the run does.

A second idea was also rejected and never written down: pasting `list.remove(x): x not in list` from the Treehouse thread into Q5. The source pack marks that message unsourced for this Python version (`SP-U1`), and the syllabus says not to rely on it unless someone captured a run. No run was captured.
