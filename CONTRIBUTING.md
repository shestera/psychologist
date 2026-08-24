# Contributing

All changes must be proposed through a pull request. Keep each pull request
focused, explain its behavioral impact, list the validation performed, and link
related issues. Add before-and-after examples when changing instructions.

Use this Conventional Commits format for the pull request title:

```text
type(scope)!: imperative summary
```

Allowed types are `feat`, `fix`, `perf`, `docs`, `refactor`, `test`, `build`,
`ci`, `chore`, and `revert`. The scope and `!` are optional. Write titles in
English, use a lowercase type and scope, omit the final period, and keep the
title within 100 characters.

Examples:

- `fix(privacy): prevent identifiers in portable notes`
- `docs(sexology): clarify consent guidance`
- `feat(journal)!: revise workspace schema`

Use `!` and add a `BREAKING CHANGE:` footer to the pull request body when a
change is incompatible. `feat` normally leads to a minor release, `fix` and
`perf` to a patch release, and a breaking change to a major release.

The repository accepts squash merges only. GitHub uses the validated pull
request title as the single commit subject on `main`.
