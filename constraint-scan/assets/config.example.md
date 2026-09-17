# constraint-scan config

Copy this file to `constraint-scan.config.md` in your project (or to `~/.claude/constraint-scan/config.md`) and fill it in. Everything here is read at the start of every scan.

## Owner

- Name: Jane Example
- Email (reports go here, and only here): jane@example.com
- Timezone: Europe/London
- Working pattern the owner wants: "4 hours a day, no work in school holidays"

## Business

- Legal entity and trading name: Example Ltd, trading as Example
- What it is, in two lines: A paid community for parents handling the first-phone transition, with a flagship mini-course. A mobile-network proposition is parked.
- Goal in the owner's own words (this defines throughput): "£19 a month, 1,000 families, cashflow plus time."
- People who matter: co-founder (name, email), key investors, key partners
- Volunteer or personal commitments that are not the business (so they are classified correctly): campaign work, school governor role

## Sources

- Gmail label ids for "to respond", "action required", "waiting", "notes" (run `list_labels` once to find them)
- Company email domains and addresses: example.com, hello@example.com
- Drive title keywords for strategy documents: Example, community, pricing, launch
- Running-thoughts document title: "Example - ongoing thoughts"
- Repositories: owner/repo, owner/other-repo
- Sources that are known to be unreachable from the sandbox (so the report says so rather than guessing): the community platform's member count, the live website

## Models and cadence

- Re-baseline day (full scan): Monday. Every other day is a delta scan unless the state is missing or says `escalate: full`.
- Models per stage (Agent tool takes `model`; the Workflow tool also takes `effort`):
  - delta scan: sonnet, medium
  - sweeps: sonnet, medium
  - judges: opus, high
  - refuters: opus, high
  - synthesis: the orchestrating session (or opus, max in the Workflow script)
  - critic (Workflow script only): sonnet, high
- Judge lenses on full days: 2 (strict Goldratt; first paid pound). Set to 4 for the deeper panel.
- Caps: 5 threads opened in full on a delta day; 10 per sweep agent on a full day; 3 Drive documents on a delta day, 5 per sweep on a full day.

## Reports

- Subject prefix: Morning constraint report
- Send hour (owner's local time): 06:30
- Language and spelling: British English
