# Course Factory Lite: guided task starter

> [!IMPORTANT]
> This repo is for **task 5a** of the FDE Learning Kit. If you have not yet, read
> [Page 05](https://github.com/AzurePartnersOrg/fde-learning-kit/blob/main/ai-course-factory/05-hands-on-practice/README.md)
> first. Then follow the steps below.

## Your task

One agent is missing: `.claude/agents/assessment-designer.md`, which writes each module's quiz,
answer key and TA feedback pack. You rebuild it from `specs/assessment-designer-spec.md`, run it on
the sample course `courses/intro-python-lists-hs/` (its quiz files are removed), and prove it works.

## Steps

1. **Save your "before".** In a terminal (not inside Claude), run:

   ```
   python -m unittest scripts/test_agents.py -v
   python scripts/check_package.py intro-python-lists-hs --through production --no-pdf
   ```

   Both report failures, because the agent is missing. That is expected. The checker also shows one
   minor `HEADING-CASE` finding on the deck, a known false positive. Copy the output into
   `submission/qa-report-before.md` and commit.
2. **Read** `specs/assessment-designer-spec.md`, the three templates `templates/quiz-m01.md`,
   `templates/quiz-m01-key.md` and `templates/ta-feedback-pack-m01.md`, and the quiz checks in
   `scripts/check_package.py`. Look at `.claude/agents/deck-writer.md` and
   `.claude/agents/lab-engineer.md` for the pattern.
3. **Write** `.claude/agents/assessment-designer.md`. You can use Claude to help.
4. **Test it.** Run the first command from step 1 again until every test passes. Commit.
5. **Run it.** Start a new `claude` session in this folder (agents load when a session starts) and
   ask: `Run assessment-designer for intro-python-lists-hs, module 1.` Then run the second command
   from step 1 again.
6. **Fix your agent, not the quiz,** until the checker shows no blocking findings. Commit each round.
7. **Check three questions by hand,** then fill in `submission/` (see `submission/README.md`).

The [5a guided brief](https://github.com/AzurePartnersOrg/fde-learning-kit/blob/main/ai-course-factory/05-hands-on-practice/5a-guided-brief.md)
has the same steps with hints, what "done" means, and how it is graded.

## Good to know

- Do not run `/new-course`. The sample course is already built, and a new course costs a lot of
  tokens.
- Below is the general project manual. Use it for setup (**What you need**) and when something goes
  wrong (**Troubleshooting**).

---

## About the project

Turn one request into a reviewed course package: a viability brief, a syllabus, a lecture deck,
a quiz with an answer key, a hands-on lab, and a QA report. Every output is a markdown file and a
PDF. Three human gates keep a person in charge, and a TA agent supports students after publish.

It runs inside Claude Code in the terminal. Claude Desktop's Code tab opens the same project folder,
which should read the same `CLAUDE.md`, agents and commands, but that has not been tested here.

This is a lighter rebuild of an earlier pipeline. `PLAN.md` explains what was kept and cut, and
`docs/dry-run-1.md` records the first full run.

## What you need

- Git, [uv](https://docs.astral.sh/uv/), Google Chrome (the renderer prints PDFs through it), and
  Claude Code signed in.
- Python 3.9 or newer on your path, for the check scripts.
- Cost: a one-module course used about 1.1 million subagent tokens in the first run on Sonnet.
  Three agents are set to Opus in their files, so a default run costs more. Edit the `model:` line
  of an agent to change it.

Check your machine:

```
powershell -File scripts/readiness-check.ps1     # Windows
bash scripts/readiness-check.sh                  # macOS or Linux
```

## Commands

| Command | What it does |
| --- | --- |
| `/new-course <topic>, level: <level>[, modules: N][, capstone: ...]` | Start a course and open Gate 0 |
| `/continue [slug]` | Do the next step, or show the gate you owe a reply on |
| `/status [slug]` | Show where courses stand |
| `/render <slug> [stage]` | Render PDFs |
| `/qa <slug>` | Rerun the checker and the QA review |
| `/ask-ta <slug> <question>` | Ask the TA as a student would |
| `/ta-digest <slug>` | Write the digest of student questions |

## What you get

```
courses/<slug>/
  STATUS.md  APPROVALS.md
  00-viability/   viability-brief.md  source-pack.md
  01-syllabus/    syllabus.md
  02-deck/        deck-m01.md
  03-assessments/ student/quiz-m01.md
                  instructor/quiz-m01-key.md  ta-feedback-pack-m01.md
  04-labs/        lab-m01.md
  qa/             qa-report.md  alignment-matrix.md  ta-grounding-manifest.md
  maintenance/    ta-log.md  ta-digest-<date>.md
  dist/           the PDFs (git ignores this folder)
```

Markdown is the master. Edit the markdown and render again, never the PDF. The decks come as two
PDFs: one for students, and one with the speaker notes for the instructor. Instructor files carry an
"Instructor only" banner and are never shown to students or to the TA.

## How it keeps itself honest

- **Gates.** Agents cannot approve anything. Only your reply to a pending gate (Gate 0, Gate 1 or
  Gate 2) is logged, in your own words, by `scripts/approve.py`. A hook blocks agents from writing
  out of order.
- **Sources.** Every product claim has an `SP-` ID, a mechanism and a source the researcher opened.
  Gaps are declared, not filled.
- **Checks.** `scripts/check_package.py` runs the mechanical rules at no token cost, and a QA agent
  does the judgment checks: worked examples, boundaries, level fit, and answer leaks.
- **Labs are written, not run.** Every lab step is marked as an unexecuted teaching sample, and
  nothing guesses at a tool's exact output. Run the lab yourself before teaching it.
- **TA.** It answers only from the files in the grounding manifest, never grades, never reveals a
  key, and escalates what it cannot answer. Treat its answers as a first line, not the last.

## The pieces

| Path | What it is |
| --- | --- |
| `CLAUDE.md` | The main session's playbook: states, gates, fix loop |
| `.claude/agents/` | Eight agents: producer, researcher, curriculum architect, deck writer, assessment designer, lab engineer, QA reviewer, TA |
| `.claude/commands/` | The slash commands |
| `.claude/settings.json` | Hooks and a short allowlist of safe commands |
| `STYLE.md` | House rules every agent follows |
| `templates/` | The skeleton for every artifact |
| `build/` | The markdown to PDF renderer and its themes |
| `scripts/` | The checker, the approval and log scripts, hooks, and all tests |
| `courses/_fixture/` | A sample course the tests use. Do not edit it casually |

## Tests

```
python -m unittest discover -s scripts -p "test_*.py"
```

## Troubleshooting

| Symptom | Cause | Fix |
| --- | --- | --- |
| `Agent type 'course-producer' not found` | Agents load when a session starts | Quit and start a new `claude` session in this folder |
| The slash commands do not appear | Same, or you are in the wrong folder | Start `claude` in the folder that holds `CLAUDE.md` |
| `error: Chrome not found` | Chrome is somewhere unusual | Set `CHROME_PATH` to the Chrome program |
| The first render takes minutes | `uv` is fetching packages | Wait once. Later renders take seconds |
| Red "NativeCommandError" text in PowerShell | `uv` prints a notice to stderr | Use `./run.ps1`, which silences it, or ignore the text |
| `stage guard: ... cannot be written until Gate N` | An agent tried to write ahead of a gate | Working as intended. The producer approves the gate first |
| `refused: ... reads as hedged` | Your reply had "but", a question, or similar | Reply with a plain "yes", or give the changes you want |
| A checker `PDF-STALE` finding | Markdown changed after its PDF | `/render <slug>` |
| A checker blocking finding | A rule was broken | The finding names the owner. The producer sends it back, up to three times |
| `Could not resolve host: github.com` | A network blip | Retry the push |
| A TA question never shows in the digest | The log line was refused | The script says why. Fix the line and run it again |

If a command asks for permission to run `scripts/ta_log.py`, approve it, or add
`Bash(python scripts/ta_log.py:*)` to the allowlist in `.claude/settings.json`.

## Limits

- Tested end to end on one topic, on Sonnet. See `docs/dry-run-1.md` for what is and is not proven.
- Hooks and slash commands are tested as scripts. A fresh live session is the real test.
- The agents cannot run code, so software labs are unverified until a person runs them.
- Hooks are guardrails, not security. The main session can run commands and could write around them.
