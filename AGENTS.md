# Repository Guidelines

## Project Structure & Module Organization

This repository packages a psychologist skill for Codex and Claude Code.

- `.codex-plugin/plugin.json` contains the Codex plugin manifest and points to `skills/`.
- `.claude-plugin/plugin.json` contains the Claude Code plugin manifest.
- `.agents/plugins/marketplace.json` and `.claude-plugin/marketplace.json`
  expose the root plugin through the OpenAI and Claude Code repository
  marketplaces without duplicating its files.
- `skills/psychologist/SKILL.md` defines the psychologist skill instructions.
- `skills/psychologist/references/` holds source-backed professional guidance;
  `privacy.md` is the mandatory privacy and journal security policy,
  `core-methods.md` defines built-in methods, and `additional-methods.md`
  governs journal-specific supplemental methods.
- `skills/psychologist/assets/note-templates/` holds schemas that remain inside
  the skill and are used to create initialized user-data records.

## Build, Test, and Development Commands

There is no build step or third-party runtime dependency. Validate every change:

```sh
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/psychologist
python3 ~/.codex/skills/.system/plugin-creator/scripts/validate_plugin.py .
claude plugin validate --strict .
find . -path ./.git -prune -o -path ./tmp -prune -o -type f -perm -111 -print
rg --files -g '!tmp/**' | rg -i '\.(py|sh|js|jsx|ts|tsx|rb|pl|php|ps1|bat|cmd|exe|jar|wasm|go|rs|java|kt|kts|swift|c|cc|cpp|h|hpp|cs|lua|r|scala|dart|groovy|m|mm|sql)$'
git grep -I -n '^#!'
git diff --check
```

Safety checks must print nothing. Journal creation
instructions must refuse symlinks and non-empty destinations, preserve existing
files, never initialize Git, and keep policies, schemas, and a local
`templates/` directory out of the editable journal.

## Coding Style & Naming Conventions

Use two-space JSON indentation, trailing newlines, and lowercase kebab-case
skill directories. Keep text in English and Markdown direct. Use relative
manifest paths such as `"skills": "./skills/"`. Synchronize the SPDX license
identifier across `LICENSE`, both manifests, and `SKILL.md`.

## Testing Guidelines

No coverage target is configured. Test behavior, not exact prose: a general
concern must not activate sexology guidance; a sexuality concern must preserve
consent and avoid pathologizing; crisis language must switch to immediate
safety; journal creation must protect existing files and never copy bundled
record schemas or core methods into the journal. Its local `methods/` directory
must start empty and accept only reviewed supplemental method records.

Validate `evals/behavioral-cases.jsonl` with the repository CI and follow
`evals/RUBRIC.md` for model runs. Before a release that changes instructions or
model-facing behavior, run every case on Codex and Claude Code. Record the
client, model, commit, evaluator, date, and result in the release PR; any failed
safety-critical case blocks release.

## Commit & Pull Request Guidelines

After the initial repository publication, every change must reach `main`
through a pull request and squash merge. Direct pushes, merge commits, and
rebase merges are not allowed.

Use Conventional Commits for every PR title and resulting squash commit:
`type(scope)!: imperative summary`. Allowed types are `feat`, `fix`, `perf`,
`docs`, `refactor`, `test`, `build`, `ci`, `chore`, and `revert`. Keep the title
in English, lowercase the type and optional scope, omit the final period, and
stay within 100 characters. Use `!` and a `BREAKING CHANGE:` PR-body footer for
incompatible behavior. Examples: `docs(skill): clarify session boundaries` and
`feat(journal)!: revise workspace schema`.

For release notes, `feat` maps to a minor release, `fix` and `perf` map to a
patch release, and `!` maps to a major release. Other types do not require a
release by themselves. Pull requests must explain behavioral impact, list
validation, link relevant issues, and add before/after examples when
instructions change.

Create releases only through `.github/workflows/release.yml`, entering SemVer
without the `v` prefix. The workflow opens a version-update pull request and,
after its squash merge, tags the resulting `main` commit and publishes the
GitHub Release. It keeps both plugin manifests, the Claude marketplace version,
and both tag-pinned marketplace sources synchronized.

## Security & Configuration Tips

Never add bundled scripts, executable files, or symlinks. Never copy material
from a user's journal into this repository. Do not commit
credentials, transcripts, case histories, timelines, intimate material,
identifying dates, or generated profiles. Use fictional, minimal examples. A
privacy scan must pass before every release. Bundled method examples must not
contain personal case details or copyrighted manuals and instruments.
