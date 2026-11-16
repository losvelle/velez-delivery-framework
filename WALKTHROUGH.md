# Velez Delivery Framework: Idea-to-Production Walkthrough

**Introduced and adapted by Carlos Velez.**

## What this is

This is an illustrative, synthetic pipeline, not a built app, a deployment result, or permission to handle protected data. Issue IDs, decisions, and prompts below are examples. No application tests, reviews, organization approvals, or releases described here have actually occurred.

The app: a small internal team request tracker. A requester submits a generic request, an authorized reviewer approves or rejects it, and the requester sees the outcome and history. Use invented users and dummy request text while learning the workflow. A real organization's approval, identity, data, and release rules must be discovered inside its approved environment.

This package uses `/velez-delivery` in Copilot. Select the account and model approved for your project. Personal installation and the optional Delivery Planner and Delivery Reviewer roles are described in [README.md](README.md). Use [/velez-recipes](skills/velez-recipes/SKILL.md) for optional companion prompts at each phase.

## 0. Set the working contract

Start in an approved repository or a dummy project. Do not send protected repository content to a personal assistant or machine. Use the normal organizational change process.

Copy/paste prompt:

> /velez-delivery I have an idea for a team request tracker. Start with discovery and planning only. Use invented sample data. Read the approved project guidance and relevant existing code before recommending changes. Do not write production code, install tools, commit, push, create external tickets, merge, or deploy. Identify the current phase, facts, unknowns, and approvals needed.

The agent should inspect facts it can discover, not ask you to retype them. It should establish the approved stack, available tests, identity integration, persistence, deployment path, and existing tracker. If an unknown blocks implementation, record it rather than guessing.

Gate: the assistant understands both the problem and its current authority. For a small feature, reuse an existing requirements note and tracker instead of making unnecessary documents.

## 1. Research feasibility, then grill the consequential decisions

Use Delivery Planner if approved, or keep the normal agent in an explicitly read-only/discovery scope.

Prompt:

> Stress-test the idea before designing it. Investigate existing capabilities and the riskiest integration assumptions. Ask one consequential design decision at a time, recommend an answer, and wait. Resolve the first user journey, access rules, failure behavior, and non-goals. Keep unverified integrations explicitly unverified. Do not repeat questions already answered by the code or an approved brief.

Possible questions, asked as separate dependent turns rather than a survey:
- Who must use the first release: one internal team or external customers?
- Can requesters see only their own requests, or a shared queue?
- Who is allowed to approve/reject, and can anyone approve their own request?
- What happens when persistence or identity is unavailable?
- Which evidence demonstrates that the workflow is better than the current workaround?

An example settled scope, only after the human actually approves it:
- Internal requester and reviewer roles using approved identity.
- Requesters see only their own request records.
- Authorized reviewers see the queue and may decide a request; self-approval is prohibited in this example.
- The initial states are Submitted, Approved, and Rejected.
- A successful decision and its audit event persist together; failure must not silently apply half the change.
- No attachments, external email, AI-generated approvals, public signup, or billing in the MVP.

Feasibility gate: demonstrate risky integrations in an authorized non-production environment or leave them blocked. A mock identity adapter can support clearly labeled local development, but it does not prove real identity integration or authorize a production release.

## 2. Write and approve the PRD

Prompt:

> Turn the confirmed decisions into a concise PRD. Include the problem, users, user stories, MVP scope, non-goals, invariants, failure behavior, acceptance scenarios, and definition of done. Separate confirmed decisions from proposed assumptions. Suggest small stable module boundaries. Do not generate code or invent test commands. Return the draft in chat first.

Example acceptance criteria to approve, adapt, or reject:
- An authenticated requester can submit valid input and see a persistent confirmation.
- Invalid input is rejected without creating a record.
- Requester A cannot retrieve requester B's record by changing a URL or request identifier; access checks are server-side.
- A reviewer can decide only an eligible request; a conflicting concurrent decision does not overwrite another outcome silently.
- The outcome and audit event are consistent, and audit records do not contain credentials or unnecessary sensitive content.
- A storage failure does not display a false success state.
- A mock identity or development bypass cannot remain active in a production configuration.

Deep-module guidance: keep authorization, valid state transitions, and transactional invariants behind a small domain/service interface. Keep identity and storage adapters replaceable without scattering these rules through page handlers. This is a conceptual design direction, not a claim that any particular class or interface already exists in a repository.

Approval prompt after your review:

