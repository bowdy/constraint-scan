# Report template

Subject: `<prefix>, <Ddd D Mon YYYY>: <one line, at most 70 characters>`

Plain language, second person, direct and warm, no hype, no lecturing. Main body 600 to 900 words; the appendix may be longer. British or American spelling to match the owner. Headings in this order, exactly:

1. **The constraint.** One bold sentence naming the single primary constraint, then two or three short paragraphs on the mechanism and the dated evidence, citing source and date inline, for example "(Drive, running thoughts, 15 Sep)". Say what throughput it blocks in the owner's own terms. Include the day-over-day line: "Same constraint as yesterday (day N)" or "Changed from X because Y".
2. **Why not the other candidates.** Two to four runners-up, one short paragraph each, each ending with why it is downstream, a symptom, or not binding today.
3. **Exploit it today.** What to do with the constraint today, what to stop or subordinate this week (name specific calendar items and inbox threads to say no to), and what elevating it would look like. Then a bold line **Today's one action**: one task finishable in under four hours, with its first physical step (which document to open, whom to message, which decision to write down) and a definition of done.
4. **Housekeeping (urgent, not the constraint).** Dated items due this week that do not unlock throughput, each with a deadline. Only the ones that matter.
5. **Signals to watch.** Three to five observable signals that the constraint is moving, and what would change the verdict.
6. **How this was produced.** Two sentences on the sources scanned and any source that was unavailable, plus the comparison with the previous report.
7. **Evidence appendix.** 10 to 20 compact dated facts.

Footer, one line, machine-readable: `CONSTRAINT-KEY: <kebab-case-slug> | CONFIDENCE: <0 to 1> | DATE: <YYYY-MM-DD>`. Keep the slug stable from day to day while the constraint is the same; the next run reads it.

Then the state block, which is what makes delta days possible. At most 25 lines, no secrets, no email addresses other than the owner's, no personal details beyond names. It goes in both the plain-text body and, in a small grey monospace block, at the end of the HTML.

```
STATE-BEGIN
mode: full | delta
day: <N, days this slug has held>
last-full: <YYYY-MM-DD>
escalate: none | full
goal: <one line, quoted from the owner>
constraint: <slug> | <one sentence>
hypotheses: H1 <slug> <survived|refuted|untested>; H2 ...; up to four
action: <today's one action, one line> | done-yesterday: yes | no | partly
open-items: <deadline YYYY-MM-DD> <item> <source>; ... at most ten
signals: <signal> => <query or check>; ... three to five
cursors: gmail=<ISO datetime> drive=<ISO datetime> git=<sha or none>
STATE-END
```

On delta days the report is shorter: section 1 may be one paragraph, sections 2 and 7 may be a single line ("Unchanged since Monday's full scan"), and section 6 becomes "What changed in the last 24 hours" (action done or not, signals fired or not, items resolved or added). Signals should be phrased so tomorrow's delta agent can check each with one search or one glance.

The email carries both an HTML body (self-contained, inline CSS only, max-width 640px, system font stack, 16px, generous line height, a light grey box around "Today's one action", no images, no external assets) and the markdown as the plain-text body. Both must be complete; a placeholder in either is what the reader sees.
