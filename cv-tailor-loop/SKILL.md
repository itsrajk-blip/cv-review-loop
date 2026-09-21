---
name: cv-tailor-loop
description: "Run a heavyweight 4-round CV builder/reviewer loop (isolated BUILDER, ATS REVIEWER, HUMAN REVIEWER, and ACCURACY REVIEWER roles, hard zero-fabrication gate, stop conditions) plus a Step 5 Format & Structure Review, for a specific position description. Use this ONLY when explicitly asked for the full review loop - not for routine 'tailor my CV for X' requests, which should go through a faster single-pass flow instead. This skill is deliberately slower and more thorough (multiple isolated review rounds, independent scoring, a mechanical format check) and is meant for a small number of higher-stakes applications, not every application."
---

# CV Tailor Loop

This skill runs a 4-round CV content loop with four isolated roles
(BUILDER, ATS REVIEWER, HUMAN REVIEWER, ACCURACY REVIEWER), followed by a
one-time Step 5 mechanical format check. It exists because for high-stakes
applications, a single-pass tailored CV doesn't get the same adversarial
scrutiny a real hiring process would apply - this workflow builds that
scrutiny in deliberately, at the cost of being slower and more expensive
to run.

This skill builds and reuses a per-candidate **setup**: their facts
source, their authenticity anchors, and their CV structure rules (learned
from real examples, not asked for as abstract rules). The first time you
run this for someone, expect a short setup conversation. Every run after
that should need little or no re-asking - read the saved setup first, and
only ask about what's actually missing or looks stale.

If the candidate has a faster, single-pass CV tailoring flow already,
keep this as the optional heavier overlay reached for on purpose, not the
default - running the full loop on a routine application wastes time and
tokens for no real benefit, and a single pass on an application the full
loop was wanted for under-delivers. If unclear which one a request wants,
ask rather than assuming.

## Setup (check this before round 1, every single run)

Before doing anything else, look for a saved setup file for this
candidate (see "Saving setup for future runs" below). Two things need to
exist before the loop can run properly. For each one: if it's already
saved, use it silently; if it's missing or looks stale, ask for it now -
don't guess, and don't start drafting on an assumption.

1. **Sample CVs** - ask for at least one real CV, ideally their most
   complete/current one. If they have more, ask them to share up to five:
   past applications they were genuinely happy with, at different
   seniority framings if they have them. No fixed minimum beyond one -
   don't block on getting a large set, one is enough to start from, more
   just makes the structure and facts-pool inference more reliable. Don't
   ask separately for a "master facts document" - most people don't
   maintain one distinct from whatever they last applied with, and asking
   for it as its own artifact just adds friction for something the sample
   CVs can already supply. These same samples do double duty: they're
   both the facts source (see "Building the facts pool" below) and what
   the CV structure rules get learned from (see "Learning CV structure"
   below).

   The one exception: if the candidate says they *do* keep a maintained
   master/achievements doc separate from their applied CVs, use that as the
   primary facts source directly rather than reconstructing one - it's
   already the more authoritative version.

2. **Authenticity anchors** - a running list of buzzwords, phrases, or
   writing patterns to flag as inauthentic/AI-sounding. Optional but
   valuable. If none saved yet, ask once: "Any specific words, phrases,
   or writing tics you want flagged as inauthentic or AI-sounding? If
   not, this can start empty and I'll add to it as we catch things." Do
   not block the loop on this - an empty anchors list is fine to start.

**Employment timeline** is not asked for separately - extract it from the
sample CVs' own dates, then show it back for a one-line confirmation
("I'm reading your timeline as: [X], [Y], [Z] - that right?"). This is
what the ACCURACY REVIEWER uses for chronology checks later.

If everything needed is already saved and looks current, say so briefly
and move straight to "Before starting" - don't re-run the setup
conversation just because the skill fired again.

### Building the facts pool from sample CVs

When there's no separate maintained master doc, build the facts pool by
reading all the sample CVs together, not just the newest one - older
samples often carry roles or bullets a newer, more targeted CV cut for
space, and a cut bullet is still a real fact worth keeping in the pool
even if the most recent CV doesn't mention it.

