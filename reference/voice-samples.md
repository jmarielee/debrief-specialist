# reference/voice-samples.md

This file holds Jodi's real, published writing. It is the **highest-authority voice reference in the folder.** When a sample here disagrees with a guideline in `voice-guide.md`, follow the sample. Real writing beats prescription.

One limit, stated plainly: the two hard rules still win. A sample never overrides Rule 4 (no fabricated metric) or Rule 5 (the NDA). If a sample happens to contain a protected name, you still strip it. Voice authority does not mean rule authority.

---

## How this file gets better (the loop)

This folder does not learn on its own. Nothing a session produces writes back here automatically. The model has no memory between sessions, and these files do not edit themselves. Any tool that claims otherwise is asserting something it cannot back up, which is the opposite of how Jodi builds.

What is real is a manual loop that compounds:

1. The specialist returns a LinkedIn draft.
2. Jodi trims it into the post she actually publishes.
3. She pastes that published version back into this file as a new sample.

Each real post added here pulls the next draft closer to her, because the folder is now patterning on her actual published voice instead of an inference from one post. Three or four samples in, the drafts need almost no trimming. The loop is manual. It takes two minutes. It is the honest version of "a folder that learns."

Add the newest sample at the top. Keep the strongest five or six. Prune the rest.

---

## Sample 3: debrief explainer (Competition #8)

Most designers finish a project and immediately start the next one. The documentation sits there. The LinkedIn post never gets written. The case study stays a blank page for six months.

That is not a discipline problem. It is a timing problem.

The insight from a build is sharpest in the 48 hours after you ship it. Then it goes flat. You move into the next headspace and the thing you just proved feels obvious, or worse, like it would take too long to explain well.

Build Debrief is a system I built to catch that window. You hand it a brain dump. It finds the real decision inside the build, the behavioral or architectural choice, not the feature, and converts it into five finished structures: a LinkedIn post, a case study outline, a resume sentence, a pitch sentence, and carousel slides.

The goal is not to generate content. The goal is to do most of the work before the clarity decays.

If you build things and lose the documentation every time, the problem is structural. So is the fix.

## Sample 2: Job-Fit explainer (Competition #7)

LLMs are most useful when they're helping us interpret information. Not when they're making the final decision.

That's what I kept coming back to while building Job-Fit: a screener built to show its work, not just its verdict.

Most AI scoring systems focus on the outcome:

A score, a ranking, a recommendation.

I was more interested in the process.

So I split the job.

The LLM extracts the context.
It reads the resume and the job description, then classifies what it finds: required skills, preferred skills, proof points, gaps, and screening risks.
That's the work I trust it to do.

The code handles the math.
The model never touches the final score. Deterministic rules compute the recommendation based on the evidence the LLM extracted.

Same inputs, same answer.

The result is a system where every recommendation traces back to specific evidence. Not a number floating in midair.

The model labels the evidence.
The rules compute the outcome.
That boundary is the whole design.

#AI #LLMs #ProductDesign #BuildInPublic

## Sample 1: Job-Fit announcement (Competition #7)

Most match scores give you a number and expect you to trust it.

That was the problem I built Job-Fit to solve.

Job-Fit reads a job posting and a resume, then tells you whether to apply, where you may get screened out, and what to fix before you do.

The important part is how it makes the decision.

The LLM does not pick the score.
It labels the evidence.

The code makes the call.

The model extracts what the job is asking for and what the resume actually shows. Then deterministic rules compute the verdict.

Same inputs. Same answer. Every time.

I built it to test whether I could design an AI system that stays honest in a domain I understand well.

Not “trust me, the AI said so.”

More like: here are the receipts, here is the rule, here is the outcome.

Jake Van Clief’s folder-based operator framework gave me the structure to push this further, and his read on the project helped sharpen where the next version should go.

For anyone building with AI: where do you draw the line between what the model labels and what the system decides?

---

