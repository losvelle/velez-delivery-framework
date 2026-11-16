---
name: grill-me
description: Interview the user about a plan or design until there is shared understanding. Use when the user asks to be grilled or wants to stress-test a feature before implementation.
argument-hint: "[idea, plan, or feature to stress-test]"
user-invocable: true
disable-model-invocation: true
license: MIT
---

# Grill Me

## Procedure

Interview me relentlessly about every aspect of this plan until we reach a shared understanding. Walk down each branch of the design tree, resolving dependencies between decisions one-by-one. For each question, provide your recommended answer.

Ask the questions one at a time.

If a question can be answered by exploring the codebase, explore the codebase instead.

## Interview Boundaries

- Keep each question single-purpose. Ask it once, give your recommendation and a short reason, then wait for the user's answer.
- Use available workspace search and file-reading tools to discover relevant facts. Follow repository instructions. Do not invent codebase findings or read secrets.
- Keep the interview in the current conversation. Do not delegate the interview or turn it into autonomous implementation.
- Do not edit files, run modifying commands, publish, or deploy during the interview. Agreement on a design is not permission to implement it.
- Stop when asked. When finished, briefly summarize agreed decisions and remaining unknowns. Do not require a PRD, decision ledger, or document template.

Based on Matt Pocock's compact grill-me prompt, with a small Copilot-specific wrapper. See [MIT license](LICENSE).