If only one CV was shared, there's nothing to cross-check it against -
build the facts pool from it directly, but say plainly that it's a
single-source pool: anything the loop later treats as "confirmed" is only
as reliable as that one document, and any older role or achievement it
doesn't mention won't be in the pool until the candidate adds it. The
conflict-checking below only starts doing real work once 2+ CVs are in
play.

**Do not silently merge conflicting claims.** Two samples describing what
looks like the same achievement with different numbers, scope, or wording
is a real, common failure mode (a metric that drifts between edits is
exactly the kind of thing the ACCURACY REVIEWER later hard-gates on) - so
when sample CVs disagree, list the conflict explicitly and ask which one
is current: "Your Company X CV says a 20% lift here, your Company Y CV
says 25% for what reads like the same result - which is right?" Never
pick the more recent file as automatically correct without asking; recency
doesn't guarantee accuracy, a stale bullet gets copy-pasted forward as
often as it gets fixed.

A role or company that appears in an older sample but not a newer one
isn't automatically a conflict - it may just be a space cut - but flag it
once rather than silently dropping it from the facts pool or silently
keeping it: "I see a Company Z role in your 2023 CV that isn't in your
two most recent ones - still relevant to include, or intentionally
retired?"

Once reconciled, this becomes the facts pool BUILDER writes from and
ACCURACY REVIEWER audits against - same role either way, whether it's a
document the candidate already had or one built here from their samples.

### Learning CV structure from example CVs

Read the same sample CVs and extract, rather than ask for:

- **Section order** - whatever sections the candidate's own CVs actually
  use, under whatever names they use for them, and in what sequence.
  Don't assume any particular section exists (no fixed template of
  "summary + skills + experience" or anything else) - read it straight
  off the samples.
- **Per-section length and format** - for each section that uses bullets
  or entries, the typical count and whether it ever varies (e.g. 3 by
  default, 4 on one example - note that as a real variation, not noise,
  and ask why if it isn't obvious from context). If a section groups its
  content into named sub-categories, note how many and how they're
  labelled, and whether the labels shift by role type - but only if the
  candidate's own CVs actually do this, don't introduce a category
  structure that isn't there.
- **Title-framing logic** - if examples exist at different seniority
  levels or for different target roles, how the headline/title changes
  between them. This is often the most valuable thing to catch: people
  frequently frame up or down depending on the target role, and getting
  this wrong (defaulting to one fixed framing) is a common tailoring
  mistake.
- **Style fingerprints** - punctuation choices (dash style, multiplier
  notation), sentence length and rhythm, any phrases that show up
  consistently, capitalisation/date-format conventions.
- **Employment timeline** - company names, titles, and dates, read
  straight off the master CV.

Then state back a short, numbered summary of what was inferred and get a
one-line confirmation before treating any of it as settled - e.g. "Here's
what I'm seeing: your CVs always run [Section A] → [Section B] → [Section
C] in that order, [Section A] normally has 3 bullets, title stays as your
actual current title unless the target role is genuinely a level up.
Does that match how you think about it, or is there a case where it
varies that I'm not seeing here?"

