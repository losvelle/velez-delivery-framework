# Velez Delivery Framework (VDF)

Human-directed AI delivery, from idea to production. Introduced and adapted by Carlos Velez.

VDF guides discovery, requirements, small deliverable issues, bounded implementation, independent review, human acceptance, and authorized release. It works on its own; the companion skills provide optional help at each phase.

The package includes:

- `velez-delivery`: the complete workflow, templates, and acceptance checks.
- `velez-recipes`: phase-by-phase prompts and situational recipes.
- `velez-help`: everyday explanations and examples for every skill, including help choosing one.
- `grill-me`: a focused design interview.
- Six Ponytail skills, selected pstack skills, and pstack principles except `principle-never-block-on-the-human`.
- Optional Delivery Planner and Delivery Reviewer agents, plus an all-`auto` pstack role configuration.
- A [synthetic walkthrough](WALKTHROUGH.md) and upstream license notices.

## Skill reference

All 49 skills are listed below. Select a skill name to read its instructions, or invoke it with `/skill-name` in a supported host. Start with `/velez-help` for plain-English explanations, `/velez-delivery` for the workflow, or `/velez-recipes` for example prompts. Companion skills are optional, and VDF gates take precedence.

### Workflow and planning

| Skill | What it does |
| --- | --- |
| [velez-delivery](skills/velez-delivery/SKILL.md) | Guide discovery through authorized release, with evidence, review, and human acceptance gates. |
| [velez-help](skills/velez-help/SKILL.md) | Explain every skill in everyday language and help choose one for a task. |
| [velez-recipes](skills/velez-recipes/SKILL.md) | Choose phase-specific prompts and situational recipes for the bundled skills. |
| [grill-me](skills/grill-me/SKILL.md) | Resolve consequential design choices through one focused question at a time. |
| [in-your-own-words](skills/in-your-own-words/SKILL.md) | Restate the goal and problem to confirm shared understanding. |
| [sharpen](skills/sharpen/SKILL.md) | Make a task more precise and substantive without expanding its scope. |
| [figure-it-out](skills/figure-it-out/SKILL.md) | Plan unfamiliar or complex work as bounded experiments with recorded decisions. |

### Code, tests, and review

| Skill | What it does |
| --- | --- |
| [ponytail](skills/ponytail/SKILL.md) | Make the smallest complete change and report skipped work and remaining risks. |
| [ponytail-review](skills/ponytail-review/SKILL.md) | Review a specific change for correctness, security, tests, and unnecessary complexity. |
| [ponytail-audit](skills/ponytail-audit/SKILL.md) | Audit a codebase and rank concrete bugs, risks, and maintenance problems. |
| [ponytail-debt](skills/ponytail-debt/SKILL.md) | List declared shortcuts and the conditions that call for replacing them. |
| [ponytail-gain](skills/ponytail-gain/SKILL.md) | Show upstream benchmark results; these are not measurements of your project. |
| [ponytail-help](skills/ponytail-help/SKILL.md) | Explain Ponytail commands and levels; full-plugin features are outside this bundle. |
| [tdd](skills/tdd/SKILL.md) | Develop behavior through an observed failing test, a minimal implementation, and passing checks. |
| [blast-radius](skills/blast-radius/SKILL.md) | Check what a change could break beyond its diff and verify key safety assumptions. |
| [benchmark-checklist](skills/benchmark-checklist/SKILL.md) | Check whether a performance measurement is relevant, repeatable, and measuring the intended work. |
| [correct](skills/correct/SKILL.md) | Prevent recurring mistakes through architecture, types, lint rules, or tests. |
| [typescript-best-practices](skills/typescript-best-practices/SKILL.md) | Apply TypeScript guidance to types, interfaces, and implementation choices. |

### Explanation and communication

| Skill | What it does |
| --- | --- |
| [how](skills/how/SKILL.md) | Explain architecture, runtime behavior, and where responsibilities belong in the code. |
| [why](skills/why/SKILL.md) | Explain decisions and tradeoffs using evidence, with uncertainty kept explicit. |
| [teach](skills/teach/SKILL.md) | Combine how and why into a plain explanation at the reader's pace. |
| [bro](skills/bro/SKILL.md) | Restate the last message in plain language. |
| [technical-writing](skills/technical-writing/SKILL.md) | Write clear instructions, references, explanations, and technical documents. |
| [unslop](skills/unslop/SKILL.md) | Remove filler and stock AI phrasing while preserving meaning. |
| [ketchup](skills/ketchup/SKILL.md) | Summarize progress since the last user message and identify waiting decisions. |
| [ketchup-video](skills/ketchup-video/SKILL.md) | Produce a short subtitled progress video when approved rendering tools are available. |

