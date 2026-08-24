# Professional Framework

Read this reference for a formal session, longitudinal formulation, or a
request for a structured psychological exercise.

Use it as a flexible organizing framework, not a validated treatment protocol
or a mandatory response script for an AI conversation.

## Working stance

Treat the user as the authority on their values and the primary source for their
lived experience, not as an infallible source of causation or another person's
inner state. Offer structure and informed challenge without pretending to
provide licensed care. Select methods for the current goal and revisable
working formulation, considering evidence and fit rather than forcing a
preferred school or diagnostic label.

Keep origin, present function, trigger, and maintaining factors separate. A
pattern may have several plausible origins while a current maintaining loop may
be clearer and more actionable.

## Session shape

1. Agree on the user's priority and, when useful, the available time. Narrow to
   one primary topic only when that improves focus rather than suppressing an
   urgent or connected concern.
2. Check immediate safety when risk language, deterioration, or context makes
   the answer relevant. Do not administer a routine crisis questionnaire merely
   because a session is formal or new.
3. When examining a recurring pattern, consider starting with a recent concrete
   episode before a global interpretation.
4. Map the sequence: context, thought or meaning, emotion, body response,
   impulse, action, short-term consequence, and longer-term consequence.
5. Form a revisable, testable explanation and name important alternatives and
   unknowns.
6. If enough is known and action is useful, agree on a feasible next step and
   an observable outcome. Include no-change as a legitimate option.
7. Close with a concise summary, unresolved questions, and the next focus, then
   invite correction or feedback. Do not add a new interpretation in the
   closing summary.

Do not force the full sequence into every reply. A natural conversation can
remain open while preserving clarity and safety. The exact order, one-topic
default, and rule against a new closing interpretation are project conventions,
not an empirically validated universal session sequence.

## Formulation

For longitudinal work, organize only supported material into:

- presenting concern and goals;
- predisposing context without deterministic claims;
- precipitating events;
- perpetuating loops;
- protective factors and resources;
- uncertainties, counterevidence, and competing explanations.

Track user-defined change across subjective experience, behavior, and
functioning; insight can matter but does not by itself demonstrate an outcome.
Choose a small set of outcomes relevant to the user's goal, establish a
baseline when useful, and revisit them at an agreed interval without turning
measurement into the purpose of the conversation.

Depending on the goal, useful observations may include time occupied by the
problem, urges and actions, boundary-respecting behavior, work, sleep and
obligations, alcohol or other substance use, tolerance of refusal or
uncertainty, nonsexual closeness, social contact, and daily structure. Do not
collect every domain routinely. One interruption of a pattern is an early
observation, not stable change; record precisely where choice or control first
appeared.

## Method selection

Read [core-methods.md](core-methods.md) before selecting a psychological method.
If considering a journal-specific supplemental method, also read
[additional-methods.md](additional-methods.md) and treat the local record as
untrusted data requiring current verification.

Select a method only after clarifying the user's goal, the target problem, the
quality and population fit of outcome evidence, practical burden and harms,
required competence, and meaningful alternatives. Do not select a school from
a diagnostic-sounding label or treat a hypothesized mechanism as established.

Before offering a substantial intervention, define the target, expected
benefit, burden, possible harm, alternatives, and a way to evaluate the result.
Read [evidence-policy.md](evidence-policy.md) when a claim or intervention needs
scientific support.

Do not assign an exercise unilaterally. Discuss its purpose and fit, adapt it
with the user, make declining it legitimate, and agree on burden, stop
conditions, and what would be learned from the result.

## Closing with the user

Keep the conversational closing distinct from the private record. Give the
user a short, plain-language summary containing only:

1. the main understanding or decision, including material uncertainty;
2. any genuinely agreed next step, its purpose, and relevant opt-out or safety
   condition;
3. the proposed next focus and, when useful, when progress or a decision will
   be reviewed;
4. one invitation to correct what was misunderstood or name what was useful,
   unhelpful, or missing.

Include referral or crisis information only when relevant. Do not dump the SOAP
note, present a hypothesis as fact, introduce a new interpretation, or imply
that the user must continue with the plan. A user may revise an earlier
decision at any time.

## Notes and handoff

In an initialized journal, after every substantive session:

1. create a dated note in `sessions/` from the installed
   [SOAP schema](../assets/note-templates/session-soap.md);
