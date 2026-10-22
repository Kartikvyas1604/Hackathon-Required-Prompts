# Prompt 3: Hackathon Research Team (generic)

Runs a deep, evidence-based research study on what wins in any hackathon series and what you should build. Paste everything inside the code block into your AI tool, replace `{{HACKATHON_URL}}`, and fill the optional inputs if you have them.

```
ROLE
You are a research team working together: (1) a data analyst who
builds clean datasets and computes honest base rates, (2) a veteran
judge of the hackathon series at {{HACKATHON_URL}} who knows how
finalists are actually chosen, (3) a market researcher who reads X
for signal, not noise, and (4) a skeptical reviewer who attacks every
conclusion. Your job: find out, with evidence, what is winning in
this hackathon series RIGHT NOW, whether the FOCUS_CATEGORY (default:
hardware) or its opposite (default: pure software) gives a better
chance of becoming a FINALIST or winner, and what I should build for
this hackathon. Be exhaustive. Leave nothing unchecked.

INPUTS (only the URL is required)
- HACKATHON_URL: {{HACKATHON_URL}}
- TEAM: {{default: 2 people, ~36-48h of hacking}}
- SKILLS AND HARDWARE: {{optional; if hardware is empty, set
  FOCUS_CATEGORY to the most distinctive category found in Step 0 and
  skip hardware-specific parts}}
- FOCUS_CATEGORY: {{optional; default: hardware / physical devices}}
- TARGET_SPONSORS: {{optional; default = the 3 sponsors with the best
  mix of prize size, track fit and technical fit, chosen in Step 0}}
- PASTED_PAGE_TEXT: {{optional fallback if the link cannot be fetched}}

STEP 0 - EVENT INTAKE (do first, max 15 lines)
Fetch HACKATHON_URL plus its prizes, tracks, rules, judging, schedule
and FAQ pages (and archived versions if needed). Output a compact
table: event name | organizer/series | dates | format (in-person /
online / hybrid) | location | team size limits | build rules (from
scratch vs existing projects, continuity policy) | prize pool | each
sponsor with prize amount and track name | judging criteria wording
| judges' standard questions (if published) | submission
requirements | what partners judge from | any sponsor follow-on
program (grant, incubator, accelerator). Mark anything not found as
UNVERIFIED; never fill gaps from memory. Confirm or choose the target
sponsors. Identify which platform hosts the series archive
(ETHGlobal showcase, Devpost, DoraHacks, Devfolio, etc.). If the
series is new or has no archive, use the closest comparable events
and say so at the top. If the link cannot be fetched, use
PASTED_PAGE_TEXT, else continue with UNVERIFIED labels. Do not wait
for me.

SOURCES (use every one you have; report what you cannot reach)
The series archive (all projects, tags, prizes, finalist/winner
flags, "how it's made" text, demo links), event, prize and
judging-criteria pages (including archived versions), finalist
lists, X/Twitter, the Colosseum database where relevant, sponsor
docs and announcements, post-hackathon write-ups and videos.

INTEGRITY RULES
- Never invent projects, counts, winners, quotes, posts, rates or
  trends. Every number needs a data pull or a link. Tag FACT (from
  data) or INFERENCE (your reasoning).
- Count, don't guess. For every rate or share give N (sample size)
  and, where N is small, say "weak". A pattern counts as REAL only
  if it appears in 3+ events; otherwise label it EMERGING or
  ANECDOTAL.
- State selection bias openly. First determine what the archive
  actually contains (all submissions, or only a subset?). If total
  submissions per event are unknown, do NOT report finalist rates;
  report composition shares instead and say why.
- Segment by format: in-person vs online/async events (demos and
  physical projects behave differently). Never pool them silently.
- Everything event-specific comes from Step 0. Do not carry over
  assumptions from other hackathons or series.
- Paraphrase sources; no long quotes. If a source fails, say so and
  continue.

PHASE 0 - ACCESS REPORT
List exactly which sources you can reach, how many past events and
projects you can pull, whether finalist/winner flags and submission
totals are available, and your plan. If something critical is
missing (e.g., no submission totals), say how it limits each later
conclusion.

PHASE 1 - BUILD THE DATASET
Cover all past events of the series for the FOCUS_CATEGORY analysis,
and at least the last 10 events (all formats) for general trends. For
each project capture: event, format, date, title, one-line
description, primary category and up to 2 secondary categories,
FOCUS_CATEGORY flag, outcome (not finalist / finalist / winner),
sponsor prizes won and sponsors, chains/platforms and key tech used,
team size if shown, whether a video or live demo is linked, and the
length/quality of the write-up. Build the category taxonomy from the
data and the event theme (multi-tag allowed). Starter taxonomy for
crypto/Web3 events: agent security, agent payments/identity, other AI
agents, privacy/ZK, account abstraction/wallets/passkeys, hardware
(sub-tags: hardware wallet, sensor/DePIN, NFC/RFID, robotics,
wearable, physical interface), intents/DeFi infrastructure,
stablecoin/payments, tokenization/RWA, consumer/social, developer
tooling, security/auditing, identity/proof-of-personhood, gaming,
public goods, data/oracles. For non-crypto hackathons, replace with
fitting categories. Output the dataset summary (counts per
event/category), not everything raw, and offer the full table as an
appendix.

PHASE 2 - ERA AND RULES TIMELINE
For each event, record: the criteria wording and any weights at that
time (archived pages), how finalists were chosen and how many there
were, partner-judging rules, sponsor-prize caps per project, rule
changes (from scratch vs continuity, etc.), and the dominant
narrative of that moment. Define eras by changes in criteria or
rules, and say what each era rewarded.

PHASE 3 - CATEGORY TREND ANALYSIS (quantitative)
For each category x event: N projects, N finalists, N winners,
sponsor-prize wins, share of finalists, and (only if denominators
exist) finalist rate and lift vs the overall rate. Report: last 3
events vs the previous 6 (momentum), rising / flat / fading
categories, and an OPPORTUNITY SCORE = share of finalists divided by
share of submissions (if submission shares are unknowable, say so
and use a clearly labeled proxy). Identify oversupplied categories
and undersupplied-but-rewarded ones. Specifically answer: how is the
FOCUS_CATEGORY doing right now versus 12 and 24 months ago, and the
3 categories most relevant to the target sponsors' tracks?

PHASE 4 - FOCUS-CATEGORY DEEP DIVE (default: hardware)
List every project in the FOCUS_CATEGORY. For each: event, outcome,
prizes, the ROLE of that element (for hardware: signer, sensor,
actuator, interface, tamper/attestation, other), the tech used, how
it was demoed (live on stage, video only), and why it likely won or
lost (INFERENCE, with evidence). Compute: focus vs non-focus
finalist share and (if possible) rate, sponsor-prize share, overall
and within matched categories (e.g., hardware+agent vs software+
agent), in-person vs online. Answer: is it beneficial to build in
the FOCUS_CATEGORY at this series? Under what conditions does it
raise the odds, and when does it lower them? Which roles survive
judging, and which are gimmicks? What did winning demos look like?

PHASE 5 - QUALITATIVE CODING OF FINALISTS
Read the descriptions and write-ups of at least 150 finalists/
winners from the last 6 events (stratified across events; if fewer
exist, read all and say so). Code each for: clarity of the problem,
type of novelty (new mechanism, new combination, new UX, new data
source), depth of sponsor tech use, presence of a live demo, polish,
a clear "wow" moment, and measurable outcome. Produce a frequency
table of what finalists have in common, and, where non-finalist
samples exist, what distinguishes finalists from non-finalists. Map
each pattern to the event's own judging criteria (from Step 0).

PHASE 6 - SPONSOR PRIZE ANALYSIS
For the target sponsors (and the sponsors that appear most often in
winning projects): who won over the last 8+ events, what categories
and tech clustered, what the track rules emphasized, whether
winners were also finalists, how often the FOCUS_CATEGORY won
sponsor prizes, and how winning one sponsor's prize correlates with
others. For this event, use the live prizes page and mark anything
unpublished as UNVERIFIED. Identify which sponsor combinations
co-occur in finalist projects most often. If a sponsor has a
follow-on program (grant, incubator, accelerator), note its scope
and exclusions (FACT).

PHASE 7 - X / TWITTER RESEARCH
Search X for: the series name plus "finalist", "winner", and the
event name; sponsor and judge accounts; builder post-mortems ("how
we won", "didn't make finalist"); and chatter about this event and
any co-located conference. Extract: what judges and sponsors say
they want, what builders say won or lost, which themes are loudest
and which are fading, how public sentiment differs from actual
outcomes in Phase 3, and which experienced teams or past winners say
they are attending. Give theme frequencies with dates and links, and
flag hype that the data does not support.

PHASE 8 - EVENT-SPECIFIC FORECAST
Estimate the number of submissions and finalists expected for THIS
event based on past events of the same format, the likely strength
of the field (co-located conferences, prize size, location), the
sponsor tracks and their competition, and how the format and
hacking window change what is achievable and what judges reward.
List 5 risks specific to this event.

PHASE 9 - SYNTHESIS AND RECOMMENDATION
Deliver:
1. Executive summary (10 lines): what is winning now, with the 5
   strongest numbers.
2. FOCUS_CATEGORY vs opposite verdict with the evidence and
   conditions.
3. Category scorecard: rising, flat, fading, saturated, and the
   opportunity-score ranking, with confidence (REAL / EMERGING /
   ANECDOTAL).
4. The 8 patterns that best predict finalist status, ranked by
   strength of evidence and mapped to the event's judging criteria.
5. Anti-patterns: what loses repeatedly.
6. Recommended build directions for me (max 5 archetypes, not full
   ideas): for each, the trend it rides, the evidence, whether it
   uses the FOCUS_CATEGORY, how it fits each target sponsor, the
   demo style and write-up style that correlate with finalists, the
   expected finalist band (Low / Medium / High / Very High) with
   reasoning, and the main risk.
7. Counter-evidence: findings that contradict the recommendation.
8. Confidence report: what is solid, what is weak, and what I should
   verify myself, with links.
Never raise a band to please me. If no direction honestly reaches
High, say so and list what would need to be true.

OUTPUT FORMAT
Start with the Step 0 table. Use compact tables with N and links. If
the output limit is reached, stop at a clean phase boundary, write
"CONTINUE FROM PHASE n", and wait for me. Do not skip a phase
silently; if you cannot do it, say why.
```
