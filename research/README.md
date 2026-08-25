# Development Evidence Archive

This directory preserves the psychological and sexological evidence used to
design Psychology Companion's professional stance, methods, and safety rules.
It exists for maintainers, reviewers, and auditors. It is not runtime skill
content, user journal data, a questionnaire library, or a source that an agent
should load before answering an ordinary user request.

The archive supports traceability and review of the project's evidence basis.
It does not make the plugin a licensed psychologist, psychotherapist,
sexologist, physician, validated treatment, diagnostic system, or certified
clinical product. Most sources concern trained human professionals or public
health systems; transferring a conservative principle into an AI instruction
does not establish equivalent safety or effectiveness.

## Scope

Include research that materially supports psychological or sexological
knowledge expressed by the shipped skills, including professional
communication, reasoning, formulation, methods, safety, sexual health,
psychometrics, and clinically derived record structures.

Do not include research about prompt writing, skill architecture, agent design,
plugin packaging, Git workflows, marketplace behavior, CI, or model selection.
Do not include user records, transcripts, case material, copyrighted manuals,
questionnaire items, scoring keys, or full-text articles.

## Runtime boundary

Nothing in `skills/` should require this directory for normal operation. Skill
files may retain current operational links needed during a conversation, such
as emergency resources, specialist directories, official instrument terms, or
current medical and legal guidance. Academic provenance and literature-review
detail belong here.

The user-facing `psychology-research` skill must not discover or load this
archive before answering a user. Its existing-research preflight applies only
to an explicitly authorized user journal. Updating this development archive is
a maintainer task: research may be requested, but a human-reviewed repository
change records the result.

## Maintenance

Start with [index.md](index.md). Each brief records the evidence snapshot date,
affected runtime files, limitations, and update triggers. A date indicates when
the project reviewed or migrated the evidence; it is not proof that every link
or conclusion remains current. Before changing a foundational instruction,
recheck the decision-relevant sources and record what was confirmed, changed,
superseded, or remains uncertain.

Use Git history for authorship and revision history. Update the brief and its
index row in the same pull request as any corresponding instruction change.
