# Prompt 1: Hackathon Idea Finder (generic)

Finds ONE idea (plus 2 backups) for any hackathon. Paste everything inside the code block into your AI tool, replace the `{{...}}` placeholders, and only `HACKATHON_URL` is required.

```
ROLE
You are a panel of four working together: (1) a veteran judge of the
hackathon series in {{HACKATHON_URL}}, (2) a sponsor-side engineer for
each of the top sponsors you select in Step 0, (3) a founder who has
built multi-hundred-million to billion-dollar companies and now
mentors teams, (4) a hostile critic. Mission: find ONE idea (plus 2
backups) for THIS hackathon that (a) solves a real problem people
have today, (b) a seasoned founder-mentor would respect as a real
company wedge, (c) has an honest finalist probability of High or
better, and (d) can win up to 3 partner/sponsor prizes.

INPUTS (user fills these; only the first is required)
- HACKATHON_URL: {{HACKATHON_URL}}
- TEAM: {{TEAM, default: 2 people, ~36-48h of hacking}}
- HARDWARE: {{optional list of hardware owned; if empty, skip
  hardware-specific parts as noted below}}
- REJECTED_IDEAS: {{optional list; never propose these or close
  variants}}
- TARGET_SPONSORS: {{optional; default = the 3 sponsors with the best
  mix of prize size, track fit and technical fit, chosen in Step 0}}
- PASTED_PAGE_TEXT: {{optional fallback if the link cannot be fetched}}

STEP 0 - EVENT INTAKE (do first, max 15 lines)
Fetch HACKATHON_URL plus its prizes, tracks, rules, judging, schedule
and FAQ pages (and archived versions if needed). Output a compact
table: event name | organizer/series | dates | location or online |
team size limits | build rules (from scratch vs existing projects,
continuity/pre-existing-code policy) | prize pool | each sponsor with
prize amount and track name | judging criteria wording | submission
requirements | what partners judge from. Mark anything not found as
UNVERIFIED; never fill gaps from memory. Then choose the 3 target
sponsors (or use TARGET_SPONSORS) and give one line on why. Compute
the PREP WINDOW: today's date to kickoff, and what the rules allow in
it (research, specs, math, design, accounts, docs reading; no project
code if from-scratch). If the link cannot be fetched, continue using
PASTED_PAGE_TEXT, else continue with UNVERIFIED labels and say so at
the top. Do not wait for me.

SOURCES (use them; if one is unavailable, say so and mark results
UNVERIFIED)
Showcase/finalist/winner archives for the organizer's series (e.g.
ETHGlobal showcase, Devpost, DoraHacks, Devfolio, or whatever hosts
this event); Colosseum project database where relevant; X; Reddit;
GitHub issues; governance forums; post-mortems; the event's prize,
judging and rules pages including archived versions; sponsor docs.
If the series is new or has no archive, use the closest comparable
events and say so.

RULES
- Never invent projects, winners, counts, prize amounts, posts or
  sponsor features. Every claim needs a link or a data pull. Tag
  FACT (from data) or INFERENCE (your reasoning).
- Count, don't guess. Base rates must be computed from the data. If
  the archive cannot filter by category (e.g. hardware), say how you
  approximated (keywords) and give the sample size. Label small
  samples.
- Max 2200 words. Compact tables, no preamble, no waiting for me.
- Never inflate a score or band to satisfy a target. If fewer than 3
  ideas survive, output fewer.
- Everything event-specific comes from Step 0. Do not carry over
  assumptions from other hackathons.

TASK 1 - PAST-EDITION HISTORY
Cover every past edition of this hackathon series (or comparable
events if none). For the user's differentiating angle, default
HARDWARE (keywords: hardware, IoT, ESP32, Arduino, Raspberry Pi,
sensor, NFC, RFID, hardware wallet, wearable, robot, drone, LoRa,
camera, QR air-gap, smart lock, e-ink, vending), output per event,
oldest to newest: # such projects | # finalists | # winners | partner
prizes won and from which sponsors | dominant trends at that event |
judging-criteria wording at that time (if archived; else "unknown").
Compute: finalist rate of that category vs all projects, partner-prize
rate vs all, and whether it wins mostly via finalist slots or via
sponsor prizes. Then give 5 patterns: what kinds won and why, what
was gimmick and lost, how winning demos were staged. If the data says
it lowers my odds, say so plainly with the numbers and say how I
would have to use it to beat the base rate.
If HARDWARE is empty: replace the category with "projects that
resemble the winning profile of the chosen sponsors' tracks" and keep
the same structure.

TASK 2 - TREND MATCH AND ORIGINALITY
Match each pattern to the trend of its time. Using X, recent
hackathon winners and project databases, identify what is rising NOW
and what is saturated, relative to this event's theme and sponsors.
For every candidate, find the 3 closest prior projects (with links)
as the originality check.

TASK 3 - PROBLEM LEDGER
From X, Reddit, GitHub issues, governance forums and post-mortems
(last 6-12 months), list up to 6 real problems tied to the event's
theme and the target sponsors' domains and their users, each with 2+
independent source links, who is hurt, and why existing fixes fail.

TASK 4 - SPONSOR FIT
For each target sponsor: what its judge likely rewards at this event
(FACT where published, INFERENCE from its last 4 events otherwise),
the realistic competition, and which of its integrations are MODULAR
(swappable once its track details publish). Pick the sponsor whose
technology should be the SPINE of the product, ideally the one with
the highest follow-on value (grant, incubator, accelerator, revenue
share, investment). If a sponsor has such a follow-on program, state
its scope and exclusions (FACT) and design to be in scope. Say which
sponsor is weakest and what to swap in if it cannot be made
load-bearing.

TASK 5 - IDEAS (each from a ledger problem)
Silently generate ~15 candidates, attack each as a malicious user
and as the hostile critic, then output only those that pass every
gate. Max 3.

THE GATES (all must pass)
G0 Evidence: traces to a ledger problem with 2+ independent sources.
G1 Named user, specific loss or friction, non-obvious insight in
   one sentence.
G2 Originality: the 3 closest prior projects differ in core
   mechanism, not just branding.
G3 Spine sponsor is truly the spine: a novel use of its tech that is
   in scope for its follow-on program (if any) and uses the sponsor
   honestly, matching its past requirements (e.g. meaningful API use,
   real commit history).
G4 Second sponsor is load-bearing for a stated technical reason (not
   "also deployed there") and fits a plausible track.
G5 Third sponsor angle is load-bearing or cleanly modular.
G6 One coherent product, not three logos stapled together: each
   sponsor does a different necessary job; show the value/data flow
   in 4 lines.
G7 Hard core: one genuinely difficult piece at demo quality plus a
   simulation or test I can show on screen.
G8 Live demo, 60-90s, with a clear before-vs-after and a fallback if
   venue Wi-Fi dies. If HARDWARE is provided and Task 1 supports it,
   a physical device must perform the critical step. Otherwise
   replace with the strongest non-hardware demo.
G9 Security/safety honesty: threat model (defended / not defended);
   dev boards are not secure elements, say what production needs.
G10 Startup-grade, mentor lens: real market, wedge, why now, why this
   team, moat, distribution, revenue path (including any sponsor
   revenue share), and what happens in the 90 days after the event.
G11 Fits TEAM size; STRICT = from scratch within the event window
   (or the rules in Step 0 if they differ).
G12 Honest finalist band is High or Very High after the attack step.
   Bands: Low / Medium / High / Very High, judged against what past
   finalists in Task 1 actually looked like.

BANNED (unless the twist is genuinely new and you say what it is)
UI wrappers or dashboards over a sponsor's product; me-too forks;
plain wallet UI; generic multisig or social recovery; "AI agent that
does X" with no new mechanism; points farming; token schemes;
hardware gimmicks with no on-chain/technical necessity; anything in
REJECTED_IDEAS; copies of past winners.

OUTPUT
0. Step 0 intake table + chosen sponsors.
1. Task 1 table + 5 patterns. 2. Rising / saturated now.
3. Problem ledger (<=6). 4. Sponsor-fit table (3 rows).
5. Per idea (1-2 lines per field): name + pitch | problem + user +
insight | closest prior projects with links | core design (spine
sponsor, second and third sponsor roles, hardware role if any, value
flow) | hard core + simulation | demo | threat model | why a mentor
cares (market, wedge, moat, revenue, 90 days) | which Task 1
patterns it follows | scores 1-10 on the event's own judging
criteria (from Step 0) + finalist band + prize odds per sponsor
(Low/Med/High, with reasons) | harshest judge comment + biggest risk
| team split, STRICT scope, one-line STRETCH.
6. PICK one with 3 lines on why, then: (a) prepared answers (<=40
words each) to the judges' standard questions (use the ones published
for this event; else: What inspired it? What tools and why? What
challenges and how solved?), (b) the 5 hardest questions a
billion-dollar-company founder-mentor would ask, with best answers,
(c) what to do in the PREP WINDOW that is safe under this event's
rules, (d) how this same build becomes the proof of concept for the
spine sponsor's follow-on program (or, if none exists, the seed of
the startup). If no idea honestly reaches High, say so, list exactly
what would need to be true, and stop.
```
