# Security Policy

## Supported version

Only the latest release on the default branch is supported.

## Reporting a problem

Report security or privacy problems privately through GitHub's security
advisory feature for this repository. Do not include real journal content,
credentials, intimate media, raw correspondence, or identifying details. Use a
minimal fictional reproduction when possible.

## Security boundaries

This plugin does not include telemetry, an MCP server, external authentication,
or cloud storage. It cannot guarantee confidentiality provided by the host
model, local computer, backups, or a user-configured tool.

The plugin must contain only instructions, manifests, policies, and static
assets: no bundled scripts, executable files, shebang files, or symlinks. Its
mandatory journal policy stays in
`skills/psychology-journal/references/privacy.md` and is not copied into an editable
journal.

The skill intentionally omits `allowed-tools`. In Claude Code that frontmatter
field pre-approves listed tools; it does not restrict unlisted tools or block
Bash. A skill-scoped deny cannot therefore be created with that field. Users or
administrators who need a mechanical Bash or network restriction must enforce
it in the host's permission and sandbox policy. See Claude Code's
[skill tool-permission semantics](https://code.claude.com/docs/en/slash-commands#pre-approve-tools-for-a-skill)
and [deny-rule documentation](https://code.claude.com/docs/en/permissions).
The installed skill still forbids executing code from itself or a journal
during journal creation.

Journal creation must remain opt-in, non-destructive, and local. Changes that
add networking, analytics, automatic Git operations, destructive file behavior,
or external storage require an explicit privacy and threat review.
