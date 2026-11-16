---
name: velez-delivery
description: Velez Delivery Framework (VDF). Guide an idea or feature through discovery, a PRD, vertical issues, bounded test-first implementation, independent review, human acceptance, and explicitly authorized release. Use when the user requests a controlled end-to-end delivery workflow.
argument-hint: "[idea or feature, plus the phase you authorize]"
user-invocable: true
disable-model-invocation: true
license: MIT
---

# Velez Delivery Framework (VDF)

Human-directed AI delivery, from idea to production.

**Introduced and adapted by Carlos Velez.**

Humans own intent and acceptance; agents own bounded implementation.

**Research → clarify → specify → slice → implement → independently verify → human accept → authorized release.**

This skill is self-contained. It does not require other skills, a specific model, external services, or automatic delegation. Invoke it manually and keep the coordinating conversation inline.

## 1. Establish scope, policy, and state

- Follow organization policy, repository instructions, data-handling rules, and the user's actual authorization. Approval of this skill is not approval of every model, repository, command, data class, or deployment.
- Work only in the approved assistant, account, model, repository, and environment. Do not transmit protected material to personal accounts or unapproved endpoints. Do not propose bypassing blocked extensions, transfer controls, or missing permissions.
- Read existing project guidance, design, tracker/queue, relevant code, manifests, tests, and git state using available approved tools. Do not read secrets or disturb unrelated work.
- Reuse one authoritative tracker. If persistent work needs a new record, adapt the [delivery-state template](templates/delivery-state.md) in the selected project's established documentation location. A small change may use a single compact note rather than several documents.
- Record the current phase, scope, constraints, evidence, approvals, and next allowed action. Discovery, documentation edits, code edits, commits, pushes, merges, staging, production release, and infrastructure changes are separate scopes unless the user's request and organization policy explicitly authorize them together.

## 2. Research and clarify

Inspect facts before asking for them. Identify risky assumptions and perform only authorized, bounded feasibility experiments. Clearly label mocks, synthetic data, throwaway code, unknowns, and untested integrations.

For consequential unresolved design choices, interview the user until there is shared understanding. Follow the decision tree in dependency order. Ask one focused decision at a time, give a recommended answer and short rationale, and wait. Do not combine audience and workflow decisions into one compound question or repeat a settled question. Stop when asked.

Resolve the desired outcome, user journey, constraints, non-goals, tradeoffs, failure behavior, and existing behavior to preserve. If an approved brief already settles them, do not restart the interview. Material unknowns remain blockers, not silent assumptions.

## 3. Specify the destination

Prepare a PRD or equivalent approved requirements note covering the user problem, stories, in-scope outcomes, exclusions, data and permission rules, failure behavior, observable acceptance, and definition of done. Separate confirmed requirements from proposed assumptions.

Do not choose a new stack or infrastructure without checking approved project constraints. A skill invocation or an agreed design alone does not authorize implementation. Reuse explicit approval already provided; do not ask repeatedly for it.

## 4. Slice into usable outcomes

Use the [vertical-issue template](templates/vertical-issue.md). Each issue delivers one small end-to-end capability across the needed UI, service, data, and verification layers. Database/API/UI work is an internal checklist, not the default top-level backlog.

Each ready issue needs a user-visible outcome, dependencies, non-goals, invariants, acceptance scenarios, allowed edits, and repository-confirmed verification commands. If no repo is selected, mark paths and commands pending discovery rather than inventing them. Keep proposed, approved, ready, and dependency-blocked issues distinct.

Every slice includes the validation, authorization, and failure behavior needed to make it safe. Do not defer essential access controls until after a slice is exposed to real users.

## 5. Implement within explicit bounds

- Implement only approved ready issues. Default to one implementer at a time and at most two fix-and-reverify cycles per failed issue unless different limits are explicitly set.
- Write a behavioral test first, run it and observe the intended failure, make the minimum implementation, observe it pass, and run relevant regression checks. A broken test environment is not a valid RED. Do not weaken acceptance tests to manufacture GREEN. Obtain an explicit exception before treating throwaway prototypes or non-code changes differently.
- Prefer small stable interfaces that hide meaningful complexity. Keep access rules and invariants behind clear module boundaries; do not scatter them through UI callbacks or add speculative wrappers. Preserve protected existing behavior and avoid unrelated refactors.
- Record actual commands, results, and the exact revision tested. Unavailable required checks stay NOT_RUN; they are not passes.
- For unattended work, first establish finite approved scope, enforceable resource/work-unit bounds, concurrency, retry limits, permitted commands, durable state, and stop conditions. Count fixes and reviews within the same allowance. Do not promise hard caps or restart durability that the tools cannot enforce.
- Do not create background services, install new tools, add paid services, change permissions, commit, push, merge, or deploy without the relevant authorization. Do not expand the backlog automatically.

## 6. Independently verify

Spec compliance comes first, then code quality/security, then integrated/runtime evidence. Review the original requirements and exact changed revision, not just the implementer's narrative.

Use a separate approved reviewer context or a human reviewer. If approved subagents are unavailable, a new chat using the same approved model can perform AI review when given the requirements, exact revision, diff, and actual test evidence. Switching roles inside the implementation conversation is not fresh-context independent review. AI review does not replace required human or organizational review.

If no independent reviewer is available, leave REVIEW_PENDING or BLOCKED; never substitute implementer self-review silently. Address findings within the repair limit, rerun affected checks, and re-review material changes. Earlier approval does not cover unreviewed edits. Never invent tests, test logs, model availability, or reviewer results.

## 7. Human acceptance

Demonstrate the result against the agreed acceptance scenarios in an approved environment. Include consequential unhappy paths and permission boundaries. Present what actually ran, limitations, open findings, and the next decision.

Passing tests and AI review mean VERIFIED, not ACCEPTED. Only actual human acceptance of the demonstrated version can satisfy that gate, alongside any required organizational signoffs. New feedback becomes proposed work or a regression issue; do not silently enlarge the approved scope.

## 8. Release and monitor only when authorized

Require the organization's applicable approvals, explicit target/environment and artifact, a practical rollback/recovery plan, migration compatibility, agreed observation signals, and an operational owner. Staging permission is not production permission. One person's acceptance cannot waive organization controls.

Use the existing approved delivery pipeline. Read back the deployed version and verify real health, user-journey, and permission behavior. Monitor agreed signals and use only the approved recovery procedure if criteria fail. Do not assume application rollback reverses data migrations safely.

If deployment or environment access is unavailable, prepare a release packet and record the handoff; do not claim it shipped. If release is outside scope, record NOT_REQUESTED.

## Completion and resumption

Distinguish IMPLEMENTED, REVIEW_PENDING, VERIFIED, AWAITING_HUMAN_ACCEPTANCE, ACCEPTED, and RELEASED. Persist status/evidence in the authoritative project tracker; resume from it rather than relying on chat memory. Recheck changed facts and permissions after a handoff.

Stop at the authorized boundary. Report the artifact, actual checks and results, independent review, outstanding approvals, and exact next allowed action. Do not claim an app is production-ready merely because a local demo works.

For non-sensitive installation and behavior checks, read the [acceptance checks](references/acceptance-checks.md). These instructions guide behavior; they are not a security sandbox or a promise of identical output across models.
