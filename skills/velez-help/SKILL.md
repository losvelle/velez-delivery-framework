---
name: velez-help
description: Explain the skills in this package in simple everyday English, with examples for people who do not write code. Use when the user invokes /velez-help to browse skills, understand a named skill, compare skills, or find one for a task.
argument-hint: "[skill name, question, or all]"
user-invocable: true
disable-model-invocation: true
license: MIT
---

# Velez help

Explain what the skills do so someone who has never written code can choose one. A skill is a set of instructions that tells the assistant how to help with a particular job.

## Answer the request

- `/velez-help` or `/velez-help all`: show the complete guide below, grouped by purpose. Keep one short explanation and one everyday example for every skill, including this one. Do not ask the reader to choose a category before showing the guide.
- `/velez-help ponytail-review` or a name with a leading slash: explain that skill, when to use it, what the reader gets back, and one example they can paste into chat.
- A question such as `/velez-help I have an app idea but don't know where to start`: recommend the most useful skill, explain why, and give a ready-to-paste prompt. Mention another only if it helps resolve a real choice.
- A comparison such as `/velez-help how vs why`: explain the difference using the same everyday example for both.
- If a name is missing or unclear, say so and offer the closest matching bundled skills. Do not invent a command.

Read the named skill's `SKILL.md` before giving detailed advice. Use the guide below for browsing. When the package's skill folders are available, check them for additions or removals so the full guide covers the current package. After personal installation, these are sibling folders beside `velez-help`. If files are unavailable, explain from this guide and say you could not check the installed version.

