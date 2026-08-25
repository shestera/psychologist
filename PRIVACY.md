# Privacy

Psychology Companion is an instruction plugin. It has no bundled MCP server,
telemetry, cloud database, or synchronization service. The host model and tools
may still process content according to their own settings and privacy terms.

## Public plugin and private journal

Keep the public plugin separate from every user's journal. A journal may
contain sensitive psychological, relationship, sexual, or health information.
Do not place journals inside this repository, use them as examples, or include
their content in bug reports.

Persistent storage is provided only by the independently configurable
`psychology-journal` skill. A verified journal already active as the authorized
workspace or connected source automatically establishes longitudinal mode and
standing documentation; the assistant does not ask whether to save each new
chat. If the skill is unavailable, it cannot read or write that journal.

Journal creation uses the host's ordinary file tools and bundled record schemas.
It:

- begins only after the user chooses a destination;
- requires an absent or empty destination;
- never overwrites existing files;
- never initializes Git or configures a remote;
- creates a device-local `private/` directory excluded by the journal's
  `.gitignore`;
- keeps bundled record schemas inside the installed skill instead of copying a
  `templates/` directory into the journal;
- creates an empty `methods/` directory for later source-checked supplemental
  method records, never local rules or copies of core methods;
- initializes minimized session, research, and method indexes so later chats
  can select exact records without scanning complete archives; and
- does not execute code bundled with the skill.

If the authorized journal root is already its own Git repository, closing a
substantive session automatically creates a local commit only when the
session's changed paths are isolated from pre-existing work and pass privacy
checks. The commit message is generic. The plugin never initializes Git, stages
unrelated changes, rewrites history, tags, pushes, or contacts a remote as part
of session closure; if the protected commit cannot be made, changes remain
uncommitted and the blocker is reported.

A repository merely remembered from another conversation is an unverified
locator, not an active journal. It is not opened or contacted until it is
reconnected. A remote-only URL still requires separate permission and a
destination before clone or fetch. Failure to reconnect an existing journal
never authorizes creation of a replacement. Only when no connected or
remembered journal data is available does the assistant offer an initial choice
between one-off conversation and creating or connecting longitudinal storage.
One-off mode performs no journal or Git operation. An explicit request not to
record overrides standing documentation without authorizing silent deletion of
an already-written draft.

Raw or identifying sources stay outside Git. The default store is the ignored
`<journal>/private/` directory on the current device. A missing ignored
`private/` after a fresh clone is expected and does not invalidate tracked
continuity records.

The user may instead authorize an external directory through an ignored
per-device `.psychology-companion.local.json`. The pointer is never committed,
must not point into a Git worktree, and does not grant permission to copy or
open every file. The plugin does not provide or claim encryption,
authentication, mounting, synchronization, or confidentiality for an external
provider. If that directory is unavailable in a cloud or another-device
session, work continues from minimized tracked records without a silent
fallback or reconstruction of raw content.

Private data is never migrated automatically. Copying requires separate
authorization for the exact source, destination, and content, and does not
delete the source.

The mandatory
[privacy and journal security policy](skills/psychology-journal/references/privacy.md)
stays inside the installed skill. It is not copied into the journal, where it
could be edited or accidentally weakened.

Pseudonymization reduces exposure but does not guarantee anonymity. Rare life
events, exact dates, and combinations of personal details may still identify a
person.

## Sharing and deletion

Before sharing any journal material, create a new minimal extract for the exact
recipient and purpose. Remove direct identifiers, unnecessary intimate detail,
recognizable dates, raw messages, media, and credentials.

Deleting a working file may not remove copies from Git history, remotes,
external private stores, synchronized providers, backups, model-provider
retention, or prior exports. Confirm the required scope before promising
deletion.

## Incident reporting

Do not open a public issue containing personal data. Follow
[SECURITY.md](SECURITY.md) for private vulnerability or privacy reports.
