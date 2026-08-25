---
name: psychology-journal
description: Manage Psychology Companion longitudinal continuity, private journal files, local or external private stores, remembered journal reconnection, handoffs, and protected Git commits. Use whenever the user asks to save personal session progress between chats, resume long-term work, connect an existing journal, or perform journal-related file or Git work, including when no journal path has been chosen yet. Do not use for an ordinary one-off consultation.
license: PolyForm-Noncommercial-1.0.0
---

# Psychology Journal

Provide persistence without turning storage into authority. Read and apply the
mandatory [privacy policy](references/privacy.md) before any journal access,
private-source access, file creation, handoff, or Git operation.

If `psychologist` is available, use it for substantive psychological reasoning
and this skill for continuity and storage. If it is unavailable, limit this
skill to journal management and do not present the result as a psychological
consultation. If `psychology-research` is unavailable, do not create evidence
briefs or supplemental-method records.

## Choose the mode before access

In a new conversation, a path, URL, repository owner, or journal fact supplied
by host context or cross-conversation memory is only an unverified locator. If
the user has not already chosen, offer one concise choice before opening it:

1. a one-off consultation using only the current chat, with no journal access
   or persistence; or
2. longitudinal continuity using the existing journal after verification.

The choice applies to the current conversation. Immediate safety overrides the
menu. Short mode performs no read, write, clone, fetch, commit, or use of
personal facts available only from previous conversations.

Longitudinal selection authorizes verification and minimum continuity reads
from a known local checkout. A remote-only locator still requires separate
permission for the exact clone or fetch and an exact destination. An
unavailable or invalid locator is not permission to create a replacement.

If this skill becomes available after a one-off conversation has begun and the
user selects longitudinal mode, the eventual session note may cover the whole
current conversation. Store a minimized structured summary, never a raw
transcript, and apply the strictest recording rule that occurred anywhere in
the conversation.

## Journal structure

Create a new journal only at an absent or empty user-authorized destination.
Refuse a symlink or non-directory, preserve all existing content, and never
initialize Git or a remote during creation.

```text
<journal>/
├── .gitignore
├── SOUL.md
├── case-formulation.md
├── case-timeline.md
├── assessment-plan.md
├── progress.md
├── next-session.md
├── therapy-backlog.md
├── sessions/
├── research/
├── methods/
└── private/                 # local default; ignored by Git
```

Initialize records only from the matching installed asset under
`assets/note-templates/`. Never copy schemas, policies, core methods, or a
`templates/` directory into the journal. `sessions/`, `research/`, `methods/`,
and `private/` start as actual empty directories with no placeholder files.

`SOUL.md` is a strict allowlist for the assistant's identity, voice, and
interaction style. It must contain no fact, identifier, preference, pronoun,
or form of address about the user or another person.

## Resume and update continuity

After the privacy checks pass, read only this baseline in order:

1. `SOUL.md`;
2. `case-formulation.md`;
3. `progress.md`;
4. `next-session.md`;
5. the most recent session relevant to the current topic;
6. `case-timeline.md` only when chronology or contradiction matters.

Open assessment, backlog, research, methods, or private sources only when the
current decision requires them. Missing `private/` after a clone does not make
the tracked journal invalid.

In longitudinal mode, close each substantive session with a minimized dated
session note and update formulation, progress, and next focus only when the
conversation supports a change. Invite correction. Never rewrite older records
to fit a new hypothesis.

When a material evidence question arises and `psychology-research` is
available, use it. A significant evidence brief may be stored automatically in
longitudinal mode; the journal skill applies privacy, path, staging, and commit
controls. Without the research skill, leave `research/` and supplemental
methods unchanged.

## Private-source modes

The default private store is `<journal>/private/`. It is device-local and
ignored by Git. Create it during new-journal initialization; after a clone,
create it only when the user chooses local private storage or private material
is actually needed.

An optional external private store is configured per device in the ignored
`.psychology-companion.local.json`. Read only the allowlisted schema defined in
the privacy policy. The plugin does not configure, authenticate, mount,
encrypt, or synchronize a provider. If the external store is unavailable,
continue from minimized tracked records, state the source gap only when
relevant, and never create a silent fallback or reconstruct raw content.

## Git and external actions

The only standing Git mutation is the protected local commit at substantive
session close when every condition in the privacy policy passes. Never
initialize Git, stage unrelated or pre-existing work, amend, rewrite history,
tag, push, or contact a remote under that standing behavior.

Every other commit and every clone, fetch, push, publication, handoff, upload,
message, copy of private material, or deletion requires authorization for the
exact operation, source, destination, and content. End file work with the main
outcome, links only to changed files, the next focus, and a commit identifier
only when a commit actually succeeded.
