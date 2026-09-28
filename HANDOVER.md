# HANDOVER

Living handover document for the autonomous session chain
(see CLAUDE.md, section "Autonomous session protocol").
Update after every completed unit of work and before every handover.

**Last updated:** 2026-09-28 (setup session — protocol files only)
**Chain status:** not started (kickoff pending, see below)

## Kickoff checklist (to be done by the user or a setup session)

The protocol is set up in theory only. Before the first worker session can
start:

1. Create the work plan as GitHub issues (self-contained, one issue = one
   PR) and list their processing order under "Work plan" below.
2. Create the integration branch `integration` from `main` and push it
   (it must contain these protocol files).
3. Create the fallback routine (claude-code-remote `create_trigger`,
   cron `0 6,18 * * *`, `create_new_session_on_fire: true`) with the
   fallback prompt from CLAUDE.md, section "Prompt templates".
4. Start the first worker session with the "Reviewer → worker" template
   for the first issue.

## Work plan

- (no issues yet — fill in `#N — title` in processing order)

## Done

- (nothing yet — protocol files added on 2026-09-28)

## In progress

- (nothing)

## Next step

- Complete the kickoff checklist above.

## Open questions / decisions taken

- External services (Spotify Web API, database) and their
  credentials may not be available in a cloud session. Implement and
  document the code path anyway and record here which steps still need a
  local run for verification.

## Known pitfalls

- Never force-push `integration`.
- Issue PRs target the integration branch, not `main` — GitHub's `Closes #N`
  auto-close does not fire there; the reviewer closes issues manually after
  the merge.
- Every issue PR is merged only by a reviewer session (see CLAUDE.md,
  "Reviewer session"); always record the open PR number and its state
  (review pending / findings open / merged) here.
- Never commit API keys or credentials; use environment variables.
