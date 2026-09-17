# Scheduling the scan

The scan is most useful as a routine that fires before the owner's day starts. Two ways to run it on a schedule.

## Claude Code routines (recommended)

1. Create the routine from the Routines page in claude.ai (or with the `create_trigger` tool from a Claude Code session).
2. Prompt: a short instruction such as "Run the constraint-scan skill in Scan mode for the business described in the config, and send the report." Include the full pipeline inline if the fresh session may not have this skill installed.
3. Connectors: tick Gmail, Google Calendar and Google Drive. A routine created from inside a session on some accounts cannot carry connector grants into a fresh session; if the tool warns that the routine "stores no MCP connectors", either create it from the Routines page instead, or bind it to the session that holds the connectors (a session-bound routine works, but that session must not be archived).
4. Cron is evaluated in UTC. Pick the hour so the report lands before the owner wakes, allowing 40 to 90 minutes for the run. Daylight saving shifts the local time by an hour twice a year; note it in the config or adjust the cron when clocks change.

## Idempotency and continuity

Every run searches Gmail for the subject prefix before doing anything. A report already sent today means stop. The previous report's `CONSTRAINT-KEY` footer and "Today's one action" are read so the new report can say "same constraint, day 3" and whether yesterday's action got done. No database is needed; the inbox is the log.

## Testing without sending

Fire the routine (or run the skill) with the extra message `TEST MODE`. The scan runs end to end and saves a Gmail draft prefixed `[TEST] ` instead of sending.

## Capacity

Remote environments often allow only two sub-agents at once. The pipeline is sized for that (six sweeps, four judges, up to eight refuters, one synthesis, one critic). Usage limits can interrupt a run; the Workflow-tool script in `scripts/` resumes from cache so the sweep does not have to be paid for twice.