Explain instructions as reference material. Do not run the skills being described, change files, install tools, or start other workers as part of help. A reader asking what a skill does is asking for an explanation. Follow [VDF's](../velez-delivery/SKILL.md) approval rules for any later work.

## Use everyday language

Use short sentences and familiar words. Keep exact skill names so the reader can find them, but explain their meaning without requiring coding knowledge. For example, say "check that the app saves your changes" instead of "validate persistence." Explain an unavoidable technical term when you first use it. Avoid unexplained abbreviations and promises that a skill will prevent every mistake.

For a single skill, a useful answer looks like this:

> **ponytail-review** checks a recent change for problems before you rely on it.
>
> Use it after the assistant changes something. You get a list of problems it found and anything it could not check.
>
> Try: `/ponytail-review Check the changes to my sign-up form. Explain any problems in simple English. Do not edit anything.`

Examples illustrate possible uses, not work that has already happened. Keep important limits clear in ordinary language:

- Help explains the choices. [Recipes](../velez-recipes/SKILL.md) gives example requests for each stage of a project. [Delivery](../velez-delivery/SKILL.md) guides the project itself.
- A "principle" is a focused working habit for the assistant. You can ask for it when that habit would help; you do not need to use every principle.
- A review of a recent change and a review of a whole project cover different amounts of work. Neither automatically approves a public launch.
- Some skills mention extra tools that this package does not include. Explain the missing tool when relevant. See the [excluded items](../velez-recipes/SKILL.md#not-included).
- `ponytail-gain` shows results reported by Ponytail's creators. It does not measure time or money saved on the reader's project. Video output needs an available video-making tool.

## Plan the work

| Skill | In everyday English | Example of when it helps |
| --- | --- | --- |
| [velez-help](SKILL.md) | Explains these skills and helps you choose one. | "Which skill helps me check whether my app is ready?" |
| [velez-delivery](../velez-delivery/SKILL.md) | Guides a project from an idea through building, checking, your acceptance, and an approved launch. | "Help me plan and build a booking app, one approved step at a time." |
| [velez-recipes](../velez-recipes/SKILL.md) | Gives example requests you can copy for each stage of your project. | "What should I ask after the first version has been built?" |
| [grill-me](../grill-me/SKILL.md) | Asks one useful question at a time to help you work out what you want. | "Help me decide who my booking app is for and what it needs to do." |
| [in-your-own-words](../in-your-own-words/SKILL.md) | Tells you what the assistant thinks you mean, so you can correct misunderstandings. | "Before we start, tell me what you think I want." |
| [sharpen](../sharpen/SKILL.md) | Makes your request clearer and more useful without adding more work. | "Make 'improve my sign-up page' into a clear request." |
| [figure-it-out](../figure-it-out/SKILL.md) | Works out a plan for a difficult job when there is no obvious set of steps. | "Plan how to move our old booking system without losing appointments." |

## Build and check things

| Skill | In everyday English | Example of when it helps |
| --- | --- | --- |
| [ponytail](../ponytail/SKILL.md) | Helps the assistant solve the whole problem with the least unnecessary work. | "Add appointment reminders using what the app already has." |
| [ponytail-review](../ponytail-review/SKILL.md) | Checks a recent change for mistakes and unnecessary complications. | "Check the new reminder feature before I try it." |
| [ponytail-audit](../ponytail-audit/SKILL.md) | Looks through a whole project and ranks the problems it finds. | "Tell me which problems in my booking app need attention first." |
| [ponytail-debt](../ponytail-debt/SKILL.md) | Lists shortcuts the developers recorded and when those shortcuts need replacing. | "What temporary fixes did we leave for later?" |
| [ponytail-gain](../ponytail-gain/SKILL.md) | Shows Ponytail's published comparison results, not results measured on your project. | "What results do Ponytail's creators report?" |
| [ponytail-help](../ponytail-help/SKILL.md) | Explains Ponytail's commands and how much it should question unnecessary work. | "What is the difference between Ponytail's lite, full, and ultra settings?" |
| [tdd](../tdd/SKILL.md) | Writes a check that shows a problem first, fixes the problem, then checks again. | "Prove that two people cannot book the same appointment slot." |
| [blast-radius](../blast-radius/SKILL.md) | Looks for other parts of the app a change might accidentally break. | "Could changing sign-in stop existing customers from opening their bookings?" |
| [benchmark-checklist](../benchmark-checklist/SKILL.md) | Checks whether a speed comparison was fair and tested the right thing. | "Was the new booking page really faster under the same conditions?" |
| [correct](../correct/SKILL.md) | Turns a repeated mistake into a rule or check that can catch it next time. | "The assistant keeps forgetting date checks. Help prevent that mistake." |
| [typescript-best-practices](../typescript-best-practices/SKILL.md) | Helps organize code written in TypeScript, a programming language with checks for common data mistakes. | "Have the assistant check our TypeScript code for avoidable mistakes." |

## Understand and communicate

| Skill | In everyday English | Example of when it helps |
| --- | --- | --- |
| [how](../how/SKILL.md) | Explains how something works and how its parts connect. | "How does a booking get from the form to my calendar?" |
| [why](../why/SKILL.md) | Looks for the reasons behind a past decision and says when the reason is uncertain. | "Why did we choose email reminders instead of text messages?" |
| [teach](../teach/SKILL.md) | Helps you understand how something works and why it was built that way, at your pace. | "Teach me how our reminder feature works. Assume I do not write code." |
| [bro](../bro/SKILL.md) | Rewrites the assistant's last explanation in simpler language. | "I did not understand that answer. Say it in everyday English." |
| [technical-writing](../technical-writing/SKILL.md) | Helps write clear guides and explanations people can follow. | "Write instructions for someone using the booking app for the first time." |
| [unslop](../unslop/SKILL.md) | Removes filler and awkward AI wording while keeping the meaning. | "Make this update sound clear and natural." |
| [ketchup](../ketchup/SKILL.md) | Catches you up on what happened and which decisions need your input. | "I have been away. What changed, and what do you need from me?" |
| [ketchup-video](../ketchup-video/SKILL.md) | Makes a short video update when a suitable video tool is available. | "Show me a short video of the work completed today." |

## Habits for better work

These longer command names each ask the assistant to apply one working habit.

| Skill | In everyday English | Example of when it helps |
| --- | --- | --- |
| [principle-attack-the-premise](../principle-attack-the-premise/SKILL.md) | Questions a shared assumption when several attempted fixes fail. | "We tried fixing the calendar twice. Are we wrong about what causes the problem?" |
| [principle-boundary-discipline](../principle-boundary-discipline/SKILL.md) | Checks information as it enters the app, before other parts rely on it. | "Reject impossible dates when someone submits the booking form." |
| [principle-build-the-lever](../principle-build-the-lever/SKILL.md) | Makes a tool that can repeat a job or check instead of doing it by hand each time. | "Make a repeatable check for broken booking links." |
| [principle-encode-lessons-in-structure](../principle-encode-lessons-in-structure/SKILL.md) | Builds a lesson into the app or its checks so it is harder to forget. | "Make it impossible to save a booking without a date." |
| [principle-exhaust-the-design-space](../principle-exhaust-the-design-space/SKILL.md) | Compares a few possible designs before choosing one. | "Show two ways customers could choose an appointment time." |
| [principle-experience-first](../principle-experience-first/SKILL.md) | Gives priority to making the result useful and pleasant for the person using it. | "Make booking one appointment feel clear and complete before adding more features." |
| [principle-explain-the-number](../principle-explain-the-number/SKILL.md) | Checks what a number really measures before using it to make a decision. | "Does 'two seconds faster' include the time spent waiting for the calendar?" |
| [principle-fix-root-causes](../principle-fix-root-causes/SKILL.md) | Finds and fixes the reason a problem happens. | "Find why duplicate reminders are sent, rather than hiding the extra messages." |
| [principle-foundational-thinking](../principle-foundational-thinking/SKILL.md) | Works out how important information should fit together before building around it. | "Decide how customers, appointments, and cancellations should be recorded." |
| [principle-guard-the-context-window](../principle-guard-the-context-window/SKILL.md) | Keeps the assistant's working notes manageable so important information stays available. | "Summarize the useful findings instead of filling the conversation with long files." |
| [principle-laziness-protocol](../principle-laziness-protocol/SKILL.md) | Looks for the smallest complete fix and removes unnecessary complications. | "Can we fix reminders using the existing system?" |
| [principle-make-operations-idempotent](../principle-make-operations-idempotent/SKILL.md) | Makes repeating an action safe, so a retry does not create extra copies. | "Clicking Book twice should still create only one appointment." |
| [principle-migrate-callers-then-delete-legacy-apis](../principle-migrate-callers-then-delete-legacy-apis/SKILL.md) | Moves every part using an old connection to its replacement, then removes the old connection. | "Move all reminders to the new email service before removing the old one." |
| [principle-minimize-reader-load](../principle-minimize-reader-load/SKILL.md) | Makes code easier for the next person to understand. | "Make the cancellation rules easier for another developer to follow." |
| [principle-model-the-domain](../principle-model-the-domain/SKILL.md) | Organizes information around the real things and rules the app deals with. | "Represent an appointment as requested, confirmed, or cancelled, with clear rules for changes." |
| [principle-outcome-oriented-execution](../principle-outcome-oriented-execution/SKILL.md) | Keeps a major change focused on the finished design instead of adding temporary work nobody needs. | "Replace the old calendar in agreed stages without maintaining extra temporary systems." |
| [principle-prove-it-works](../principle-prove-it-works/SKILL.md) | Checks the actual result before saying the job is done. | "Book a sample appointment and confirm it appears in the calendar." |
| [principle-redesign-from-first-principles](../principle-redesign-from-first-principles/SKILL.md) | Rethinks how the parts should fit when an important new need changes the design. | "If bookings now support groups, how should the appointment system fit together?" |
| [principle-separate-before-serializing-shared-state](../principle-separate-before-serializing-shared-state/SKILL.md) | Gives simultaneous jobs separate working information where possible so they do not overwrite each other. | "Keep each reminder job's notes separate while several jobs run." |
| [principle-sequence-verifiable-units](../principle-sequence-verifiable-units/SKILL.md) | Splits work into small useful steps and checks each before moving on. | "Finish and check booking an appointment before adding rescheduling." |
| [principle-subtract-before-you-add](../principle-subtract-before-you-add/SKILL.md) | Removes unused or repeated parts before adding something new. | "Remove the abandoned reminder code before adding its replacement." |
| [principle-test-behavior-not-implementation](../principle-test-behavior-not-implementation/SKILL.md) | Checks what a person can do with the app, so internal changes do not invalidate useful checks. | "Check that cancelling frees the slot, whichever way the code is organized." |
| [principle-type-system-discipline](../principle-type-system-discipline/SKILL.md) | Uses programming-language checks to catch invalid information before the app runs. | "Help the code catch a booking that has no customer before anyone uses it." |
