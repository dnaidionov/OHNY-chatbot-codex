# Global PR Execution Rules (applies to all agents)

1) Start from latest main
- Fetch and checkout latest `main` before making changes.

2) Work on a branch
- Create a new branch named: `agent/<agent-name>/<short-topic>`.

3) PR-only workflow
- Do not push to `main` directly.
- Open a Pull Request for all changes.

4) Respect file write scope
- Modify ONLY files listed under “Write Permissions” in the agent task file.
- If you believe changes outside scope are necessary:
  - Do not make them.
  - Add a PR comment describing the needed change and why.
  - Stop.

5) Keep commits reviewable
- Prefer small, focused commits.
- Do not mix unrelated changes.

6) PR description requirements
Include:
- What changed (bullet list)
- Files changed
- How this meets DoD checklist

7) No silent rewrites
- Do not overwrite non-empty files unless explicitly instructed by the task.

8) If blocked, stop and report
- If required inputs are missing or unclear, stop and ask for the minimum info needed.