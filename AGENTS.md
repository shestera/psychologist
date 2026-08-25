# Repository Guidelines

## Project Structure & Module Organization

This repository packages three coordinated Psychology Companion skills for
Codex and Claude Code.

- `.codex-plugin/plugin.json` contains the Codex plugin manifest and points to `skills/`.
- `.claude-plugin/plugin.json` contains the Claude Code plugin manifest.
- `.agents/plugins/marketplace.json` and `.claude-plugin/marketplace.json`
  expose the root plugin through the OpenAI and Claude Code repository
  marketplaces without duplicating its files.
- `skills/psychologist/` is the lightweight conversational, safety, methods,
  and sexology core.
- `skills/psychology-journal/` owns longitudinal continuity, privacy, record
  schemas including evidence and supplemental-method templates, private-store
  selection, and protected Git behavior.
- `skills/psychology-research/` owns evidence appraisal, psychometrics,
  and source-backed research results. It returns findings to its requester and
  never persists journal records. Its psychometric registry is a dated starting
  point, not a bundled questionnaire library.
- `research/` is the development-only evidence archive for the psychological
  and sexological knowledge expressed by the skills. It is for maintainers and
  auditors, never runtime preload or user journal data. Do not place skill
  architecture, prompting, packaging, Git, CI, or model-selection research
  there.

## Build, Test, and Development Commands

There is no build step or third-party runtime dependency. Validate every change:

```sh
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/psychologist
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/psychology-journal
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/psychology-research
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
`templates/` directory out of the editable journal. External private-store
configuration must remain ignored, allowlisted, per-device, and outside every
Git worktree. New journals include minimized `session-index.md`,
`research-index.md`, and `method-index.md` maps. Legacy journals without any of
these indexes remain valid and require opt-in, bounded backfill rather than an
automatic scan of record directories.

## Coding Style & Naming Conventions

Use two-space JSON indentation, trailing newlines, and lowercase kebab-case
skill directories. Keep text in English and Markdown direct. Use relative
manifest paths such as `"skills": "./skills/"`. Synchronize the SPDX license
identifier across `LICENSE`, both manifests, and `SKILL.md`.

Keep academic provenance and literature-review detail in dated topic briefs
under `research/`, with affected runtime paths, limitations, review dates, and
update triggers. Runtime skill files keep only decision-changing instructions
and operational links required at use time. Never make a skill load the root
evidence archive before an ordinary user response. Update the relevant brief
and `research/index.md` in the same pull request as a foundational knowledge
change.

## Testing Guidelines

No coverage target is configured. Test behavior, not exact prose: a general
concern must not activate sexology guidance; a sexuality concern must preserve
consent and avoid pathologizing; crisis language must switch to immediate
safety; journal creation must protect existing files and never copy bundled
record schemas or core methods into the journal. Its local `methods/` directory
must start empty and accept only reviewed supplemental method records.
Longitudinal resume must use the session index to select relevant prior notes
and use research and method indexes to select only relevant full records,
without loading full archives. It must degrade safely when a legacy journal has
no index. A verified journal already active as the authorized workspace uses
standing documentation without a repeated mode or save prompt; an unverified
remembered locator does not.
Disabling the journal skill must force one-off conversation behavior;
disabling research must prevent evidence-note creation without weakening
crisis safety. Research itself must never write journal files; only the journal
skill may render returned findings with its installed record templates.
Research may read the minimum content from exact user files explicitly provided
or authorized for the current question, but must not discover or enumerate a
journal independently. With an authorized active journal, research reads the
provided `research-index.md` first and opens only relevant indexed briefs before
performing a fresh search.

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

## graphify

This project has a knowledge graph at graphify-out/ with god nodes, community structure, and cross-file relationships.

When the user types `/graphify`, use the installed graphify skill or instructions before doing anything else.

Rules:
- For codebase questions, first run `graphify query "<question>"` when graphify-out/graph.json exists. Use `graphify path "<A>" "<B>"` for relationships and `graphify explain "<concept>"` for focused concepts. These return a scoped subgraph, usually much smaller than GRAPH_REPORT.md or raw grep output.
- Dirty graphify-out/ files are expected after hooks or incremental updates; dirty graph files are not a reason to skip graphify. Only skip graphify if the task is about stale or incorrect graph output, or the user explicitly says not to use it.
- If graphify-out/wiki/index.md exists, use it for broad navigation instead of raw source browsing.
- Read graphify-out/GRAPH_REPORT.md only for broad architecture review or when query/path/explain do not surface enough context.
- After modifying code, run `graphify update .` to keep the graph current (AST-only, no API cost).
