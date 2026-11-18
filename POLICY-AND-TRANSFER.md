# Policy and Transfer

VDF is a reusable workflow package. Installation does not grant organization approval, a model entitlement, access to protected data, or production authority. On a managed device, follow the organization's existing intake and customization rules.

## Use your existing company process

Use the account, project, and working practices your company already permits. VDF does not add a separate approval process. Reuse settled decisions for the same scope rather than asking everyone to complete a policy checklist at the start of each task.

The assistant starts with the requested work and reads available project guidance. It asks only when a specific next action lacks necessary authorization, conflicts with a known rule, or has an unresolved access or data-handling issue. The question names the action and the reason it matters. Other authorized work can continue.

If your company requires a review before installing external skills, use its existing process. The following are topics for that review when relevant, not questions every user must answer in chat:

- Personal Copilot skills under `~/.copilot/skills/` and optional agents under `~/.copilot/agents/` are permitted. They are shared across projects, so approval must cover their intended use.
- The selected account, model, projects, and data classifications are approved. Approval of an extension does not necessarily cover every model or repository.
- The reviewed external package may enter through the proposed intake route.
- The environment permits the intended reading, testing, code changes, and independent reviewer contexts.
- Applicable change, release, security review, and retention requirements are understood.

Keep protected designs, code, tickets, logs, credentials, personal data, and test evidence in their approved environment. Use invented examples for discussion across environments.

## What to transfer

Transfer the reviewed package through the route your organization permits. Install skills and agents only in the user's personal directories, never in a project repository. Preserve resource folders and all license notices. Review name collisions before replacing an existing copy.

The optional `settings/pstack-models.md` is a plain-text role preference file. Its personal destination is `~/.agents/pstack-models.md`; every role is `auto`, and subagent model arguments stay unset. It neither supplies credentials nor configures a new provider. Copilot must be explicitly told to read it; copying it does not make it an enforced global setting.

Do not transfer assistant home directories, `.env` files, tokens, sessions, memory, provider credentials, personal chat history, or personal cloud access. None is needed to install this package. Review any tools or external dependencies a companion skill proposes separately from installing its instructions.

If a download, transfer route, extension, or feature is blocked, use the normal intake process. Do not evade the restriction. A manual-prompt alternative is appropriate only when that route and use are permitted too.

## Optional approval request

Use this only if your existing company process requires approval to install the package. Do not send it as a prerequisite for every task.

> I would like to install a reviewed Velez Delivery Framework skill package using our existing approved Copilot account and model. It covers discovery, requirements, small deliverable issues, test-first implementation, independent review, human acceptance, and authorized release, with optional companion skills. Skill folders and their resources/licenses would go in my personal `~/.copilot/skills/` directory, and two optional read/search-only agent definitions in `~/.copilot/agents/`. No customization files would be installed into project repositories. An optional plain-text role preference file would go in `~/.agents/pstack-models.md`, with every role set to `auto` and subagent model arguments unset. This installation adds no provider, credentials, hooks, background service, or auto-approval setting. Companion instructions can refer to tools or external dependencies; their execution remains subject to our normal controls. Is this personal customization permitted for the intended projects and data classes, and what intake and review route should I use?

On Windows, `~` means the user's profile directory. A personal installation describes file scope; it does not mean using a personal account for organizational data.

## Policy stays authoritative

VDF's authorization gates and the organization's applicable rules take precedence over companion workflow advice. A skill cannot waive review, human acceptance, data-handling controls, or release approval.

Copilot may transmit permitted context to its model service according to the selected deployment and settings. Markdown installation does not make execution local-only or offline. Do not add personal API keys or providers, disable safeguards, enable broad auto-approval, or change managed settings to make a companion work.

Verify the optional agents' actual tool restrictions and skill behavior on the installed Copilot version. Instructions are not a sandbox. A checksum establishes that files match, not that they are trusted or approved. Retain verification evidence in the appropriate environment.
