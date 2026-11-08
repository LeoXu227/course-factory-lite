# QA report before

Commands run in the repo root, before any agent change. Output is pasted as the terminal printed it.

```
python -m unittest scripts/test_agents.py -v
```

```
test_every_agent_ends_with_the_report_block (scripts.test_agents.AgentFiles.test_every_agent_ends_with_the_report_block) ... ok
test_every_agent_reads_style_and_states_its_scope (scripts.test_agents.AgentFiles.test_every_agent_reads_style_and_states_its_scope) ... ok
test_exactly_the_expected_agents (scripts.test_agents.AgentFiles.test_exactly_the_expected_agents) ... FAIL
test_front_matter (scripts.test_agents.AgentFiles.test_front_matter) ... ok
test_no_agent_may_approve (scripts.test_agents.AgentFiles.test_no_agent_may_approve) ... ok
test_no_em_dashes (scripts.test_agents.AgentFiles.test_no_em_dashes) ... ok
test_no_video_agent (scripts.test_agents.AgentFiles.test_no_video_agent) ... ok
test_only_researcher_has_web_tools (scripts.test_agents.AgentFiles.test_only_researcher_has_web_tools) ... ok
test_qa_cannot_edit (scripts.test_agents.AgentFiles.test_qa_cannot_edit) ... ok
test_ta_agent_cannot_search_the_repo (scripts.test_agents.AgentFiles.test_ta_agent_cannot_search_the_repo) ... ok
test_ta_agent_reports_its_log_line_instead_of_writing_the_log (scripts.test_agents.AgentFiles.test_ta_agent_reports_its_log_line_instead_of_writing_the_log) ... ok

======================================================================
FAIL: test_exactly_the_expected_agents (scripts.test_agents.AgentFiles.test_exactly_the_expected_agents)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/home/ubuntu/work/course-factory-5a/scripts/test_agents.py", line 32, in test_exactly_the_expected_agents
    self.assertEqual(EXPECTED, found)
AssertionError: Items in the first set but not the second:
'assessment-designer'

----------------------------------------------------------------------
Ran 11 tests in 0.002s

FAILED (failures=1)
```

```
python scripts/check_package.py intro-python-lists-hs --through production --no-pdf
```

```
check_package: intro-python-lists-hs through production
  BLOCKING MANIFEST-MISSING       03-assessments/instructor/quiz-m01-key.md: required file is missing  -> assessment-designer
  BLOCKING MANIFEST-MISSING       03-assessments/instructor/ta-feedback-pack-m01.md: required file is missing  -> assessment-designer
  BLOCKING MANIFEST-MISSING       03-assessments/student/quiz-m01.md: required file is missing  -> assessment-designer
  MINOR    HEADING-CASE           02-deck/deck-m01.md:276: heading looks like Title Case; use sentence case  -> deck-writer
metrics:
  claims in source pack: 33, citations: 143
  deck m01: 22 slides, longest abstract run 2, notes 2337 words vs budget 2340, narration gap -0.0 min
  lab m01: step minutes 29 vs hands-on 29
result: 3 blocking, 1 minor
```

The deck `HEADING-CASE` line is a known false positive. It is kept as printed. The deck was not changed.