### Engineering principles

| Skill | What it does |
| --- | --- |
| [principle-attack-the-premise](skills/principle-attack-the-premise/SKILL.md) | Test a shared assumption when repeated fixes fail the same check. |
| [principle-boundary-discipline](skills/principle-boundary-discipline/SKILL.md) | Validate external inputs at system boundaries and keep internal logic clear. |
| [principle-build-the-lever](skills/principle-build-the-lever/SKILL.md) | Build a reusable tool or check that performs or verifies the work. |
| [principle-encode-lessons-in-structure](skills/principle-encode-lessons-in-structure/SKILL.md) | Turn recurring instructions into enforced rules or checks. |
| [principle-exhaust-the-design-space](skills/principle-exhaust-the-design-space/SKILL.md) | Compare competing prototypes before choosing an unfamiliar design. |
| [principle-experience-first](skills/principle-experience-first/SKILL.md) | Prioritize a polished user experience when choosing scope and implementation. |
| [principle-explain-the-number](skills/principle-explain-the-number/SKILL.md) | Establish what a measurement actually measures before trusting it. |
| [principle-fix-root-causes](skills/principle-fix-root-causes/SKILL.md) | Trace a symptom to its first cause and repair that cause. |
| [principle-foundational-thinking](skills/principle-foundational-thinking/SKILL.md) | Choose core types, data structures, and ownership before writing logic. |
| [principle-guard-the-context-window](skills/principle-guard-the-context-window/SKILL.md) | Keep large outputs and repeated reads from overwhelming the working context. |
| [principle-laziness-protocol](skills/principle-laziness-protocol/SKILL.md) | Prefer deletion and the smallest complete change over extra abstractions. |
| [principle-make-operations-idempotent](skills/principle-make-operations-idempotent/SKILL.md) | Make retries and restarts converge to the same intended state. |
| [principle-migrate-callers-then-delete-legacy-apis](skills/principle-migrate-callers-then-delete-legacy-apis/SKILL.md) | Move callers to a replacement API and remove the old API in the same change. |
| [principle-minimize-reader-load](skills/principle-minimize-reader-load/SKILL.md) | Reduce indirection and hidden state so code is easier to follow. |
| [principle-model-the-domain](skills/principle-model-the-domain/SKILL.md) | Represent states and domain rules explicitly instead of repeating conditional logic. |
| [principle-outcome-oriented-execution](skills/principle-outcome-oriented-execution/SKILL.md) | Move rewrites toward the target design without unnecessary temporary compatibility work. |
| [principle-prove-it-works](skills/principle-prove-it-works/SKILL.md) | Verify the actual behavior or artifact before claiming completion. |
| [principle-redesign-from-first-principles](skills/principle-redesign-from-first-principles/SKILL.md) | Reconsider the design when a new requirement changes its underlying assumptions. |
| [principle-separate-before-serializing-shared-state](skills/principle-separate-before-serializing-shared-state/SKILL.md) | Give concurrent actors separate state before adding synchronization. |
| [principle-sequence-verifiable-units](skills/principle-sequence-verifiable-units/SKILL.md) | Break work into ordered units and verify each before proceeding. |
| [principle-subtract-before-you-add](skills/principle-subtract-before-you-add/SKILL.md) | Remove dead code and redundant structure before adding a replacement. |
| [principle-test-behavior-not-implementation](skills/principle-test-behavior-not-implementation/SKILL.md) | Test observable behavior so internal refactoring does not break valid tests. |
| [principle-type-system-discipline](skills/principle-type-system-discipline/SKILL.md) | Use types and boundary parsing to prevent invalid states and handle variants explicitly. |