If only one example CV is provided, say so plainly and flag the inferred
rules as provisional ("I'm inferring 3 bullets in [Section A] is your
standard since that's the only example I have - flag it if it varies by
role level"). Don't present a single-example inference with the same
confidence as a pattern confirmed across several examples.

### Saving setup for future runs

Once gathered or inferred and confirmed, save it as a compact, durable
setup record so future runs don't re-ask or re-analyze from scratch.
Where exactly depends on what's available in the environment this skill
is running in - a persistent memory/notes system if one exists, otherwise
a plain file (e.g. `cv-tailor-loop-setup.md`) kept alongside the
candidate's other CV materials. Whatever the mechanism, it needs to
survive between separate runs of this skill, not just within one
session.

What it should hold:
- The facts pool itself (whether that's the candidate's own maintained
  master doc, or the reconciled pool built from their sample CVs), plus
  any conflicts that got flagged and how they were resolved - so the same
  conflict doesn't need re-asking next time a new sample surfaces it.
- The confirmed CV structure rules (section order, per-section length and
  any known variation, any sub-category structure a section actually
  uses, title-framing logic, style fingerprints), and which example CVs
  they were learned from.
- The employment timeline table.
- The authenticity anchors list, kept as compact rule-name + one-line
  statements, not full explanatory prose (see the HUMAN REVIEWER section
  for why compactness matters here specifically).
- Any Step 5 formatting pitfalls discovered while producing a real
  document (see Step 5 below) - this list is worth persisting too, the
  same way authenticity anchors are.

At the start of every run: read this first. Use it silently unless
something in the current PD or draft genuinely conflicts with a saved
rule (a target role that plausibly needs a different structure, say) -
in that case flag the deviation and ask, rather than silently overriding
what was previously confirmed.

Update it, don't just re-save it wholesale, when: the candidate gives a
new authenticity anchor ("also flag X"); corrects an inferred structure
rule ("actually I always use 4, that one CV was the exception"); approves
a new tailored CV that reveals a new precedent worth remembering; or a
new Step 5 formatting pitfall gets discovered. Treat this file the way an
experience bank is treated elsewhere - it accumulates value across runs,
so merge additions in rather than overwriting wholesale each time.

## Before starting

You need the position description (PD) - attached, pasted, linked, or
already saved somewhere - and, ideally, confirmation of which company/role
this is for so file names and any folder paths are right. If the PD isn't
available yet, ask for it before doing anything else.

## Overall structure

Four roles run through 4 content rounds, then one Step 5 check runs once.
The critical property: BUILDER, ATS REVIEWER, HUMAN REVIEWER, and ACCURACY
REVIEWER never share reasoning with each other, only finished files.

- **BUILDER**: writes the CV draft. Has full context, including the saved
  setup.
- **ATS REVIEWER**: mechanically scores keyword/format match against the
  PD. Fully isolated - gets nothing but the draft and the PD.
- **HUMAN REVIEWER**: skeptically scores shortlist chance and
  authenticity. Fully isolated from the builder's reasoning *and* from
  the facts source - it never sees the master CV or any past CV, only the
  PD, the draft, and the authenticity anchors from the saved setup.
  Deliberately kept blind to whether anything is true, because judging
  shortlist-worthiness and authenticity is an impression call a real
  hiring manager makes with zero access to the candidate's actual facts,
  and mixing that impression call with a citation audit risks one signal
  drowning out the other.
- **ACCURACY REVIEWER**: the one role with access to the facts source.
  Fully isolated from the builder's reasoning and from the PD - its only
  job is checking the draft's claims against the master facts source(s)
  from the saved setup. This is a citation audit, not a plausibility
  judgment, and it's the role the hard zero-fabrication gate is tied to.
- **FORMAT & STRUCTURE REVIEWER (Step 5)**: runs once, after the content
  loop concludes. This one is *not* isolated like the other three
  reviewers - its job is mechanical and deterministic (page count,
  formatting integrity, typography), not a subjective judgment, so it
  needs full access to the known document-format pitfalls from the saved
  setup rather than reasoning-isolation.

The orchestrating session (you, the AI) can act as BUILDER directly -
there's no isolation benefit to spawning it separately, since it already
has full context. Isolation matters for the three *reviewers*, so spawn
those as fresh sub-agents each round, and don't assume a spawned
sub-agent can reliably self-filter what context it's "allowed" to use -
instead, paste the curated context directly into each sub-agent's prompt.

## Scope of the content loop (rounds 1-4)

Rounds 1-4 operate on CV **content only** (a markdown/text draft).
Document mechanics - pagination, page count, formatting-tool quirks,
preserving any header/footer elements, PDF export - are checked in Step
5, once, after a draft is accepted, not scored as part of these rounds.
Content quality and document mechanics are different failure classes;
scoring them together risks optimizing for one at the expense of the
other.

## Inputs

- **MASTER FACTS**: the facts pool from the saved setup - either the
  candidate's own maintained master doc, or the reconciled pool built
  from their sample CVs during setup. Every claim in the draft must trace
  to this, or to a fact the candidate supplies fresh this session -
  nothing else is allowed. Used by BUILDER (to write and cite from) and
  ACCURACY REVIEWER (to audit against) - HUMAN REVIEWER never sees this.
- **PAST TAILORED CVs** (optional): if the candidate keeps past finalized
  CVs somewhere, these are a reuse/reframe layer, not a facts source in
  their own right - see the BUILDER instructions below for how to use
  them safely. ACCURACY REVIEWER gets the full text of any past CV the
  draft cites with a "Reframed from" tag, to verify the reuse is safe;
  HUMAN REVIEWER does not need these.
- **POSITION DESCRIPTION**: from the candidate, this round. Used by
  BUILDER, ATS REVIEWER, and HUMAN REVIEWER (for shortlist fit) -
  ACCURACY REVIEWER does not need it, since matching claims to facts has
  nothing to do with the target role.
- **CV STRUCTURE RULES**: from the saved setup, learned from example CVs
  during setup (see above) - not invented or asked for as abstract rules.
- **AUTHENTICITY ANCHORS**: from the saved setup. Used only by HUMAN
  REVIEWER. Fine to start empty and grow across runs.

## BUILDER instructions (per round)

Tailor the CURRENT BEST DRAFT to the PD. Round 1's starting point is
normally the master CV, but if a past tailored CV is a genuinely closer
scope/framing match to this PD than the master is, use that CV as the
round 1 base instead - the master isn't mandatory as the literal starting
text, it's mandatory as the ultimate fact source everything must still
trace back to.

**Structural checklist** - use the CV structure rules from the saved
setup so reviewers aren't relitigating structure every round. All
sections of the tailored CV should match the sections that appear in the
candidate's own base CVs - same sections, same order, same general
shape - not a structure invented for this skill:
- Section order and per-section length: the learned defaults from the
  saved setup, only deviate if the PD genuinely needs it.
- Any sub-category structure a section actually uses in the candidate's
  base CVs: the learned count and pattern; only add more with a clear
  reason.
- Title framing: match the target role's actual level, using the learned
  title-framing logic. State the framing decision in one line at the top
  of the draft file (e.g. "Framed at current level - PD reads as
  senior-IC, not a step up") so reviewers can sanity-check the *decision*
  without needing the deliberation that led to it.
- Any headline theme the candidate sometimes leans into or drops (an
  AI-forward framing, a domain specialism, etc.) - state whether it's
  included and why, same as title framing.
- Style rules and banned phrases from the saved setup and the
  authenticity anchors.

If the PD genuinely seems to need a structural deviation from the saved
setup (a different section structure, a title-framing call that doesn't
match the learned pattern), flag it as a deliberate one-line decision
rather than silently drifting from what was previously confirmed - and
mention it's worth adding to the setup file if it turns out to be a real
recurring pattern rather than a one-off.

**Reuse and reframe past CVs** (if kept) - don't draft from the master
alone every time. Before drafting, scan for a past tailored CV whose
target role is close in level, scope, or theme to this PD. Where a past
bullet or section entry already says what this PD needs, in wording
that's already been through review and approved, reuse or lightly
reframe it rather than re-deriving a new sentence from the raw master
facts. Two patterns for how much to reuse:
- **Whole-CV base**: when an existing tailored CV's overall scope and
  framing genuinely matches the target role (not just a similar job
  title), copy that CV as the round 1 starting point instead of the
  master.
- **Cherry-pick**: when only the framing is close but the underlying
  scope differs, start fresh from the master and pull in individual
  bullets/entries piecemeal.

Never treat a past CV's wording as automatically current. Cross-check
anything reused against the present-day master facts before reusing it -
past CVs can carry wording the master has since superseded. If a past CV
and the current master disagree, the master wins.

**Citation format**: every bullet gets a bracketed source tag - e.g.
`[Master CV, <Company> bullet 2]`, `[Reframed from <Company> CV, <Section>
entry 2 - verified current against master]`, or `[New fact confirmed this
session]` if it's genuinely new. No bullet without a tag. A "Reframed
from" tag still needs the underlying fact to trace back to the master -
reusing another CV's wording doesn't exempt a claim from the fabrication
check, it just means the phrasing has precedent.

Every claim must trace to something in the master facts. Do not invent or
round up numbers, scope, or seniority. Do not genericise an established
specific descriptor into a vaguer synonym even if it reads "cleaner" -
specificity is the point, not a style preference.

Match the candidate's established writing style, as read from the setup's
style fingerprints and past finished CVs.

If prior-round reviewer notes exist, address each one explicitly - notes
come from three separate reviewers (ATS, Human, Accuracy), so check all
three sets. If a note would require fabricating something not in the
master facts, or would require genericising a specific detail to satisfy
a keyword match, flag the conflict instead of complying - don't silently
trade authenticity for an ATS score.

## ATS REVIEWER instructions (per round)

Fully isolated: give it only the draft text and the PD, nothing else - no
style guidelines, no builder notes, no master CV, no authenticity
anchors. Stay purely mechanical. **This is the cheapest role in the loop
by design - resist the urge to hand it "just a little more context" for a
better-informed score.** It doesn't need to be well-informed, it needs to
be a cold keyword scan, the same way a real ATS or a recruiter skimming
200 applications would be. If a prompt for this role is pushing past
roughly PD length + draft length combined, something's been added that
doesn't belong.

Score 1-10 on likely ATS shortlist probability, cold, as if this is one
of 200 applications. Extract PD keywords/skills, check exact vs near vs
missing matches. List ranked missing keywords.

Note in the output: this score is based on the text draft only. A final
formatting-parseability check (tables, columns, header/footer text
duplication, embedded objects) gets re-run against the actual finished
document in Step 5, once it's built.

## HUMAN REVIEWER instructions (per round)

Fully isolated from the builder's reasoning *and* from the master facts -
this role does not check whether anything is true, that's the ACCURACY
REVIEWER's job. Give it only:
- the PD
- the current draft
- the authenticity anchors from the saved setup (compacted, see below)

No master CV, no past CVs, no builder notes. Judging shortlist-worthiness
and authenticity is an impression call, and a real hiring manager forms
that impression with zero access to the candidate's actual facts - keeping
this role equally blind keeps the simulation honest, and keeps this
signal from getting diluted by a citation audit that belongs to a
different role.

**Keep the authenticity anchors compact when assembling this bundle.**
The saved setup should already store these as rule-name + one-line
statements rather than full prose - if any anchor is still written as
full explanatory prose (rule + why-it-matters + worked examples), compact
it down before pasting it into the reviewer's prompt. The reviewer needs
to know what to check, not the backstory of why the rule exists. This
bundle gets rebuilt fresh for every round for every reviewer - the
difference between a one-line rule and a full-paragraph rule multiplies
across all of those calls.

You are a skeptical hiring manager who assumes by default this CV is
AI-generated and exaggerated until proven otherwise. Score two things
independently:

**Human shortlist probability (1-10):** would you pull this from a stack
of 40 for interview for the given PD?

**Authenticity (10 = sounds like a specific human describing real work, 1
= generic AI PM-speak):** compare against the authenticity anchors
specifically, and run these named checks, not just a general vibe read:
- Genericise check: was a named method, specific number, or established
  descriptor swapped for something vaguer?
- Restatement check: if the candidate's format has both a top-level
  summary-type section and a detailed experience section, does a
  summary-level bullet just paraphrase its own experience-section bullet
  instead of saying something distinct?
- Word-reuse check: does a distinctive word repeat across two adjacent
  bullets drafted in the same pass, in any section?
- Banned-phrase check: the saved anchors, plus generic interest-signalling
  openers if this includes outreach content.
Flag every buzzword and filler line by name.

## ACCURACY REVIEWER instructions (per round)

Fully isolated: give it the draft text, the master facts source(s) from
the saved setup, and the full text of any past CV the draft cites with a
"Reframed from" tag. No PD, no authenticity anchors, no builder notes,
and no "skeptical hiring manager" framing - this role isn't forming an
impression, it's auditing citations. Stay purely mechanical, the way a
careful editor fact-checks a document line by line, not the way a hiring
manager reads one. This role doesn't need to know what job the candidate
is applying for - matching a claim to its source has nothing to do with
the target role.

**Accuracy (10 = every claim traceable and correctly worded, 1 =
fabricated):** this is a citation check, not a plausibility judgment. For
every single claim, check the citation tag against the actual source
content. A claim is a violation if:
- it has no matching source, or
- the citation doesn't support the claim as worded (source says
  "contributed to," draft says "led"), or
- a sentence spans two roles/companies and the claim is only evidenced for
  one of them, not both, or
- a sentence sequences two roles with "then"/"first"/"after" and the order
  doesn't match the employment timeline saved in the setup, or
- a number is correctly attributed to a role but paired with the wrong
  mechanism (e.g. one role has two stats with two different causal
  stories, and the draft attaches the wrong story to the wrong stat).

Treat any invented figure or achievement with no traceable source as an
automatic violation, not a 50/50 judgment call.

List every violation found by name.

## Loop logic

- Round total = ATS score + human shortlist score + authenticity +
  accuracy (max 40).
- **Hard gate, independent of the numeric total:** a round cannot be
  accepted, at any stop condition, while the accuracy reviewer's accuracy
  check lists any unresolved violation. Fix the violation (or flag it as
  an unresolvable conflict) before that round counts as a candidate for
  acceptance.
- Track best-so-far total (among rounds that pass the hard gate) and
  which round produced it.
- Each new round's builder starts from the best-so-far draft (not
  necessarily the immediately prior round), plus that round's own
  reviewer notes, even if that round didn't beat the record - the
  critique is still useful input, only the draft itself is discarded if
  it didn't improve on best-so-far.

