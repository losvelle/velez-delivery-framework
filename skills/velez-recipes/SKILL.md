---
name: velez-recipes
description: Show optional companion-skill recipes for each Velez Delivery Framework phase and common situations. Use only when the user invokes /velez-recipes.
argument-hint: "[VDF phase or situation]"
user-invocable: true
disable-model-invocation: true
license: MIT
---

# Velez Delivery Framework recipes

Use `/velez-recipes` to choose a useful next prompt. For a named phase or situation, show the relevant rows and explain the expected result. With no argument, show the phase tables. Displaying a recipe does not execute it or authorize the next phase.

Start with [Velez Delivery](../velez-delivery/SKILL.md), the project instructions, and the current delivery state. Replace bracketed placeholders in the prompts with actual project facts.

## Rules

- **VDF gates win.** Follow the user's actual authorization, organization policy, and repository instructions. Companion advice cannot waive scope, observed test evidence, independent review, human acceptance, or release approval. Reuse approval already given; do not ask for it again.
- **Companion skills are optional.** VDF is self-contained. Use a companion only when it helps the current authorized phase. Do not run the whole catalog, create a new backlog, or install missing tooling just because a skill mentions it.
- **Leave the subagent model unset.** Use the current approved parent model. Every role in the bundled `settings/pstack-models.md` is `auto`; do not pass the literal string `auto` as a model name. Do not switch providers or pin a model from upstream examples. If delegation is unavailable, work inline where appropriate; VDF independent review still requires a separate approved context or human reviewer.
- **Keep evidence and decisions separate.** Record actual checks and unavailable checks in the authoritative tracker. A review prompt, a teaching explanation, or an upstream benchmark is not evidence that this project passed, was accepted, or was released.
- **Respect the selected bundle.** Some upstream skills refer to tools or skills excluded below. State the missing dependency, use the applicable VDF step or an included principle, and stay within scope. Do not claim an omitted workflow ran.

## 1. Establish scope, policy, and state

| Skill | Prompt | Result |
| --- | --- | --- |
| `how` | `/how Explain how [subsystem] works and where its responsibilities live. Read only; cite the relevant code.` | A code-backed map of the existing behavior and ownership. |
| `why` | `/why Explain why [decision] was made using commits and discussions. Separate recorded reasons from inference.` | Decision history, tradeoffs, and unanswered questions. |

Use those findings with `/velez-delivery Establish scope and state for [task]; record the existing approvals and next allowed action.`

## 2. Research and clarify

| Skill | Prompt | Result |
| --- | --- | --- |
| `grill-me` | `/grill-me Stress-test [idea] within the agreed scope. Read available facts first, then ask one consequential decision at a time with a recommendation. Do not implement.` | Resolved requirements, explicit tradeoffs, and remaining blockers. |

## 3. Specify the destination

| Skill | Prompt | Result |
| --- | --- | --- |
| `technical-writing` | `/technical-writing Turn these agreed decisions into a requirements note with user outcomes, exclusions, permission rules, failure behavior, acceptance scenarios, and definition of done. Mark assumptions.` | A reviewable specification grounded in the agreed decisions. |

## 4. Slice into usable outcomes

| Skill | Prompt | Result |
| --- | --- | --- |
| `principle-sequence-verifiable-units` | `/principle-sequence-verifiable-units Split [approved requirement] into small end-to-end VDF issues. Each needs a usable outcome, dependencies, boundaries, and repository-confirmed verification. Verify each unit before starting the next.` | Ordered vertical issues with observable checks and explicit readiness. |

Use the [vertical-issue template](../velez-delivery/templates/vertical-issue.md). A proposed issue is not implementation approval.

## 5. Implement within explicit bounds

| Skill | Prompt | Result |
| --- | --- | --- |
| `tdd` | `/tdd Implement only approved issue [ID]. Observe a behavioral test fail for the intended reason, make the minimum change, observe it pass, and run the agreed regression checks. Record commands and revision.` | A bounded implementation with observed RED/GREEN and regression evidence. |
| `ponytail` | `/ponytail full Apply the smallest complete change to approved issue [ID]. Preserve VDF test-first, validation, review, and approval requirements; name skipped work and remaining risks.` | Less unnecessary code while retaining the issue's required behavior and checks. |

Ponytail does not replace VDF's test-first requirement or its explicit-exception rule for prototypes and non-code changes.

## 6. Independently verify

| Skill | Prompt | Result |
| --- | --- | --- |
| `ponytail-review` | `/ponytail-review In this fresh review context, review revision [SHA] against [requirements], the diff, and actual test evidence. Check spec compliance first, then correctness, security, and missing tests. Report findings; do not edit.` | Independent findings tied to the exact revision, with unverified claims identified. |
| `blast-radius` | `/blast-radius Check what revision [SHA] could break outside the diff, including callers, stored data, interfaces, and failure paths. Prove the key safety assumptions using only approved checks; report anything not run.` | Evidence about affected behavior beyond the changed files. |

