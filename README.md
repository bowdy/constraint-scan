# constraint-scan

A Claude Code skill that scans a founder's business every morning, works out the single primary constraint on throughput, and emails a short report with one action for the day.

It reads what is already there (Gmail, Google Calendar, Google Drive, code repositories), has six specialist agents gather dated evidence, four judges propose the constraint through different lenses, refuters try to knock each candidate down, and one synthesiser writes the report. The result commits to exactly one constraint, explains why the runners-up are symptoms or downstream, separates urgent housekeeping from the constraint, and ends with a task finishable before lunch.

## Install

Copy the `constraint-scan/` folder into your skills directory:

```bash
# project-level
mkdir -p .claude/skills && cp -r constraint-scan .claude/skills/

# or user-level
mkdir -p ~/.claude/skills && cp -r constraint-scan ~/.claude/skills/
```

Then copy `constraint-scan/assets/config.example.md` to `constraint-scan.config.md` in your project (or `~/.claude/constraint-scan/config.md`) and fill it in. The config is what makes the scan yours: who you are, what the business is, the goal in your own words, and which sources to read.

Requires the Gmail, Google Calendar and Google Drive connectors in Claude Code. GitHub access is optional.

## Use

- `What's my constraint right now?` runs a scan and emails the report.
- `Set up the constraint scan` creates the config with you.
- `Schedule the constraint scan every morning` walks through the routine (see `constraint-scan/references/scheduling.md`).
- Add `TEST MODE` to any request to get a Gmail draft instead of a sent email.

## Layout

```
constraint-scan/
  SKILL.md                      the skill: modes, pipeline, rules
  references/method.md          Theory of Constraints vocabulary, sweep briefs, judge lenses, refuters
  references/report-template.md the email format and footer
  references/scheduling.md      running it daily, idempotency, testing
  scripts/workflow.js           optional Workflow-tool script with cached resumes
  assets/config.example.md      the config template
```

## Author

Richard Bowdler. MIT licence.
