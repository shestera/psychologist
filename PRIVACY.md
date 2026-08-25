# Privacy

Psychology Companion is a local instruction plugin. It has no bundled MCP
server, telemetry, cloud database, or network service. The host model and tools
may still process content according to their own settings and privacy terms.

## Public plugin and private journal

Keep the public plugin separate from every user's journal. A journal may
contain sensitive psychological, relationship, sexual, or health information.
Do not place journals inside this repository, use them as examples, or include
their content in bug reports.

Journal creation uses the host's ordinary file tools and bundled record
schemas. It:

- begins only after the user chooses a destination;
- requires an absent or empty destination;
- never overwrites existing files;
- never initializes Git or configures a remote;
- creates a `private/` directory excluded by the journal's `.gitignore`;
- keeps bundled record schemas inside the installed skill instead of copying a
  `templates/` directory into the journal;
- creates an empty `methods/` directory for later source-checked supplemental
  method records, never local rules or copies of core methods; and
- does not execute code bundled with the skill.

If the authorized journal root is already its own Git repository, closing a
substantive session automatically creates a local commit only when the
session's changed paths are isolated from pre-existing work and pass privacy
checks. The commit message is generic. The plugin never initializes Git, stages
unrelated changes, rewrites history, tags, pushes, or contacts a remote as part
of session closure; if the protected commit cannot be made, changes remain
uncommitted and the blocker is reported.

The mandatory
[privacy and journal security policy](skills/psychologist/references/privacy.md)
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
backups, model-provider retention, or prior exports. Confirm the required scope
before promising deletion.

## Incident reporting

Do not open a public issue containing personal data. Follow
[SECURITY.md](SECURITY.md) for private vulnerability or privacy reports.