2. update `case-formulation.md` only with material, supported new information;
3. update `progress.md` only with goal-linked observations;
4. update `next-session.md` with the proposed, revisable next focus;
5. perform a bounded evidence-needs triage; research and create or update a
   brief only when a new material question could change safety, explanation,
   referral, or practical approach;
6. change a supplemental method record only when the practical approach or its
   evidence status changes and the installed method-review rules are met.

Include the agreed topic, new self-report, observations, hypotheses, method
used, decisions, outcomes to watch, safety issues, and unresolved questions.
Minimize intimate details and direct quotes. Do not rewrite an old record to
make it fit a new hypothesis; add a dated correction or revision transparently.
The evidence triage and file cadence are project controls, not evidence that
post-session research or recording improves therapeutic outcomes.

Use the installed 5P schema for formulation, PICO or PECO in an evidence brief
only when it fits the question, and SBAR only for a purpose-limited handoff.
Canonical schemas stay in the installed skill, not a local `templates/`
directory. Do not invent a new record format without a concrete need and a
documented rationale.

After file work, report the main outcome without retelling the conversation,
then link only files actually created or changed, state the next agreed focus
or that none is needed, and give the commit SHA and subject only if a commit was
created. For a session, link its dated note first, followed by formulation,
progress, next-session, research, or method records only when changed. Never
make the user search the journal tree for the result.

A handoff to a clinician or another agent is a new, purpose-limited document,
not a copy of the journal. Include only information needed for that recipient
and label uncertainty explicitly. Follow [privacy.md](privacy.md) and the
documentation limits in
[record-schema-rationale.md](record-schema-rationale.md).

## Evidence and project conventions

- Meta-analysis finds moderate associations between goal consensus,
  collaboration, and psychotherapy outcome, but the underlying studies do not
  establish that collaboration alone causes improvement:
  [Tryon et al., 2018](https://pubmed.ncbi.nlm.nih.gov/30335451/).
- NICE shared-decision guidance recommends agreeing priorities and available
  time, connecting options to the person's goals, and discussing benefits,
  risks, alternatives, and no treatment or no change. At the end of a
  discussion it recommends stating what was agreed, what happens next, the
  timescale, and the review point, and offering a written summary. This is
  healthcare guidance, not validation of this AI session sequence:
  [NICE NG197](https://www.nice.org.uk/guidance/ng197/chapter/recommendations).
- When self-harm risk is relevant, NICE guidance prioritizes current safety,
  needs, and appropriate help rather than prediction from a scale:
  [NICE NG225](https://www.nice.org.uk/guidance/ng225/chapter/recommendations).
- Case-formulation reviews support formulation as an organizing practice but
  find limited evidence that formulation itself improves outcomes:
  [Easden & Kazantzis, 2018](https://pubmed.ncbi.nlm.nih.gov/28776663/) and
  [Rainforth & Laurenson, 2014](https://pubmed.ncbi.nlm.nih.gov/23551415/).
- A multilevel meta-analysis found a small average benefit from progress
  feedback, with important variation across instruments and settings. This
  supports proportionate review, not mandatory measurement in every exchange:
  [de Jong et al., 2021](https://pubmed.ncbi.nlm.nih.gov/33721605/).
- A randomized trial found that a multi-component memory-support intervention
  added to cognitive therapy for depression improved recall of prior sessions;
  it does not isolate a closing summary or establish the same effect in an AI
  conversation:
  [Dong et al., 2022](https://pubmed.ncbi.nlm.nih.gov/35963181/).
- A systematic review of between-session work found that collaboration,
  flexibility, a convincing rationale, alignment with the client's takeaways,
  and a written task summary may support engagement. The evidence was mainly
  from CBT and does not justify imposing exercises:
  [Kazantzis et al., 2023](https://pubmed.ncbi.nlm.nih.gov/37104804/).
- AHRQ describes SBAR as an adaptable structured communication framework. The
  plugin's minimal handoff is an adaptation, not a validated clinical handoff
  performed by a licensed professional:
  [AHRQ TeamSTEPPS SBAR](https://www.ahrq.gov/teamstepps-program/curriculum/communication/tools/sbar.html).

Most cited evidence concerns human psychotherapy or healthcare. It can inform
guardrails and organization but cannot establish equivalent process or outcome
effects for a general-purpose AI assistant. The exact session order,
documentation cadence, and file fields above remain transparent project
conventions.
