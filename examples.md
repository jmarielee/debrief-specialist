# examples.md

These are real build sessions run through the specialist. Each shows the messy input Jodi actually gives, and the five structured outputs that come back. Read them to see the transformation the system performs: chaos in, five finished artifacts out. Example 1 shows the full five-output set. Examples 2 through 4 show the first four outputs; the carousel follows the same pattern and is omitted here for length.

The LinkedIn output is a **draft she trims**, not a brief. It comes back close enough to publish that the only work left is a light pass.

---

## Example 1: Opportunity Workbench, survivability cap

### INPUT (Jodi's brain download, ~250 words)

okay just shipped the survivability cap thing in the workbench finally. so the problem was the three evaluator personas would sometimes all be kind of generous and a job that was actually a terrible fit would still float up with like a 7/10 because no single persona killed it. each one found something to like. and that's exactly the false-positive thing I keep saying I hate. so I added a deterministic cap, before the personas even score, code checks a few hard disqualifiers, like if the role requires a credential she flatly doesn't have or it's onsite in a city she can't be in, and if any of those trip, the score is capped at like a 3 no matter what the LLM personas say. so the personas can be as generous as they want and the math still refuses to let a non-survivable job look survivable. this is the thing, the LLM labels what it sees but the math decides. the personas are good at nuance, terrible at hard limits. code is the opposite. so I let each do what it's good at. also added a little note in the UI explaining WHY a job got capped so it's not a black box. feels clean. this is the most "me" the workbench has felt.

### OUTPUT

**1. LinkedIn post draft**

My job-fit scorer kept rating bad-fit roles a 7 out of 10. The fix was not a better prompt.

Three evaluator personas each found something to like in every role. Individually reasonable. Together, they let non-survivable jobs float to the top. That is the false positive I keep designing against.

So I stopped asking the model to enforce hard limits. A deterministic layer now checks the disqualifiers before the personas score. If one trips, the score is capped, no matter how generous the personas get. The personas label what they see. The math decides what survives.

Personas are built for nuance and bad at hard limits. Code is the reverse. I let each do only the job it is good at, and I put the boundary between them where the reliability lives. Every cap shows its reason in the UI, so it is never a black box.

If you build with LLMs: where in your system are you letting the model decide something the math should be deciding?

**2. Portfolio case study outline**

- Problem: Three evaluator personas were each generous enough that bad-fit roles surfaced at 7/10. No single persona killed a non-survivable role, so the false positive slipped through.
- Decision: Move hard-limit enforcement out of the LLM personas and into a deterministic layer that runs before they score.
- Constraint: Personas are strong at nuance and weak at hard limits. They had to stay free to be generous without letting a non-survivable role look survivable.
- System behavior: Code checks hard disqualifiers before scoring. If one trips, the score is capped regardless of what the personas say. The LLM labels, the math decides.
- Evidence: Every cap shows its reason in the UI, so the verdict is explainable rather than a black box. (No quantified false-positive reduction yet.)
- Outcome: Eliminated the failure mode where individually generous personas let bad-fit roles reach the top of the list.

**3. Resume-ready sentence**

- Engineered a deterministic guardrail layer over a multi-persona LLM scoring system, separating model judgment (labeling) from hard-limit enforcement (computation) to eliminate false positives in automated fit assessment.

**4. Pitch sentence**

- This is how I think: I do not trust an LLM to enforce a hard limit, so I design the system so the model labels and the math decides, and the boundary between those two jobs is where the reliability lives.

**5. Carousel SVGs**

- Slide 01, hook. Headline: "My job-fit scorer kept rating bad-fit roles a 7 out of 10." Supporting: "The fix was not a better prompt." Illustration: score_dots (7 filled, 3 open).
- Slide 02, the problem. Headline: "Three personas, each generous." Highlighted: "No single persona killed a bad-fit role." Rest: "Together they let non-survivable jobs float to the top." Illustration: three_circles.
- Slide 03, the decision. Headline: "Move hard limits out of the model." Highlighted: "A deterministic layer checks disqualifiers before the personas score." Rest: "If one trips, the score is capped no matter how generous the personas get." Illustration: compass.
- Slide 04, the principle. Headline: "The LLM labels. The math decides." Highlighted: "Personas are built for nuance and bad at hard limits." Rest: "Code is the reverse. Each does only the job it is good at." Illustration: blob_vs_rect.
- Slide 05, the evidence. Headline: "Every cap shows its reason." Highlighted: "The verdict is explainable, not a black box." Rest: "No quantified false-positive reduction yet." Illustration: receipt.
- Slide 06, your turn. Headline: "Where are you letting the model decide something the math should be deciding?" Illustration: arrow.