> I approve this PRD version, including the stated non-goals. You may save the approved requirements and delivery state in this project's established docs location. This approval covers documentation only, not implementation or deployment.

Gate: the destination and definition of done are explicit. Important unresolved requirements remain blockers.

## 3. Create a vertical backlog

Prompt:

> Slice the approved PRD into small end-to-end issues. Each issue must produce a demonstrable user outcome, list dependencies and non-goals, include required security/failure behavior, and specify verification. Put database/API/UI work inside each issue's implementation checklist. Mark issues proposed until I approve them. Use the existing issue tracker; prepare drafts only unless ticket creation is authorized.

Illustrative backlog:

| Example issue | Usable end-to-end result | Dependency | Important acceptance |
| -- | -- | -- | -- |
| REQ-01 | An authenticated requester submits a request and sees their own saved confirmation | Approved identity/persistence design | Validation, server-side ownership, persistence, invalid input, storage failure |
| REQ-02 | An authorized reviewer sees eligible requests and approves or rejects one | REQ-01 | Role enforcement, no self-approval, allowed transitions, concurrency protection, atomic outcome/audit persistence |
| REQ-03 | A requester sees their own current status and decision history | REQ-02 | No cross-user record access, accurate status/history, safe error and empty states |
| REQ-04 | A reviewer finds a particular pending request using the approved queue filters | REQ-02 | Scoped results, correct filtering, no authorization leakage, appropriate data volume checks |

These are proposed illustrative IDs, not tickets created in a real system. Approve only necessary MVP capabilities; REQ-04 can remain out of scope if it is not needed.

Production-readiness concerns are acceptance obligations across the appropriate slices and release gate. Do not defer essential authorization to a final security ticket after exposing real users.

Gate: the next issue is approved, dependency-ready, and has repository-confirmed commands and allowed paths. If no repository is selected, those details remain pending discovery.

## 4. Authorize one bounded implementation slice

Use the normal approved implementation agent, not a read-only role.

Prompt:

> Implement only approved issue REQ-01 in this repository. Confirm the current branch, worktree, applicable instructions, exact test commands, and allowed files before editing. Use test-first development: show the intended failing behavior, implement minimally, then run affected tests and regressions. Preserve unrelated work. Use one implementer and no more than two fix-and-reverify cycles. Stop when the slice is implemented and ready for independent review, or when blocked. No new infrastructure, scope expansion, commits, pushes, merges, or deployment are authorized.

The agent must produce actual evidence, not plausible output:
1. A test that fails for the intended missing behavior, not a setup typo.
2. The minimum end-to-end change.
3. The same test passing, then relevant regressions.
4. A real runtime check of the submission and confirmation path.
5. A concise changed-files summary, revision/worktree identity, and outstanding limitations.

The exact commands depend on the inspected repository. This guide intentionally does not invent pytest/npm/build commands for a project that has not been selected.

Status: IMPLEMENTED / REVIEW_PENDING. Passing tests do not mean accepted or released.

For a batch, explicitly name the approved issues, resource/work-unit bounds, permitted tools, repair budget, and stop conditions. Do not ask it to invent work forever. If the tool cannot enforce a hard time/spend ceiling or survive restarts, do not represent a chat instruction as such a guarantee.

## 5. Independently review the exact change

Start a NEW approved chat/context with Delivery Reviewer, an approved independent agent, or a human reviewer. Switching the name of the agent in the implementation conversation is not sufficient separation.

Prompt:

> Review this exact revision/worktree change against the approved REQ-01 issue and PRD. Review spec compliance first, then code quality/security and integration evidence. Inspect the actual diff, relevant files, and existing test logs. Do not change code. Separate evidence you inspected from checks you did not execute. Return blocking findings, nonblocking suggestions, and an explicit verdict bound to the reviewed version. Do not mark human acceptance or authorize release.

Supply the original requirements, exact diff/revision, relevant files, and actual CI/test evidence. Do not provide only the implementer's reassuring summary.

If findings exist, return them to the implementer within the approved repair cap. Re-run affected checks and obtain fresh review after material changes. If a required independent reviewer is unavailable, the issue remains REVIEW_PENDING.

Repeat the bounded implementation/review cycle for each approved dependency-ready slice. End with integration checks over the combined app, not just isolated issue tests.

## 6. Prepare a reviewed release candidate and staging handoff

After independent verification, use your actual approved branch/PR/CI process. Local coding permission did not automatically authorize commits, pushes, tickets, or staging.

Example explicit authorization when appropriate:

