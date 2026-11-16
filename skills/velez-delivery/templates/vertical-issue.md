# <Issue ID>: <One Usable Capability>

Status: PROPOSED | READY | IN_PROGRESS | REVIEW_PENDING | VERIFIED | AWAITING_HUMAN_ACCEPTANCE | ACCEPTED

## User outcome
As <user>, I can <complete action/result>, so that <value>.

## End-to-end scope
- Entry point → processing/data → observable result: <full path>
- In scope: <small capability>
- Non-goals: <excluded work>
- Existing behavior/invariants to preserve: <requirements>
- Dependencies: <issue IDs and readiness>
- Approval basis: <actual authorized scope or still proposed>

## Acceptance scenarios
- Given <state>, when <action>, then <observable outcome>.
- Required invalid/missing input, permission, and failure behavior: <observable checks>.

## Implementation checklist
Use tiny steps inside this vertical issue: failing behavior test, verified RED, minimal implementation across needed layers, GREEN, regression checks, and review. Do not turn every layer into its own top-level issue.

- Allowed files/interfaces: <discovered paths or pending repo discovery>
- Exact verification commands: <repo-confirmed commands or pending discovery>
- Runtime/demo check: <actual surface to exercise>
- Test data: <real source or explicitly labeled fixture/synthetic data>

## Review and acceptance
- Spec review of revision: <evidence/pending>
- Quality/security review of revision: <evidence/pending>
- Integration/regression outcome: <actual result/NOT_RUN>
- Human acceptance: <actual confirmation/pending>
- Remaining blockers: <specific unresolved items>

Issue completion does not authorize commit, merge, publication, or deployment. Record release authority separately.