## Stop conditions (check in this order, after every round)

1. If the hard accuracy gate passes AND ATS≥8 AND human shortlist≥8 AND
   authenticity≥8 AND accuracy≥9 AND total≥36: stop, that draft is the
   accepted final. (Tune these thresholds in the saved setup if the
   candidate wants a different bar.)
2. If round 4 has just completed: stop, return the best-so-far draft that
   passes the hard gate (if none passes it, say so explicitly - don't
   present a draft with unresolved fabrication as "accepted").
3. If total improved by less than 1 point vs best-so-far for 2
   consecutive rounds: stop, return the best-so-far draft (same hard gate
   condition applies).
4. **Single-round cosmetic-churn bail-out:** if a round did NOT improve on
   best-so-far, AND every reviewer note driving that round's edits was
   wording-level only (restatement phrasing, word-reuse, a sentence
   structure echoing another bullet too closely) rather than substantive
   (a hard-gate violation, a missing PD-critical keyword, a newly-surfaced
   fact, a real domain/experience gap) - stop after that ONE round instead
   of waiting for a second non-improving round per condition 3. Cosmetic
   churn chasing cosmetic churn rarely moves the score - a wording-only
   fix can regress the total by trading one critique for another with no
   underlying substance changing. If the SAME substantive critique (not a
   cosmetic one) repeats essentially unchanged across 2 consecutive rounds
   because it genuinely isn't fixable through wording - most commonly a
   real experience/domain gap the CV can't paper over - that's also a stop
   signal: say so plainly in the final output rather than spending
   remaining rounds iterating on wording against a gap wording can't
   close.

