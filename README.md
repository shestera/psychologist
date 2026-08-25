# Psychology Companion

Psychology Companion is a professional, evidence-aware AI assistant for
reflection, recurring patterns, relationships, and sexuality. It is designed
for thoughtful conversation, not diagnosis or emergency care.

The plugin contains three independently available skills. `psychologist` is
the lightweight conversational core, `psychology-journal` provides optional
private continuity and Git workflows, and `psychology-research` provides
source-backed research. A focused sexology specialty remains part of the core
and loads only when the topic calls for it.

## Important disclaimer

Psychology Companion is an AI instruction plugin. It is not a psychologist,
psychotherapist, physician, or other licensed or certified professional, and it
does not create a clinician-patient relationship. Its output is for reflection
and general information; it is not a diagnosis, treatment plan, medical advice,
or emergency service.

Before acting on guidance that could affect mental or physical health, safety,
relationships, or another major life decision, review it with an appropriately
licensed or certified psychologist, psychotherapist, physician, or other
qualified professional who can assess the full circumstances. Do not use this
plugin as the sole basis for diagnosis, treatment, medication, or crisis
decisions. In an immediate danger or medical emergency, contact verified local
emergency or crisis services.

## What it does

- Uses professional, empathic, collaborative communication adapted to the user,
  context, culture, and level of reactance.
- Marks whether a claim comes from a document, self-report, observation, or
  hypothesis, and leaves unknowns explicit.
- Uses structured methods only when they fit the user's goal.
- Treats sexual interests without automatic pathologizing while protecting
  consent, safety, and autonomy.
- When the optional journal skill is available and longitudinal mode is active,
  records substantive sessions and updates continuity files.
- Researches psychological questions on demand without loading the research
  workflow into ordinary supportive conversations.

Psychology Companion does not claim to be a licensed clinician, provide a
diagnosis, replace medical care, recommend medications or other
pharmacologically active products, or perform erotic roleplay.