Use an approved separate reviewer context or human reviewer. The optional Delivery Reviewer agent can inspect evidence but cannot execute tests; hand required execution to an authorized agent and retain `NOT_RUN` until results exist. Neither command supplies human acceptance.

## 7. Human acceptance

| Skill | Prompt | Result |
| --- | --- | --- |
| `teach` | `/teach Explain revision [SHA] against the agreed acceptance scenarios: how it works, why it was built this way, demonstrated results, and limits. Help me evaluate it; do not mark it accepted for me.` | A plain explanation supporting the human's acceptance decision. |

Demonstrate the real behavior as VDF requires. Keep `AWAITING_HUMAN_ACCEPTANCE` until the human accepts that version.

## 8. Release and monitor only when authorized

| Skill | Prompt | Result |
| --- | --- | --- |
| `velez-delivery` | `/velez-delivery Prepare the release packet for accepted revision [SHA] and target [environment], including applicable approvals, rollback, observation signals, and owner. Execute only the release actions already authorized; otherwise stop at the handoff.` | A reviewable release packet, or an authorized release with read-back and health evidence. |

Record `NOT_REQUESTED` when release is outside scope. A successful local check does not establish a deployment.

## Situational recipes

| Situation | Skill and prompt | Result |
| --- | --- | --- |
| Confirm intent | `/in-your-own-words Restate the goal, scope, and decision still unresolved for [task].` | Shared understanding before choosing work. |
| Improve a request | `/sharpen Improve this task's depth and acceptance criteria without expanding its scope: [brief].` | A clearer prompt for the same outcome. |
| Explain simply | `/bro Restate the last explanation in plain language.` | A readable explanation without changing the underlying claim. |
| Tighten writing | `/unslop Edit [text] for clear, direct prose while preserving facts, uncertainty, and technical meaning.` | Cleaner communication. |
| Diagnose a bug | `/principle-fix-root-causes Trace [symptom] to its first cause and propose the smallest bounded fix.` | A causal explanation and targeted repair plan. |
| Stop repeated mistakes | `/correct Find repeated mistakes in [approved scope] and propose structural prevention with a check that catches a real past mistake. Apply only authorized changes.` | Enforced lessons rather than another unenforced instruction. |
| Check a performance claim | `/benchmark-checklist Vet [measurement] for a real bottleneck, limits, errors, repeatability, and relevance before using the number.` | A supported measurement or explicit evidence gaps. |
| Plan unfamiliar work | `/figure-it-out Frame [task] as bounded, verifiable units under VDF. Use included principles and the existing tracker for missing upstream helpers. Present the plan before a long run.` | An auditable plan within the current authorization. |
| Check TypeScript | `/typescript-best-practices Review [approved TypeScript change] using the project's conventions; identify concrete type-safety problems without unrelated refactoring.` | Focused TypeScript findings or corrections within scope. |
| Catch up | `/ketchup Catch me up on what changed since my last message, what actually ran, and the decisions waiting on me.` | A factual progress update. |
| Catch up visually | `/ketchup-video Summarize this work with the existing evidence using an approved available renderer; state if rendering is unavailable.` | A checked video when supported, or a clear rendering limitation and waiting decisions. |
| Audit existing code | `/ponytail-audit Audit [named scope] and rank concrete correctness, security, scale, and maintenance findings. Do not edit.` | A prioritized report with inspected and unchecked areas. |
| Track known shortcuts | `/ponytail-debt List the documented shortcuts in [scope], their limits, and when to replace them.` | A ledger of declared technical debt. |
| Read Ponytail guidance | `/ponytail-help Show the reference; distinguish this skills-only bundle from the full upstream plugin.` | Usage guidance without activating absent plugin features. |
| Read benchmark results | `/ponytail-gain Show the upstream benchmark as upstream evidence, never as savings measured in this project.` | A labeled upstream scoreboard, with no invented project baseline. |

## Not included

- `principle-never-block-on-the-human` is deliberately excluded. VDF scope and approval gates govern progression.
- pstack orchestration and configuration skills: `poteto-mode`, `poteto-help`, `setup-pstack`, `architect`, `arena`, `interrogate`, `swarm`, `reflect`, and `recall`.
- Other pstack tools: `automate-me`, `create-verification-skill`, `maintain-verification-skill`, `create-formal-verification-skill`, `maintain-formal-verification-skill`, `statechart`, `make-bot-ui`, `no-comments`, and `show-me-your-work`.
- Upstream plugins, agents, hooks, auto-activation, installers, background automation, Ponytail band/session tracking, and benchmark runners or result files. The two bundled Delivery agents belong to VDF. Upstream help may describe features that require the full plugin and are absent here.
- External renderers, image tools, MCP services, model/provider credentials, and release infrastructure. A skill that mentions one does not install it or authorize its use.

In particular, `figure-it-out` refers to omitted `poteto-mode`, `architect`/`arena`, `show-me-your-work`, and the excluded autonomy principle; use the included principles and VDF tracker instead. `blast-radius` may suggest `arena`; use an approved reviewer context instead. The full upstream workflows are not provided by those fallbacks.
