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

## Choosing

Prefer survivors. Among survivors prefer the most upstream one the refuters' reasoning supports. When nothing survives, read the refutations as votes: the hypothesis the others are called symptoms of is usually the root. Confidence is a number the reader can use, so make it honest: 0.8 when the evidence is direct and recent, 0.6 when it rests on inference from absence, lower when a key source was unreachable.
