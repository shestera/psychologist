# Record Schema Rationale

Read this reference when creating, changing, reviewing, or explaining a bundled
record schema. It documents why the schemas have their present shape and where
the borrowed structures come from.

## Status and limits

There is no single international format for every psychological record. These
schemas are a project standard that combines several established documentation
structures for different purposes. They organize information; they do not
validate an intervention, establish a diagnosis or causal mechanism, turn this
AI skill into a clinician, or create a medical record.

Professional record-keeping duties depend on role, setting, jurisdiction, and
law. The APA Record Keeping Guidelines linked below were archived by APA in
August 2019. Use them only as historical professional context about accurate,
current, pertinent, secure, and purpose-sensitive records—not as current law,
active APA policy, or authority for this AI journal.

## Schema choices

- `session-soap.md` adapts Subjective, Objective, Assessment, and Plan to a text
  interaction. Weed's problem-oriented medical record is a historical
  antecedent, not evidence that this adapted note improves psychological
  outcomes. “Objective” is therefore limited to observable features of the
  current interaction, and “Assessment” remains a revisable formulation.
- `case-formulation-5p.md` uses Presenting, Predisposing, Precipitating,
  Perpetuating, and Protective categories reflected in an NHS formulation aid.
  Formulation reviews find limited evidence that formulation itself improves
  outcomes, so the schema requires alternatives, counterevidence, uncertainty,
  and no diagnostic claim.
- `case-timeline.md` keeps chronology separate from the current formulation.
  This is a project safeguard against treating temporal order alone as
  causation, not a standardized clinical template.
- `research-evidence-brief.md` may use PICO or PECO to focus a question and a
  GRADE-informed account of evidence certainty. Do not assign a formal GRADE
  rating without the required body-of-evidence appraisal, and never convert an
  evidence rating into certainty about one user.
- `handoff-sbar.md` adapts AHRQ's Situation, Background, Assessment, and
  Recommendation or Request structure for a minimal, user-authorized handoff.
  It omits unnecessary identifiers and asks the recipient to assess
  independently rather than transmitting an AI diagnosis.
- `progress-review.md` records user-defined outcomes, a baseline, repeated
  observations, uncertainty, fit, and burden. Change in a chosen measure is
  evidence about that measure, not by itself a diagnosis or proof of cause.
- `assessment-plan.md`, `next-session-plan.md`, `therapy-backlog.md`,
  `assistant-preferences.md`, and `journal-gitignore.md` are project controls
  rather than internationally standardized clinical formats. `method-note.md`
  is the review record for a journal-specific supplemental method, not a
  treatment manual or evidence of recognition; its append-only revision table
  keeps method changes transparent without a separate local changelog. Together
  they preserve purpose, consent, continuity, privacy, alternatives, and the
  installed skill's absolute medication-recommendation boundary.

## Application rules

- Keep all schemas in the installed skill. Write only initialized or completed
  user-data records to the journal; omit prompts and explanatory guidance.
- Use only the schema needed for the current record. A heading is not a fact
  about the user, and an empty field is not evidence that a topic was assessed.
- Label provenance and uncertainty, minimize sensitive detail, and keep a raw
  source separate from a derived note.
- Do not rewrite historical records merely for visual consistency. Apply a new
  schema on the next substantive update while preserving meaning and revision
  history.
- A schema never authorizes an intervention, disclosure, diagnosis, medication
  recommendation, or external action.

## Sources

Links checked 2026-08-24.

- SOAP/POMR historical antecedent: Lawrence L. Weed, “Medical Records That Guide
  and Teach,” *New England Journal of Medicine* (1968),
  [DOI 10.1056/NEJM196803212781204](https://www.nejm.org/doi/10.1056/NEJM196803212781204).
- 5P practical aid:
  [CNTW NHS Foundation Trust, 5Ps mental-health and wellbeing resource](https://www.cntw.nhs.uk/resources/understanding-what-influences-your-mental-health-and-wellbeing-5ps).
- Case-formulation evidence limitations:
  [Easden & Kazantzis (2018)](https://pubmed.ncbi.nlm.nih.gov/28776663/) and
  [Rainforth & Laurenson (2014)](https://pubmed.ncbi.nlm.nih.gov/23551415/).
- Causal inference and temporality:
  [Fedak et al. (2021)](https://pubmed.ncbi.nlm.nih.gov/33324996/).
- Evidence questions and certainty:
  [GRADE Book, GRADE Working Group](https://book.gradepro.org/).
- Structured handoff:
  [AHRQ TeamSTEPPS SBAR](https://www.ahrq.gov/teamstepps-program/curriculum/communication/tools/sbar.html).
- Screening versus diagnosis:
  [Levis et al. (2020)](https://pubmed.ncbi.nlm.nih.gov/30894161/).
- Preference-sensitive decisions:
  [Hoffmann et al. (2014)](https://pubmed.ncbi.nlm.nih.gov/24999896/) and
  [Lindhiem et al. (2014)](https://pubmed.ncbi.nlm.nih.gov/25189522/).
- Historical professional record-keeping context, explicitly archived in 2019:
  [APA Record Keeping Guidelines](https://www.apa.org/practice/guidelines/record-keeping).
