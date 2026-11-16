# Feature Delivery State

Use the existing tracker/queue if one already owns this work. This template is for a selected project that needs a new durable handoff, not a second task system.

## Scope and authority
- Project/repo: <verified path>
- Branch/revision and initial worktree state: <actual observations>
- Desired outcome: <user-visible result>
- In scope / non-goals: <approved boundary>
- Protected behavior and paths: <constraints>
- User authorization: <what was actually authorized, with reference>
- Allowed next action: <specific action within that scope>
- Not authorized: <implementation, commit, push, merge, deploy, spend, etc. as applicable>

## Phase and artifacts
- Current phase/status: <actual gate, not desired final state>
- Design/PRD/backlog references: <existing files or tracker IDs>
- Open decisions / feasibility blockers: <unresolved; do not hide as defaults>
- Release: <NOT_REQUESTED, authorization pending, or actual target/status>

## Approved work
| Issue | Usable outcome | Dependencies | Owner | Status | Evidence |
| -- | -- | -- | -- | -- | -- |

Keep proposed follow-up work distinct from approved ready issues.

## Execution limits, if unattended
- Scope and finite budget: <user-approved time/cost/work units>
- Enforced by: <actual mechanism; identify advisory-only limits>
- Concurrency / repair cap: <explicit bounds>
- Usage so far: <measured, or unknown; not fabricated zero>
- Stop/escalation conditions: <failure, budget, material scope change>

## Verification evidence
| Revision | Requirement/check | Exact command or review | Actual result | Evidence location |
| -- | -- | -- | -- | -- |

Separate tests, integration/runtime checks, spec review, and quality/security review. Mark unavailable checks NOT_RUN. Invalidate affected evidence after material edits.

## Human acceptance and release
- Human acceptance: <pending, or actual confirmation of demonstrated version>
- Requested changes: <linked issues, approved or proposed>
- Release authorization and target: <actual permission, not inferred>
- Rollback path: <verified/practical approach when relevant>
- Deployment read-back and monitoring: <actual observations or NOT_RUN>

## Next handoff
- Completed with evidence: <compact summary>
- Remaining blocker: <exact failure and needed input>
- Next allowed action and owner: <do not auto-expand scope>
