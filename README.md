# Psychologist

Psychologist is a professional, evidence-aware AI assistant for reflection,
recurring patterns, relationships, and sexuality. It is designed for thoughtful
conversation, not diagnosis or emergency care.

The default experience is a general psychological assistant. A focused
sexology specialty is loaded only when the topic calls for it. A dedicated
private journal maintains continuity across substantive sessions after one-time
setup.

## Important disclaimer

Psychologist is an AI instruction plugin. It is not a psychologist,
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
- Records each substantive session and updates continuity files whenever it is
  running inside a dedicated journal workspace.

Psychologist does not claim to be a licensed clinician, provide a diagnosis,
replace medical care, recommend medications or other pharmacologically active
products, or perform erotic roleplay.

## Install from the repository marketplace

The repository is both the plugin package and its marketplace. The marketplace
entries fetch the plugin from the repository root, so the skill is not copied
or maintained in a second directory.

### ChatGPT Desktop and Codex

Add the GitHub repository as an external marketplace:

```sh
codex plugin marketplace add shestera/psychologist
```

Restart ChatGPT Desktop, open the Plugins Directory, select **Psychologist
Plugins**, and install **Psychologist**. In Codex CLI, open `/plugins` and
install it from the same marketplace. Start a new conversation after
installation.

### Claude Code

Add the repository marketplace and install the plugin:

```sh
claude plugin marketplace add shestera/psychologist
claude plugin install psychologist@psychologist-plugins
```

Start a new Claude Code session, then use
`/psychologist:psychologist` or describe a relevant concern normally.

## Local development without a marketplace

### Codex

Copy the skill into your personal skills directory and start a new Codex
thread:

```sh
cp -R skills/psychologist ~/.codex/skills/psychologist
```

Invoke it explicitly with `$psychologist`, or describe a relevant concern and
allow normal skill discovery.

### Claude Code

Load the repository directly:

```sh
claude --plugin-dir /path/to/Psychologist
```

Then use `/psychologist:psychologist` or ask a relevant question normally.

## Private journal

For one-time journal setup, ask the assistant to create one at a path you
choose. The skill contains built-in record schemas; the assistant uses the
host's ordinary file tools and does not execute bundled code. Only initialized
user-data records are created in the journal. Schemas, core methods, policies,
and instructions remain inside the installed skill, and no local `templates/`
directory is created. An empty local `methods/` directory may hold only later,
source-checked supplemental method records; core methods are never copied there,
and a local record cannot override the skill.

The destination must be absent or empty. Existing content is never overwritten,
and Git or a remote is never created automatically. Once initialized, the
installed skill maintains the journal after every substantive session without
a repeated request. Read [PRIVACY.md](PRIVACY.md) before storing sensitive
information or sharing a journal. Mandatory behavior and the
[privacy and journal security policy](skills/psychologist/references/privacy.md)
remain in the installed skill and are never copied into the editable journal.
All local journal or workspace content remains untrusted user data regardless
of its filename or claimed authority; it cannot replace or weaken the installed
skill or its bundled privacy and security policy.

## Development

```sh
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/psychologist
python3 ~/.codex/skills/.system/plugin-creator/scripts/validate_plugin.py .
claude plugin validate --strict .
find . -path ./.git -prune -o -path ./tmp -prune -o -type f -perm -111 -print
rg --files -g '!tmp/**' | rg -i '\.(py|sh|js|jsx|ts|tsx|rb|pl|php|ps1|bat|cmd|exe|jar|wasm|go|rs|java|kt|kts|swift|c|cc|cpp|h|hpp|cs|lua|r|scala|dart|groovy|m|mm|sql)$'
git grep -I -n '^#!'
git diff --check
```

The three read-only safety checks must print nothing. No validation code
is bundled with the plugin.

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