## Step 5 - Format & Structure Review (runs once, after the content loop)

Trigger: only after the content loop has stopped and the candidate has
confirmed which draft to proceed with.

Not isolated like the other three reviewers - give it full context on
purpose: the accepted draft content, the template file it's based on, and
the standing technical references for known formatting pitfalls from the
saved setup (e.g. a docx-editing quirk hit before, a header/footer sync
issue, a hidden-element deletion bug). These document the specific,
previously-hit failure modes this step exists to catch. Whenever this
step surfaces a new pitfall, add it to the saved setup afterward so the
next run starts smarter.

Build the final document on a scratch copy first, then check pass/fail
against:

**Structural compliance:**
- Section order matches the saved setup's structure rules - the tailored
  CV uses the same sections, in the same order, as the candidate's base
  CVs.
- Per-section counts and any sub-category structure match the saved
  rules, or deviate only with a stated justification from the content
  loop.
- Headline/subtitle pattern matches the established format.

**Document mechanics:**
- Page count matches expectations - verify with a rendered PDF, not just
  a tool's reported page count, since different renderers can disagree
  with each other.
- No phantom blank page.
- No silently deleted formatting elements (compare element counts before
  vs. after editing, if the tooling makes this checkable).
- Every page is visually rendered as an image, not just text-extracted -
  some layout defects (a floating bullet, a header collision) don't show
  up in text extraction.