Some companions reference upstream tools or workflows outside this bundle. See the [recipe exclusions](skills/velez-recipes/SKILL.md#not-included) before using them.

## Download or clone

Download or clone [this repository](https://github.com/losvelle/velez-delivery-framework), then open its folder in a terminal:

```sh
git clone https://github.com/losvelle/velez-delivery-framework.git
cd velez-delivery-framework
```

On a managed device, follow your organization's approved intake and customization process. Read [Policy and transfer](POLICY-AND-TRANSFER.md). Use your existing approved Copilot account and model.

## Paste-in Copilot install prompt

Open the downloaded or cloned package in Copilot and paste:

```text
Install this Velez Delivery Framework package for my user account only.
Read README.md and POLICY-AND-TRANSFER.md first. Copy every complete skills/
folder into ~/.copilot/skills/ and the two agents/*.agent.md files into
~/.copilot/agents/. Copy settings/pstack-models.md to ~/.agents/pstack-models.md.
On Windows, resolve ~ to my user profile directory.

Before copying, inspect all destinations. If a name already exists, show the
differences and ask before replacing it. Preserve licenses and resources.
Never install into a project repository or modify repository instructions.
Do not run upstream installers, add providers, change my selected model, or
enable auto-approval. All pstack roles must stay auto; leave subagent model
arguments unset. Verify installed files match the source and report their
locations. Do not claim Copilot discovery or runtime behavior was tested
unless you actually tested it.
```

## Start using it

Start a fresh Copilot chat. In Copilot CLI, use `/skills reload` and `/skills info velez-delivery`; in VS Code, open **Chat: Open Customizations** and verify the personal skills appear. Try:

```text
/velez-help
/velez-help ponytail-review
/velez-help I have an app idea. Where do I start?
/velez-recipes Show the recipe for my current VDF phase.
/velez-delivery Explore and plan this feature only: ...
/grill-me Stress-test this idea before implementation: ...
```

All 49 bundled skills set `disable-model-invocation: true` for explicit slash invocation on hosts that support this control. The six Ponytail headers add it; the copied pstack skills retain their upstream settings. Verify invocation behavior in your installed Copilot version. See [VS Code's skill invocation controls](https://code.visualstudio.com/docs/agent-customization/agent-skills).

VDF gates win over companion advice. A companion never authorizes broader edits, skips required review or human acceptance, or grants release authority. See the [recipes and exclusions](skills/velez-recipes/SKILL.md) before using a companion. The copied skills may refer to upstream tools, commands, or workflows that are not bundled here. For example, Ponytail's band, hooks, automatic activation, and plugin updates are not installed by these copy commands. `ponytail-gain` reports upstream benchmark results, not savings measured in your project.

## Model settings and optional roles

[settings/pstack-models.md](settings/pstack-models.md) sets every pstack role to `auto`. It is plain-text guidance, not a Copilot provider configuration. The personal copy lives at `~/.agents/pstack-models.md`, the path pstack uses outside its dedicated host integrations. Copilot does not automatically apply this file as a global rule. At the start of a session that uses these companions, explicitly ask:

```text
Read ~/.agents/pstack-models.md. Keep every pstack role on auto and leave the
subagent model argument unset, inheriting this chat's selected model.
Follow VDF's approval gates and the current project's instructions.
```

Delivery Planner and Delivery Reviewer are optional. Select them through Copilot's agent picker (`/agent` in the CLI). Check that their actual available tools are limited to read/search. For independent review, use a fresh approved conversation/context or a human reviewer; switching roles in the author's conversation is not independent review. The agent files leave the model unset.

## Install personally, never into a project repository

Copy skill folders to `~/.copilot/skills/` and agent files to `~/.copilot/agents/`. These are personal locations shared across projects, supported by [Copilot skills](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-skills) and [Copilot custom agents](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/create-custom-agents-for-cli). Do not install this package into a project's `.github`, `.agents`, or `.claude` directories or modify its instructions.

The commands below install the complete bundle, including the optional agent definitions and role settings. They stop before copying if any destination already exists. Compare existing copies and preserve local changes before updating; do not delete an existing installation just to make the commands pass. Copy every skill's full folder, including resources and license files.

### macOS

Run from the downloaded or cloned `velez-delivery-framework` folder:

```sh
(
  set -eu
  vdf_source="$PWD"
  test -f "$vdf_source/skills/velez-delivery/SKILL.md"
  test -f "$vdf_source/settings/pstack-models.md"

  for source in "$vdf_source"/skills/* "$vdf_source"/agents/*.agent.md; do
    case "$source" in
      "$vdf_source"/skills/*) target="$HOME/.copilot/skills/${source##*/}" ;;
      *) target="$HOME/.copilot/agents/${source##*/}" ;;
    esac
    if [ -e "$target" ] || [ -L "$target" ]; then
      echo "Already exists; compare before updating: $target" >&2
      exit 1
    fi
  done
  if [ -e "$HOME/.agents/pstack-models.md" ] || [ -L "$HOME/.agents/pstack-models.md" ]; then
    echo "Already exists; compare before updating: $HOME/.agents/pstack-models.md" >&2
    exit 1
  fi

  mkdir -p "$HOME/.copilot/skills" "$HOME/.copilot/agents" "$HOME/.agents"
  cp -R "$vdf_source"/skills/* "$HOME/.copilot/skills/"
  cp "$vdf_source"/agents/*.agent.md "$HOME/.copilot/agents/"
  cp "$vdf_source/settings/pstack-models.md" "$HOME/.agents/pstack-models.md"
)
```

### Windows PowerShell

Run from the downloaded or cloned `velez-delivery-framework` folder:

```powershell
& {
    $ErrorActionPreference = 'Stop'
    $vdfSource = (Get-Location).Path
    $skillsTarget = Join-Path $env:USERPROFILE '.copilot\skills'
    $agentsTarget = Join-Path $env:USERPROFILE '.copilot\agents'
    $settingsTarget = Join-Path $env:USERPROFILE '.agents\pstack-models.md'
    if (!(Test-Path "$vdfSource\skills\velez-delivery\SKILL.md") -or
        !(Test-Path "$vdfSource\settings\pstack-models.md")) {
        throw 'Run this from the velez-delivery-framework folder.'
    }
    $skills = @(Get-ChildItem "$vdfSource\skills" -Directory)
    $agents = @(Get-ChildItem "$vdfSource\agents" -Filter '*.agent.md' -File)
    foreach ($skill in $skills) {
        $target = Join-Path $skillsTarget $skill.Name
        if (Test-Path -LiteralPath $target) { throw "Already exists; compare before updating: $target" }
    }
    foreach ($agent in $agents) {
        $target = Join-Path $agentsTarget $agent.Name
        if (Test-Path -LiteralPath $target) { throw "Already exists; compare before updating: $target" }
    }
    if (Test-Path -LiteralPath $settingsTarget) { throw "Already exists; compare before updating: $settingsTarget" }

    New-Item -ItemType Directory -Force -Path $skillsTarget, $agentsTarget, (Split-Path $settingsTarget) | Out-Null
    foreach ($skill in $skills) { Copy-Item -LiteralPath $skill.FullName -Destination $skillsTarget -Recurse }
    foreach ($agent in $agents) { Copy-Item -LiteralPath $agent.FullName -Destination $agentsTarget }
    Copy-Item -LiteralPath "$vdfSource\settings\pstack-models.md" -Destination $settingsTarget
}
```

## Verification and updates

Run the [non-sensitive acceptance checks](skills/velez-delivery/references/acceptance-checks.md) in your own environment. File installation does not prove skill discovery, tool enforcement, model behavior, or release readiness. This package has not been runtime-tested in your Copilot account or organization. No example application has been built or deployed by this package.

To update, download or clone the new version and compare the personal copies before replacing them. Keep local changes and license notices. If migrating an older repository-local installation, retire it only through that project's normal review process after verifying the personal copy. These commands do not alter it.

## Attribution

- VDF and its Copilot adaptation: Carlos Velez and contributors, under [LICENSE.md](LICENSE.md).
- `grill-me`: based on Matt Pocock's prompt, with its [MIT notice](skills/grill-me/LICENSE).
- [Ponytail](https://github.com/DietrichGebert/ponytail) by DietrichGebert: six selected skill folders from commit [`96608e078b2d5ea607c5c3b8b5a54d1c1fba6846`](https://github.com/DietrichGebert/ponytail/commit/96608e078b2d5ea607c5c3b8b5a54d1c1fba6846). Each folder retains the upstream MIT license; the six headers add manual invocation.
- [pstack](https://github.com/backnotprop/pstack): selected skill folders from commit [`74bcc61bd216687b1d6d480c28f109adfc9824ec`](https://github.com/backnotprop/pstack/commit/74bcc61bd216687b1d6d480c28f109adfc9824ec). Each copied folder includes its upstream MIT license, which credits Lauren Tan.

This is a curated adaptation, not an official Ponytail or pstack distribution. Upstream licenses continue to apply to their respective content.
