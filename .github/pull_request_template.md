## Summary
Describe what this PR changes (2–5 bullets).

## Phase / Gate
- [ ] Scaffolding / Process
- [ ] Gate 1 (Product Architecture)
- [ ] Gate 2 (Intelligence + Interface)
- [ ] Implementation
- [ ] Hardening (QA/Security/Ops)
- [ ] Case Study

## Scope Discipline
- [ ] Files changed are within this agent/task’s declared **Write Permissions**
- [ ] No unrelated refactors or drive-by edits

## DoD Checklist
Link to the agent task file, then check off the DoD items here:

Task file: `/agents/<task-file>.md`

- [ ] DoD item 1
- [ ] DoD item 2
- [ ] DoD item 3

## Safety & Privacy
- [ ] No secrets/API keys in client/browser code
- [ ] No PII logged in plaintext (name/email/phone/zip)
- [ ] localStorage PII is only stored with explicit user consent (where applicable)

## Performance & Reliability (esp. check-in)
- [ ] Check-in path has strict upstream timeout
- [ ] Rate limiting behavior exists (baseline OK)
- [ ] Check-in path does **not** depend on LLM output for site resolution

## Testing / Verification
- [ ] CI passed
- [ ] Evals/tests run locally or in CI (details below)

### Test notes
Paste commands run or link to CI run:
- `...`

## Notes / Follow-ups
List any known gaps and follow-up tasks/issues.