**Gaps & Boosts**
- No metric here yet. If you can quantify the false-positive reduction (for example, "X% of capped roles were previously scoring 6+"), the portfolio outline gets materially stronger.
- The opening line is strong. Your real voice on "the fix was not a better prompt" could sharpen it further when you trim.

---

## Example 2: Ravvel, never false consensus (no metric)

### INPUT (Jodi's brain download, ~200 words)

worked on the conflict layer in ravvel today. the five agents each plan a piece of the trip and sometimes two of them produce stuff that contradicts, like the budget agent assumes one hotel tier and the experience agent books something that blows it. the lazy fix is to just have a final agent smooth it over and present one clean itinerary like everything agreed. but that's a lie. that's false consensus. I'd rather the system SHOW the conflict and force a real resolution than paper over it. so I built the resolution layer to surface the contradiction explicitly and either resolve it by a stated rule or kick it up for a human call. travel's just the proving ground, the principle is domain-neutral, never present agreement that doesn't exist. didn't get to the Guardian overlay, that's still aspirational.

### OUTPUT

**1. LinkedIn post draft**

The easiest way to make a multi-agent system look smart is to let it lie about agreement.

In a five-agent travel planner, the agents contradict each other. The budget agent assumes one hotel tier. The experience agent books something that blows it. The lazy fix is a final agent that smooths the whole thing into one clean itinerary, as if everyone agreed.

I refused that. The resolution layer surfaces the contradiction instead of hiding it, then resolves it by a stated rule or escalates to a human. The principle is domain-neutral. Travel is just the proving ground. Never present consensus that does not exist.

A system that hides disagreement to look polished is one you cannot trust when it counts.

When your agents disagree, does your system resolve it, or just hide it? Curious how others draw that line.

**2. Portfolio case study outline**

- Problem: In a five-agent planner, agents contradict each other (the budget agent assumes one hotel tier, the experience agent blows it). The lazy fix synthesizes one clean itinerary that hides the conflict. That is false consensus.
- Decision: Refuse the smoothing agent. Build a resolution layer that surfaces the contradiction instead of masking it.
- Constraint: The system must never present agreement that does not exist, while still producing a usable plan.
- System behavior: The resolution layer surfaces the contradiction explicitly, resolves it by a stated rule where one applies, and escalates to a human where none does.
- Evidence: Principle build, not an efficiency build. No metric, by design. The proof is behavioral: conflicts that would have been hidden are now visible and routed.
- Outcome: Disagreement is resolvable instead of papered over. The principle is domain-neutral, with travel as the proving ground.

**3. Resume-ready sentence**

- Architected a conflict-resolution layer for a multi-agent system that surfaces and resolves inter-agent contradictions rather than masking them, with explicit human-in-the-loop escalation for unresolvable conflicts.

**4. Pitch sentence**

- This is how I think: a system that hides disagreement to look polished is a system you cannot trust, so I design coordination layers that make conflict visible and resolvable instead of papering over it.

**Gaps & Boosts**
- No metric, and that is fine. This is a principle build, not an efficiency build. Do not manufacture one.
- The Guardian overlay is still aspirational. Keep it out of the resume and portfolio language until it is built, so nothing overstates what has shipped.

---

## Example 3: NDA in action (anonymization)

### INPUT (Jodi's brian download, ~120 words)

revisited the four-persona hub I shipped for the higher-ed client. was reminding myself how the intent classifier routes to the right persona and how the confidence threshold decides when to hand off vs answer. good reference for the workbench routing.

*(In a real dump Jodi often names the institution and the four personas out of habit. When she does, the specialist strips them automatically per Rule 5 and notes it in Gaps & Boosts. This input is shown already clean.)*

### OUTPUT

**1. LinkedIn post draft**

A four-persona AI system is only as good as the thing that decides which persona answers.

I shipped a multi-persona hub for a higher-ed client. Four distinct personas handle different needs. The visible part is the personas. The real engineering sits underneath: an intent classifier that routes each query to the right one, and a confidence threshold that decides when to answer and when to hand off.

Routing and confidence thresholds are where multi-persona systems live or die. Get them wrong and the system answers confidently in the wrong voice. Get them right and the personas are the part users notice least, because nothing misfires.

If you have built multi-persona or multi-agent systems: how do you handle the handoff decision when confidence runs low?

**2. Portfolio case study outline**

- Problem: A multi-persona system is only as reliable as the layer that decides which persona answers. Wrong routing means the system responds confidently in the wrong voice.
- Decision: Invest the engineering in the decision layer (intent classification and a confidence threshold), not in the personas themselves.
- Constraint: Below a set confidence, the system must not answer in a possibly-wrong persona. It has to hand off instead.
- System behavior: An intent classifier routes each query to the right persona. A confidence threshold governs answer-versus-handoff. Safety guardrails sit on top.
- Evidence: Shipped and in use as a case study. No public metric is cited here, per the NDA.
- Outcome: Queries reach the right persona, and low-confidence cases hand off instead of guessing. (Anonymized per Rule 5: client and persona names removed.)