> The reviewed changes may be committed and submitted through our approved PR process for the named branch and reviewers. Do not merge or deploy until the required approvals and CI gates pass. Preserve the exact reviewed artifact and record any later changes for renewed verification.

Then prepare release evidence:
- Requirements-to-test mapping and current independent review findings.
- Actual CI, type/lint, security/dependency/secret scan results required by the organization. Do not invent tools or counts.
- Real identity/permission integration checks, not only local mocks.
- Configuration/secrets handling and supported data/retention rules.
- Accessibility/performance/reliability checks against approved targets, not arbitrary fabricated thresholds.
- Migration compatibility, backup/recovery procedure, and a tested practical rollback approach.
- Staging target, exact artifact/version, operational owner, and proposed observation signals.

Staging authorization prompt:

> I authorize deployment of this exact approved candidate to the approved staging target through the existing delivery pipeline, subject to required organization approvals. This is staging permission only. Verify the actual deployed version and the agreed smoke/permission checks. Do not deploy to production.

A person without the required authority cannot grant it by pasting this prompt. If credentials or environment access are unavailable, produce the handoff packet and mark deployment NOT_RUN; do not claim success.

## 7. Human acceptance in staging

Prompt:

> Prepare a UAT walkthrough for the deployed candidate against the approved acceptance scenarios. Use permitted dummy/test accounts and data. Include positive, failure, and cross-role cases. Report what is demonstrated, what is not tested, and any remaining blocker. Wait for my acceptance or changes.

The human or designated stakeholder should actually walk through:
- Submit and reopen a request.
- Verify an unauthorized user cannot access another request directly.
- Review/decide with the correct role; reject self-approval where required.
- Confirm state/history and audit consistency.
- Check authorized failure handling, without injecting failures into a live service without permission.

Explicit acceptance after the walkthrough:

> I accept this demonstrated candidate against the listed criteria. Record acceptance of this exact version. Production release remains unauthorized until our release/change process approves it.

Status: ACCEPTED, not RELEASED. Material new edits can invalidate test/review/acceptance evidence and must be reassessed.

## 8. Authorize and perform the production release

Use the organization's real change/release/security process. The skill cannot replace required approvals or security authorization.

Prompt only when you actually hold the relevant authority:

> The required release approvals are complete. I authorize the named approved artifact/version to the approved production target through our existing pipeline, within the approved change window and rollout scope. Confirm the rollback/recovery plan, migration compatibility, owner, observation checks, and abort criteria before executing. Do not change unrelated infrastructure or bypass a failed gate. Read back the actual version and smoke-check the deployed outcome.

Keep exact target/version/change references inside the approved environment. Do not assume an application rollback safely reverses a database migration. Destructive data restoration needs its own authorized procedure and owner.

Gate: the pipeline succeeded AND read-back confirms the intended version and behavior. A tool returning success or an artifact being uploaded is not enough.

## 9. Monitor, close, and iterate

Prompt:

> Verify the agreed post-release signals and business-critical journeys over the approved observation window. Report actual observations and any monitoring gaps. If abort criteria are met, use only the approved recovery procedure or escalate to the owner. Propose follow-up issues separately; do not expand implementation authority.

Relevant signals for this example may include request-write failures, error rate, permission-denial anomalies, decision/audit consistency, and the primary submit/review/status user journeys. Use approved thresholds, systems, and retention rules. Do not invent telemetry or claim continuous monitoring when no monitoring process is running.

Close the delivery record with the released version, actual verification/review/acceptance evidence, operational ownership, known limitations, recovery references, and proposed follow-ups.

## Suggested artifact arrangement, not a required repo layout

Prefer existing conventions and trackers. If none exists, a compact arrangement could be:
- One PRD/design note with decisions and acceptance criteria.
- Existing issue tracker with approved vertical issues.
- One delivery-state record linking current status, evidence, and authority.
- A release runbook with rollout/recovery/monitoring and operational owner.

The skill package includes issue/state templates, not a competing queue or automatic ticket publisher.

## For an existing feature rather than a new app

Start from the current repository, approved requirements, and next relevant phase. Inspect existing behavior, add regression coverage, reuse the established architecture and delivery pipeline, and grill only material unanswered choices. A small feature still needs an observable outcome, bounded edits, verification, appropriate review, human acceptance, and the authorized release path; it does not need to rebuild the whole process from zero.

## The short version

You supply intent and approvals. The agent investigates, specifies, slices, implements within limits, and produces evidence. Independent reviewers test the claim. Humans accept the result. Only the organization's authorized release path gets it into production.