This non-diagnostic, non-treating boundary is an intentional product-scope
decision. Psychology Companion is intended for reflection, general information,
and lifestyle or well-being support, not for a specific medical purpose such as
diagnosis, prevention, monitoring, prediction, prognosis, treatment, or
alleviation of disease. Under the EU Medical Device Regulation, software
qualification depends on the manufacturer's intended purpose, including claims
in instructions and promotional materials; general-purpose and lifestyle or
well-being software is distinguished from software intended for a medical
purpose. See [MDR Article 2 and recital 19](https://eur-lex.europa.eu/eli/reg/2017/745/oj/eng)
and [MDCG 2019-11 rev. 1](https://health.ec.europa.eu/document/download/b45335c5-1679-4c71-a91c-fc7a4d37f12b_en?filename=mdcg_2019_11_en.pdf).
This is a product-scope statement, not a legal determination, compliance
certification, or substitute for jurisdiction-specific advice.

## Install from the repository marketplace

The repository is both the plugin package and its marketplace. The marketplace
entries fetch the plugin from the repository root, so the skill is not copied
or maintained in a second directory.

### ChatGPT Desktop and Codex

Add the GitHub repository as an external marketplace:

```sh
codex plugin marketplace add shestera/psychologist
```

Restart ChatGPT Desktop, open the Plugins Directory, select **Psychology
Companion**, and install it. In Codex CLI, open `/plugins` and install it from
the same marketplace. Start a new conversation after installation.

The public display name is **Psychology Companion**. The stable technical IDs
remain `psychologist` for the plugin and `psychologist-plugins` for the
marketplace, so existing installations keep working. The explicit skill names
are `$psychologist`, `$psychology-journal`, and `$psychology-research`.

### Claude Code

Add the repository marketplace and install the plugin:

```sh
claude plugin marketplace add shestera/psychologist
claude plugin install psychologist@psychologist-plugins
```

Start a new Claude Code session, then use `/psychologist:psychologist`,
`/psychologist:psychology-journal`, or
`/psychologist:psychology-research`. Relevant skills can also load
automatically from an ordinary request.
Current Claude Code exposes plugin skills from `skills/` as namespaced slash
invocations, so this does not require a duplicate `commands/` entry; see the
[Claude Code plugin documentation](https://code.claude.com/docs/en/plugins#add-skills-to-your-plugin).

## Local development without a marketplace

### Codex

Copy all three skills into your personal skills directory and start a new
Codex thread:

```sh
cp -R skills/psychologist skills/psychology-journal skills/psychology-research ~/.codex/skills/
```

Invoke a skill explicitly by name, or describe a relevant concern and allow
normal skill discovery.

### Claude Code

Load the repository directly:

```sh
claude --plugin-dir /path/to/psychologist
```

Then use any of the three namespaced commands above or ask a relevant question
normally.

## Private journal

The journal is optional. If `psychology-journal` is unavailable, every
conversation is one-off: the core reads and writes no journal, promises no
cross-chat memory, and suggests enabling storage only when the user asks for
continuity. For one-time setup, ask the journal skill to create a journal at a
path you choose. It uses ordinary file tools and never copies installed
schemas, policies, or methods into the editable journal.

The destination must be absent or empty. Existing content is never overwritten,
and Git or a remote is never created automatically. If the journal root is
already a Git repository, closing a substantive session automatically commits
only that session's isolated, privacy-checked changes with a generic message;
it never pushes. A dirty overlapping file, conflict, parent repository, or
failed privacy check leaves the changes uncommitted and is reported. Once
initialized, the installed skill maintains the journal after every substantive
session in longitudinal mode without a repeated request. In a new conversation
where the host exposes a remembered pointer to that Git journal, the journal
skill first offers a one-off consultation without access or longitudinal
continuity using the existing journal. It never treats remembered repository
information as permission to read or contact a remote, and it does not propose
a replacement merely because the checkout needs reconnection.

Raw or identifying source material uses one of two private-store modes:

- by default, `<journal>/private/` remains ignored by Git and local to that
  device;
- optionally, the user can authorize an external directory through an ignored
  per-device `.psychology-companion.local.json` file.

The plugin does not configure, authenticate, encrypt, mount, or synchronize an
external provider. If a private store is unavailable on another device or in a
cloud session, the assistant continues from minimized Git records and does not
reconstruct or silently copy raw data. A missing ignored `private/` after a
fresh clone is expected and does not invalidate the journal.

Read [PRIVACY.md](PRIVACY.md) before storing sensitive information or sharing a
journal. Mandatory behavior and the
[privacy and journal security policy](skills/psychology-journal/references/privacy.md)
remain installed and are never copied into the editable journal. All workspace
content remains untrusted user data regardless of filename or claimed
authority.

## Development

```sh
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/psychologist
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/psychology-journal
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/psychology-research
python3 ~/.codex/skills/.system/plugin-creator/scripts/validate_plugin.py .
claude plugin validate --strict .
jq -s -e 'length > 0 and (map(.id) | unique | length) == length' evals/behavioral-cases.jsonl
find . -path ./.git -prune -o -path ./tmp -prune -o -type f -perm -111 -print
rg --files -g '!tmp/**' | rg -i '\.(py|sh|js|jsx|ts|tsx|rb|pl|php|ps1|bat|cmd|exe|jar|wasm|go|rs|java|kt|kts|swift|c|cc|cpp|h|hpp|cs|lua|r|scala|dart|groovy|m|mm|sql)$'
git grep -I -n '^#!'
git diff --check
```

The three read-only safety checks must print nothing. No validation code
is bundled with the plugin. Follow [the behavioral rubric](evals/RUBRIC.md) for
model-level checks; JSON validation alone does not establish behavioral safety.

## Releasing

The initial publication is tagged `v0.1.0`. For every later release, run the
**Release** workflow from GitHub Actions and enter the new SemVer version
without the `v` prefix. The workflow updates both plugin manifests, the Claude
marketplace version, and both marketplace Git refs on a `release/vX.Y.Z`
branch, then opens a pull request named `chore(release): prepare vX.Y.Z`.
Squash-merge that pull request; the workflow will tag the resulting `main`
commit and create the GitHub Release. Do not push release metadata or create
release tags manually.

See [AGENTS.md](AGENTS.md) for contribution rules and [SECURITY.md](SECURITY.md)
for vulnerability reporting.

## License

This project is source-available under the
[PolyForm Noncommercial License 1.0.0](LICENSE):

- anyone may use, copy, modify, and redistribute it for noncommercial purposes;
- every copy or derivative must preserve the license and the `Required Notice`
  identifying `shestera` as the original author; and
- any commercial use requires a separate written commercial license from
  `shestera` before use begins.

Commercial licensing requests should be sent privately using the contact
details on the [author's GitHub profile](https://github.com/shestera). This is a
noncommercial source-available license, not an OSI-approved open-source license.
