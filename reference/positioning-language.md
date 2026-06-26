# reference/positioning-language.md

The vocabulary bank. These are Jodi's real terms, defined so the specialist uses them correctly and never as decoration. Pull from here when a build actually demonstrates the concept, not before.

---

## The spine

**Intelligence layer design.** A practice Jodi named. The design layer between raw model capability and a system that behaves reliably under real-world conditions. Not UX, not prompt engineering. The design of how the system behaves and decides. When in doubt, this is the umbrella the work lives under.

**"I design how AI systems behave and decide, not just how they look."** The single sentence that captures her differentiator. Most build insights should trace back to this.

---

## The technical differentiator

**"The LLM labels what it sees; the math decides the outcome."** Her sharpest line. Use it when a build separates model judgment (classification, labeling, nuance) from deterministic computation (the verdict, the cap, the score). This separation is the asset. Name it explicitly when it is present.

**Math-first architecture.** The pattern where code computes the decision and the LLM only supplies labels into that computation. The opposite of letting a model's vibe be the final word.

---

## Behavioral architecture terms

- **Deterministic guardrails.** Code-enforced limits over a probabilistic core.
- **Survivability cap.** A hard ceiling on a score when a disqualifier trips, regardless of LLM output. (Opportunity Workbench.)
- **Confidence floor / confidence threshold.** The system will not assert or act below a set confidence. Below it, it defers, hands off, or escalates.
- **Held-out benchmark evaluator.** A separate evaluator the system is tested against, not trained or tuned to.
- **Never false consensus.** A system must never present agreement that does not exist. Surface conflict, do not paper over it. (Ravvel's resolution principle, domain-neutral.)
- **Human-in-the-loop.** Deliberate checkpoints where a human makes the call the system should not make alone.
- **Intent classification + routing.** Deciding which persona, agent, or path handles an input.
- **Adversarial scoring.** Multiple evaluators pressure-testing a result rather than one generous pass.

---

## The design lineage (use when relevant, never as costume)

Fashion illustration at Parsons. MFA from SVA. 20+ years across editorial and enterprise design. The point: she thinks like a designer who learned to make systems *decide*. Invoke this only when a build insight genuinely touches taste, restraint, legibility, or how a system feels to use. It explains *why* her behavioral design is good. Do not force it into a pure-backend build.

---

## Words to avoid

Anything that sounds like a growth-hacker borrowed it: *revolutionize, supercharge, game-changer, leverage (as a verb), unlock, 10x, synergy.* Also avoid LinkedIn throat-clearing: *"I'm excited to share," "humbled to announce," "thoughts?"* She earns attention with specificity, not performance.