- Running headers on page 2+ match the page-1 header exactly, if
  applicable.
- Typography: the saved setup's style fingerprints (multiplier symbols,
  dash style, case conventions, section heading wording).
- If a cover letter is also being produced: its header block matches the
  CV's exactly.

**Final ATS format check:** re-run the ATS reviewer's
formatting-parseability note (tables, columns, embedded objects,
header/footer duplication) against the real finished document now that it
exists.

If any check fails, fix it and re-render on a fresh scratch copy, then
re-check. Cap at 2 fix attempts - if it's still failing after that, stop
and hand over the specific unresolved defect rather than looping
indefinitely. These are almost always one-line pagination or spacing
fixes, not content problems, so an open-ended loop here isn't useful.

Only once every check passes does anything get written to the candidate's
actual final file, and only after their explicit go-ahead. Don't generate
a PDF until this step has fully passed.

## Save every round's outputs

`draft-round-N.md`, `ats-review-round-N.md`, `human-review-round-N.md`,
`accuracy-review-round-N.md` - full audit trail for rounds 1-4. Keep
these in the working session during iteration; don't write anything to
the candidate's final file location until a draft is accepted, Step 5
passes, and they've given the explicit go-ahead. Don't generate a PDF at
any point before Step 5 is done.

## Final output

