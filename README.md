# CV Tailor Loop

A Claude skill that runs a heavyweight, multi-round CV tailoring and
review process for high-stakes job applications: four isolated AI
reviewer roles (ATS match, human/authenticity, fact-accuracy, and
format/structure), a hard zero-fabrication gate, and clear stop
conditions, so a tailored CV gets the same adversarial scrutiny a real
hiring process would apply before you send it.

It is deliberately slower and more expensive to run than a normal "tailor
my CV for this job" request. Use it for the handful of applications that
matter most, not every application.

## What it does

Most single-pass CV tailoring is one AI writing a draft and calling it
done. This skill instead runs four separate, isolated review passes on
every round:

- **BUILDER** - tailors the current best draft to the job description.
- **ATS REVIEWER** - a cold keyword/format match score, sees only the
  draft and the job ad. No context about you, on purpose - a real ATS
  doesn't have any either.
- **HUMAN REVIEWER** - a skeptical hiring-manager read on shortlist
  odds and authenticity (does this sound like a real person, or generic
  AI PM-speak). Sees the draft and the job ad, but never your actual
  facts, so it can't rubber-stamp a claim just because it's true.
- **ACCURACY REVIEWER** - a citation audit against your real facts. Every
  claim in the draft has to trace back to something you actually did.
  Never sees the job ad, so it can't be swayed by "this would look good
  for this role."

A round is only accepted once it clears a hard accuracy gate (no
unresolved fabricated or misattributed claims) and hits score thresholds
across all four dimensions. A one-time Step 5 pass then checks the
finished document for real formatting/pagination issues before anything
gets written to a final file.

## What you need to run it

This skill needs an environment that can spawn isolated sub-agents (so
the four roles genuinely can't see each other's reasoning) and read/write
files. That means:

- **Claude Cowork** - works fully.
- **Claude Code** - works fully; the setup file (see below) is just saved
  as a plain file in your working directory or repo instead of using a
  memory system.
- **Plain claude.ai chat (no Cowork, no sub-agent tool)** - the skill can
  still guide the process, but true role isolation isn't possible in a
  single continuous conversation. Treat it as an approximation, not the
  full design.

## Installation

**Claude Code:** copy the `cv-tailor-loop/` folder into your skills
directory (typically `.claude/skills/`), so the final path is
`.claude/skills/cv-tailor-loop/SKILL.md`.

**Claude Cowork / claude.ai (personal skills):** upload `SKILL.md` as a
custom/personal skill following whichever skill-upload flow your Claude
client offers.

Either way, once installed, the skill's own description tells Claude when
to use it - it only activates when you explicitly ask for the full review
loop (e.g. "run the CV review loop," "give this the full review," "the
4-round loop"), not for routine tailoring requests.

## Using it

### First run (setup)

The first time you use this, the skill will ask you for:

1. **1-5 real CVs you've actually used** - your most complete/current one
   is enough to start; if you have a few different versions (different
   seniority framings, different roles), share those too. One is the
   minimum, more just makes it more reliable. You don't need a separate
   "master resume" document - the skill builds a facts pool directly from
   whatever CVs you give it, and if any of them disagree on a number or
   claim, it'll ask you which one's actually right rather than guessing.
2. **(Optional) Any words or phrases you want flagged as inauthentic or
   AI-sounding.** Fine to skip this and let it grow over time as you
   catch things during review.

From those CVs, it infers your actual section structure (whatever
sections you use, in whatever order, with whatever per-section format -
nothing assumed or templated in), how your title/framing shifts by role
level, and your writing style - and shows you what it inferred so you can
correct it before it's used.

### Every run after that

Just share the job description. The skill reads back its saved setup
(facts pool, structure rules, authenticity anchors) and only asks again
if something's missing, stale, or genuinely in conflict with a new CV you
share. It should get faster and need less input the more you use it.

### Where the setup gets saved

Depends on where you're running it:

- **Cowork with a connected folder:** a plain file next to your CV
  materials.
- **Cowork with persistent memory:** in memory, if that's available in
  your account.
- **Claude Code:** a file in your working directory or repo (e.g.
  `cv-tailor-loop-setup.md`).

Whatever the mechanism, it needs to survive between separate runs, not
just within one session - if your setup isn't persisting, check that
Claude actually has write access to wherever it's trying to save it.

## What you get out

- A tailored CV, with a summary table showing what changed from your
  base CV(s) and why, tied to specific language in the job description.
- A score breakdown across all four rounds (ATS / human shortlist /
  authenticity / accuracy), plus a pass/fail on the accuracy gate.
- If the loop stops without hitting its bar: an honest list of what's
  still short and why, rather than a draft dressed up as finished.
- A running note of anything worth adding to your saved setup (a new
  banned phrase, a corrected structure rule, a formatting gotcha) so the
  next run starts smarter.

## Customizing it

`SKILL.md` is plain text - open it and adjust:

- The **score thresholds** in the "Stop conditions" section if you want a
  stricter or looser bar.
- The **Step 5 checklist** if your CV format has its own recurring
  technical issues (page breaks, template quirks) worth checking for
  every time.
- The **relationship to a faster/single-pass flow**, if you have one you
  want this skill to defer to for routine applications.

## Background

This started as a personal workflow for tailoring product-management CVs
for senior/lead/principal-level roles, then got generalized so anyone can
adapt it to their own facts, structure, and style rather than someone
else's.

## License

MIT - see [LICENSE](LICENSE).
