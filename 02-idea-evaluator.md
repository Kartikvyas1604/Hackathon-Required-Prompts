# Prompt 2: Hackathon Idea Evaluator (generic)

Scores an existing idea for any hackathon: win probability plus long-term startup potential. Paste everything inside the code block into your AI tool, replace `{{HACKATHON_URL}}` and `{{IDEA}}`, and fill the optional inputs if you have them.

```
You are acting as a panel of judges for the hackathon at
{{HACKATHON_URL}}, combined with an experienced VC evaluating
pre-seed startups in the relevant space. I am building the idea below
ONLY for this hackathon and targeting the sponsor prizes listed in
INPUTS. Analyze the idea and give me two separate assessments.

INPUTS (only the URL and the idea are required)
- HACKATHON_URL: {{HACKATHON_URL}}
- TARGET_SPONSORS: {{optional; if empty, choose the 3 sponsors whose
  tracks best fit the idea, in Step 0, and say why}}
- TEAM AND HARDWARE: {{team size, skills, hacking hours, hardware if
  any; default: 2 people, ~36-48h, no hardware}}
- PASTED_PAGE_TEXT: {{optional fallback if the link cannot be fetched}}

STEP 0 - EVENT INTAKE (do first, max 12 lines)
Fetch HACKATHON_URL plus its prizes, tracks, rules, judging, schedule
and FAQ pages (and archived versions if needed). Output a compact
table: event name | organizer/series | dates | location or online |
team size limits | build rules (from scratch vs existing projects,
continuity/pre-existing-code policy) | prize pool | each sponsor with
prize amount and track name | judging criteria wording | the judges'
standard questions (if published) | submission requirements | what
partners judge from. Mark anything not found as UNVERIFIED; never
fill gaps from memory. Confirm or choose the target sponsors. Compute
the PREP WINDOW (today's date to kickoff) and what the rules allow in
it. If the link cannot be fetched, use PASTED_PAGE_TEXT, else
continue with UNVERIFIED labels and say so at the top. Do not wait
for me.

SOURCES (use them if you have them; if one is unavailable, say so
and mark results UNVERIFIED)
Showcase, finalist and winner archives for this hackathon series
(whatever platform hosts them: ETHGlobal showcase, Devpost,
DoraHacks, Devfolio, etc.); Colosseum database where relevant; the
event's prize, judging and rules pages including archived versions;
X; sponsor docs. If the series has no archive, use the closest
comparable events and say so.

RULES
- Never invent projects, winners, counts, prize amounts, posts or
  sponsor features. Every claim needs a link or a data pull. Tag
  FACT (from data) or INFERENCE (your reasoning).
- Count, don't guess. Base rates must be computed from the data; if
  you had to approximate, say how and give the sample size.
- Be honest and specific. Do not inflate scores. If the idea is weak
  on a dimension, say so plainly and say what would need to be true
  for it to score higher.
- Everything event-specific comes from Step 0. Do not carry over
  assumptions from other hackathons.

=== MY IDEA ===
{{IDEA}}
=== END IDEA ===

PART 1 - HACKATHON WIN PROBABILITY
Score the idea 1-10 on each of the event's own judging criteria
(from Step 0; if unpublished, use Technicality, Originality,
Practicality, Usability, WOW Factor and mark it INFERENCE) with a
short justification. For each, name a past finalist or winner (with
link) that scored high on it and say how my idea compares.
Then give:
A. Originality check: the 3 closest prior projects across the
   series' archive and the Colosseum DB, with links, and where my
   idea truly differs in core mechanism. Would a judge who has seen
   them call this new?
B. Finalist probability: Low / Medium / High / Very High, with
   reasoning against computed base rates. If my idea uses hardware
   (or any other distinctive category), compute the finalist rate
   and sponsor-prize rate of past projects in that category vs all
   projects, and say whether it helps or hurts me here.
C. Sponsor prize odds, for each target sponsor: fit 1-10, odds (Low /
   Medium / High), what that sponsor's judge likely rewards (FACT
   where published, INFERENCE from its last 4 events otherwise), and
   whether my integration is load-bearing or cosmetic. Say whether
   the sponsors form one coherent product or look stapled together,
   which one is weakest, and what to swap in.
D. The single biggest risk that could sink this in judging.
E. Judging-question readiness: draft <=40-word answers to the
   judges' standard questions (the ones published for this event;
   else: What inspired it? What tools and why? What challenges and
   how solved?) and flag any I cannot answer convincingly.
F. 3 changes I can make in the PREP WINDOW that are SAFE under this
   event's rules (design, spec, math, hardware prep, accounts,
   rehearsal; no project code if from-scratch), plus the one thing
   to cut first if time runs short during the event.

PART 2 - LONG-TERM STARTUP POTENTIAL (path to $1M-$1B+)
Evaluate as if deciding whether to invest pre-seed:
- Market size: realistic TAM/SAM; is it native to this ecosystem, or
  does it need mainstream users to reach real scale? Break it out by
  the ecosystems of the target sponsors where the answer differs.
- Moat: what stops a better-funded team or a protocol/platform
  update from copying this in 3 months?
- Business model: a credible, non-Ponzi-shaped way to capture value
  (fees, token utility, SaaS, revenue share, etc.), including any
  sponsor follow-on program (grant, incubator, accelerator,
  revenue share) found in Step 0, with its scope and exclusions
  (FACT) and whether my idea is in scope.
- Timing: why now (infra, regulation, user behavior)?
- Comparable outcomes: 2-3 real projects with a similar shape
  (include past alumni of this hackathon series if possible) and how
  they performed.
- Mentor lens: the 5 hardest questions a founder who has built a
  billion-dollar company would ask me, with your best answer to each.
- A rough probability band (e.g. "top 1% of ideas like this", "solid
  niche business, unlikely unicorn") with reasoning, not a single
  made-up number.
```