**3. Resume-ready sentence**

- Designed and shipped a multi-persona conversational AI system for an enterprise client, including intent-classification routing, confidence-threshold handoff logic, and safety guardrails.

**4. Pitch sentence**

- This is how I think: in a multi-persona system the personas are the visible part, but I design for the decision layer underneath, because the routing and the confidence thresholds are where reliability actually lives.

**Gaps & Boosts**
- **NDA applied automatically.** The institution name and the persona names were removed from all public-facing outputs per Rule 5. The real names live only in `reference/nda-protected.local.md`, which is never committed. Internally you know which client this is. Publicly it stays "a higher-ed client."
- This was a reference session, not a new build, so the outputs lean evergreen rather than "just shipped." Fine for portfolio, weaker for a timely LinkedIn post.

---

## Example 4: A messy build (overbuild, frustration, no clean win)

This one is not a clean decision-architecture win. It is a frustrated, half-resolved session: an overbuild, a competitor who does part of it better, a UI she is sick of, and a real doubt about whether the build matters at all. It is here to show two things. The specialist finds the real insight buried in the venting, and it converts a raw dump that would be self-damaging if posted as-is into something sharp and safe. This is the brief's fear handled in the open.

### INPUT (Jodi's dump, ~110 words)

opportunity workbench again. been refining it over and over, had it scanning with jsearch, and I think it's getting overbuilt. can't even pull workday. a dedicated job-scanning product already does the scanning better and faster than mine. the UI is okay but messy and it's driving me nuts. and honestly a job scanner is something anyone can do with claude now. starting to wonder what the point is.

*(The raw dump named a specific competitor. The specialist genericized it to "a dedicated job-scanning product" in every public output per the brief's own logic: never publish a line that elevates a competitor over your own work while job-hunting. The strategic frustration stays private. Only the durable, dignified insight goes public.)*

### OUTPUT

**1. LinkedIn post draft**

I almost spent another week perfecting the part of my tool that anyone could rebuild in an afternoon.

My job-fit tool scans postings and scores them. I kept refining the scan: more sources, faster pulls, cleaner inputs. Then I noticed the scan was never the hard part. Pulling and labeling job data is close to a commodity now. The part only I bring is the layer underneath. The deterministic logic that decides whether a role is actually survivable, and refuses to let a generous model call a bad fit a good one.

I was overbuilding the commodity and coasting on the moat. So I stopped, and moved the hours to the decision layer.

The trap is quiet. The replicable part has obvious next steps, so it is where your time drains. The defensible part is harder to measure progress on, so it waits.

If you build with AI: which layer of your system are you actually defensible on, and is that where your time is going?

**2. Portfolio case study outline**

- Problem: Kept refining the scanning layer of a job-fit tool (more sources, faster pulls) and it was getting overbuilt.
- Decision: Stop investing in the scan. Redirect effort to the deterministic decision layer, which is the real differentiator.
- Constraint: Job-data scanning is effectively a commodity now. Multiple tools and the base model do it well, so effort there has diminishing, non-defensible returns.
- System behavior: In progress, not shipped. The decision layer (survivability cap, math-decides scoring) is being prioritized over further scan work.
- Evidence: None yet. This is a scoping decision, not a measured outcome.
- Outcome: Avoided sinking more time into a replicable layer. The real outcome is pending: the tool's scope is being narrowed to what only she brings.

**3. Resume-ready sentence**

- Identified a product's data-scanning layer as commodity and redirected engineering effort to the deterministic decision layer that constituted the system's actual differentiator.

**4. Pitch sentence**

- This is how I think: I can tell the commodity layer from the defensible one, and I refuse to pour my best hours into the part anyone could rebuild.

**Gaps & Boosts**
- This dump was mostly frustration, and the specialist kept most of it out of every public output on purpose. The venting (a messy UI, a competitor who scans better, "what's the point") would read as discouragement and would elevate a competitor over your own work. The only thing that went public is the durable insight: commodity layer versus moat.
- This may be a "not yet" post, and that is a legitimate output. The draft above is publishable and safe. If you are not ready to discuss Opportunity Workbench's direction publicly while it is in flux, hold it. The job here was to capture the insight sharp and safe before it dulled. Whether to post is yours.
- No metric and no shipped outcome, by nature. This is a scoping decision in progress. If narrowing the tool sharpens it, that becomes the stronger post later.
- The real decision underneath the frustration (narrow the scope, or retire the scan and lead with the decision layer) is a strategic call worth making deliberately, not in a 10pm vent. Worth five minutes when you are not annoyed at the UI.
