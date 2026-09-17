# Method: how the scan thinks

## The idea in one paragraph

A business is a chain of dependent steps between today and the owner's goal. At any moment one link limits throughput; improving any other link changes nothing until that one moves. The scan's job is to find that link, say why the runners-up are downstream or symptoms, and turn it into one action the owner can finish today. Goldratt's five focusing steps give the report its shape: identify, exploit (get the most out of it today), subordinate (stop everything that competes with it), elevate (invest to remove it), repeat.

## Vocabulary the agents should keep straight

- **Constraint**: the link that limits throughput now. Relieving it raises throughput immediately.
- **Symptom**: a downstream effect (empty calendar, unanswered mail, low signups). Fixing it directly does not raise throughput because the cause upstream keeps producing it.
- **Necessary condition**: something that must hold (a registered company, a working bank account, a valid domain) but that does not set the rate of throughput. Urgent housekeeping lives here. It goes in the report, in its own section, never as the constraint.
- **Policy constraint**: a rule or habit that limits flow ("learn before doing", "raise before selling", "keep both ventures open"). Often the real root when every physical candidate turns out to be a symptom.

## Sweep briefs

Give each sweep agent the config, the read-only rule, the tool notes, and one of these. Ask for dated observations, candidate constraints, and unknowns. Adjust the search strings to the config (label ids, company domains, names).

**a) Inbox obligations (last 21 days).** Deadlines, notices, invoices, cancellations, verification demands, and every inbound message from a real person that has no reply. Searches at minimum: important mail not from the owner and not promotions; the owner's "to respond", "action required" and "waiting" labels if they exist; `(invoice OR "past due" OR "final notice" OR cancelled OR suspended OR verification OR overdue OR "payment failed") newer_than:21d`; mail from the company formation agent, the domain or email host, and the business bank; mail to the company's own addresses. Classify each item company-critical, business, volunteer, or personal.

**b) Commercial pipeline (last 120 days).** Investors or lenders, the co-founder, customers and waitlist signals (form submissions per week, community joins, payments), partners and suppliers, and everything the owner sent in the last 30 days classified by business, volunteer, personal, other, with counts. Name the single most valuable stalled conversation.

**c) Calendar (14 days back, 14 ahead).** Classify every event: business, the new venture if there is one, volunteer, learning and courses, admin, family, or routine templates. Hours per category per week excluding templates. What overlays the owner's deep-work block. Fixed commitments ahead. Compare with the owner's stated working pattern.

**d) Strategy documents (modified in the last 45 days).** Timeline of edits. Read the key documents in full. Decisions made (with quotes), decisions still open (price, offer, which venture, what to tell whom), ratio of thinking documents to shipped customer-facing artifacts, and any launch date, price, or checkout anywhere.

**e) Founder decision state.** Notes-to-self, the owner's running-thoughts document, and the volume of newsletters and course digests arriving. Report the stated goal (quote), decisions made, decisions oscillating, promises to other people that are outstanding, the gap between the stated goal and where attention goes, and what the owner seems to think the constraint is.

**f) Product and code.** Recent commits on the named repositories and their plan documents. What is live, what is built but not shipped, the shortest technical path to the first unit of throughput. If GitHub tools are absent, return that as an unknown and stop.

## Judge lenses

Each judge gets all six observation sets and one lens, and returns at most five ranked hypotheses with mechanism, dated evidence, why it is not a symptom, and what relieving it unlocks.

1. **Strict Goldratt.** Define the goal in the owner's words. Map the chain (decide, define the offer, minimum build, reach, convert, deliver, retain, plus enabling conditions: entity, cash, co-founder, founder hours). Find the one binding link. Be rigorous about constraint versus bottleneck versus symptom versus policy. The constraint is where the queue is.
2. **Offer, reach and conversion.** What stops the first unit of throughput arriving this week: no sellable offer, nobody knows, no way to convert, or the founder consuming instead of shipping?
3. **Survival and obligations.** Entity, cash, investors, co-founder. Which of these truly bind throughput, and which are urgent housekeeping that must be done but change throughput by zero? Say so explicitly.
4. **Founder capacity and decisions.** Unmade decisions, consumption over production, fragmentation of the productive hours. Use the dated evidence; do not moralise.

## Refuters

Each refuter gets one hypothesis, the list of the other candidates for context, and one of these instructions. Default to `refuted: true` when unsure; the point is to make survival mean something.

- **Symptom or not binding.** Show it is a symptom of something upstream (name the cause), or that relieving it within 30 days would not raise throughput because another link binds next (name it).
- **Evidence re-check.** Re-check the key evidence against the live sources (a reply that was sent, a decision already made, a payment already taken, a date misread). Report exactly what was checked.
- **Combined** (for lower-ranked hypotheses): both of the above in one pass.

Return: `hypothesis_id`, `refuted`, `confidence`, `reasoning`, `symptom_of` (if any), `evidence_problems` (if any).

## Delta scan

Most mornings nothing that moves the constraint has happened, and a full rescan is paying to rediscover yesterday. The delta scan reads only what is newer than the cursors in the previous state, with hard caps, and asks one question: did anything material happen?

Brief for the delta agent: "Read only (1) mail newer than 1 day excluding promotions, social and digest senders, plus sent mail newer than 1 day, search results only, opening at most five threads that touch the constraint, an open item, a signal, or a real person the owner must answer; (2) notes to self newer than 1 day; (3) Drive files modified in the last 24 hours, reading at most three that touch the constraint or a signal, and quoting any change to the goal if the running-thoughts document changed; (4) the calendar for yesterday and the next 7 days in one call; (5) commits since the git cursor, subjects only. Return dated observations; each signal marked fired or not, with evidence; whether yesterday's action shows evidence of being done; items resolved and new items with deadlines; the new cursors; and whether the constraint plausibly moved, with the reason."

Material means at least one of: a signal fired; yesterday's action relieved the constraint; a decision was written down (price, offer, direction); money came in or a payment path went live; a deadline passed; the goal changed. One more newsletter, meeting or inbound email is not material.

Not material: write the report from the state plus the delta, keep the slug, increment the day count. Material: one judge-and-refuter agent decides whether the constraint moved, refuting the move first (symptom of the existing constraint? would relieving the new candidate raise throughput within 30 days? does the evidence hold?). Re-baseline with a full scan weekly regardless, because an incremental world model drifts, and sooner if two material days in a row end with confidence under 0.5.

## Choosing

Prefer survivors. Among survivors prefer the most upstream one the refuters' reasoning supports. When nothing survives, read the refutations as votes: the hypothesis the others are called symptoms of is usually the root. Confidence is a number the reader can use, so make it honest: 0.8 when the evidence is direct and recent, 0.6 when it rests on inference from absence, lower when a key source was unreachable.