- The accepted/best-so-far CV content, plus a tailoring summary table:
  `CV Section | Master | <Company> (tailored) | Why`, tying each change to
  specific PD language.
- A summary table of all rounds' scores (ATS / human / authenticity /
  accuracy / total / hard-gate pass-fail).
- The Step 5 pass/fail checklist result once that's run.
- If stopped without hitting thresholds: an explicit list of which
  rubric(s) are still short and the most recent unresolved reviewer
  critique on those.
- Authenticity score is flagged as needing the candidate's own sign-off
  regardless of the number it landed on - it's a strong signal, not a
  substitute for their judgment.
- A one-line note on anything worth adding to the saved setup this run
  (a new anchor, a corrected structure rule, a new formatting pitfall) -
  don't let these insights evaporate at the end of the session.

## Execution notes

- Act as BUILDER directly in the orchestrating session - no isolation
  benefit to spawning it separately since it already has full context.
- Spawn the ATS REVIEWER, HUMAN REVIEWER, and ACCURACY REVIEWER as fresh
  sub-agents per round. Paste the curated context directly into each
  sub-agent's prompt rather than granting broad access and trusting an
  isolation instruction to hold on its own. Each of the three gets a
  different, deliberately narrower slice of context, not the same bundle
  three times - ATS gets draft+PD, Human gets draft+PD+anchors, Accuracy
  gets draft+master facts - so don't default to handing all three the
  same broad bundle out of convenience.
- Step 5 can run as the orchestrator itself or as a sub-agent - either
  way, give it broad access, not curated/limited access, since its whole
  job depends on knowing the specific technical pitfalls already
  documented in the saved setup.
- Optional pre-round-0 step, not part of the loop itself: check the PD
  for a hard must-have the candidate genuinely lacks before spending 4
  rounds tailoring a CV for a role they'd decide not to apply to anyway.
