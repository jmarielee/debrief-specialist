# reference/output-templates.md

The exact skeleton for each output. The specialist fills these every session. Structure is fixed. Content comes from the brain dump.

---

## 1. LinkedIn post draft

A near-finished post she trims, not a brief she builds from. It should read like something she could publish after a light pass.

```
[Claim-first opening line: the idea or the decision, stated flat. No windup.]

[2 to 4 short sentences that prove the claim with the build. Name the
behavioral decision. Show the failure mode it avoids. Teach the one thing.
Aim any edge at the pattern, never a person.]

[Optional: one line of earned, specific gratitude, only if a real person
contributed a real thing this time. Never the opening.]

[CTA: one specific question a peer would actually answer.]

[Optional: up to three relevant hashtags, or none.]
```

Rules that bind this output: claim first, teach one thing, no em-dashes, flat declaratives, 120 words by default (up to ~250 only if the idea needs it), anonymized per Rule 5, voice matched to `reference/voice-samples.md`.

---

## 2. Portfolio case study outline

A six-part outline she can expand into a full case study. Each part is one to two tight sentences, not a paragraph. Anonymized where Rule 5 applies.

```
- Problem:         [the failure mode or gap the build addressed]
- Decision:        [the behavioral or architectural choice she made]
- Constraint:      [the hard limit she designed around]
- System behavior: [what the system actually does now, the mechanism]
- Evidence:        [proof it works: real metric, held-out test, or
                    explainability feature. Never a fabricated number.]
- Outcome:         [what changed, or the failure mode eliminated]
```

If a part is not supported by the dump, still write the line and flag it in Gaps & Boosts. Do not invent content to fill a part.

---

## 3. Resume-ready sentence

```
[Strong action verb] [the system or layer], [separating or enforcing what],
[to achieve what outcome]. No metric unless real.
```

One sentence. Drops straight into a resume line.

---

## 4. Pitch sentence

```
This is how I think: [the judgment the build reveals, not the feature,
the reasoning underneath it].
```

The highest-altitude output. What this build proves about how she thinks. The sentence she would say to a recruiter to explain why she is different.

---

## 5. Carousel SVGs

Six 1080×1080px SVG files generated every session. Use the Python pattern below, substituting content from the brain dump. Write to the outputs directory and present all six with `present_files`.

---

### Slide content structure

Each session, determine these six content blocks from the brain dump before generating code:

```
Slide 01 — hook
  headline_1:   [opening claim, line 1 — same as LinkedIn post opener]
  headline_2:   [opening claim, line 2 if needed]
  supporting:   [one secondary line, e.g. "The fix was not a better prompt."]
  illustration: score_dots | arrow | minimal_mark

Slide 02 — the problem.
  headline_1:   [failure mode, line 1]
  headline_2:   [failure mode, line 2 if needed]
  body_hl:      [first sentence — the highlighted proof sentence]
  body_rest:    [remaining sentence(s)]
  illustration: three_circles | relevant_shape

Slide 03 — the decision.
  headline_1:   [behavioral decision, line 1]
  headline_2:   [behavioral decision, line 2 if needed]
  body_hl:      [first sentence — highlighted]
  body_rest:    [remaining sentence(s)]
  illustration: compass | relevant_shape

Slide 04 — the principle.
  headline_1:   [transferable rule, line 1]
  headline_2:   [transferable rule, line 2 if needed]
  body_hl:      [first sentence — highlighted]
  body_rest:    [remaining sentence(s)]
  illustration: blob_vs_rect | relevant_shape

Slide 05 — the evidence.
  headline_1:   [what the proof looks like, line 1]
  headline_2:   [line 2 if needed]
  body_hl:      [first sentence — highlighted]
  body_rest:    [remaining sentence(s)]
  illustration: receipt | relevant_shape

Slide 06 — your turn.
  headline_1–4: [CTA question, split across lines — same as post CTA]
  illustration: arrow
```

---

### Design system constants

```python
import os
OUT = '/mnt/user-data/outputs'
os.makedirs(OUT, exist_ok=True)

F   = "'Plus Jakarta Sans', Arial, sans-serif"
YEL = '#F5CC38'   # yellow highlight fill
BLK = '#111111'   # headlines, illustrations
DGY = '#555555'   # body text (unhighlighted)
MGY = '#333333'   # labels
LGY = '#AAAAAA'   # slide number, footer name
RUL = '#E2E2E2'   # divider lines
```

---

### Helper functions (copy verbatim each session)

```python
def wrap(body):
    return (f'<svg xmlns="http://www.w3.org/2000/svg" width="1080" height="1080" viewBox="0 0 1080 1080">\n'
            f'  <rect width="1080" height="1080" fill="#FFFFFF"/>\n{body}\n</svg>')

def hdr(n):
    return (f'  <text x="72" y="116" font-family="{F}" font-size="32" font-weight="400" fill="{LGY}" letter-spacing="7">0{n} / 06</text>\n'
            f'  <line x1="275" y1="108" x2="1008" y2="108" stroke="{RUL}" stroke-width="1"/>')

def ftr():
    return (f'  <line x1="72" y1="965" x2="1008" y2="965" stroke="{RUL}" stroke-width="1"/>\n'
            f'  <text x="72" y="1002" font-family="{F}" font-size="30" font-weight="400" fill="{LGY}" letter-spacing="4">jodi paige-lee</text>')

def lbl(t):
    return f'  <text x="72" y="385" font-family="{F}" font-size="30" font-weight="600" fill="{MGY}" letter-spacing="5">{t}</text>'

def hl(y, w):
    # Yellow highlight rect behind a body text line. y = text baseline. w = estimated text pixel width.
    return f'  <rect x="68" y="{y-30}" width="{w}" height="44" rx="3" fill="{YEL}" fill-opacity="0.65"/>'

def tx(t, x, y, sz=36, wt="400", fill=DGY):
    return f'  <text x="{x}" y="{y}" font-family="{F}" font-size="{sz}" font-weight="{wt}" fill="{fill}">{t}</text>'
```

---

### Layout grid (fixed every session)

```
Slide number text:   x=72,  y=116,  font-size=32
Divider line:        y=108, x1=275, x2=1008
Illustration center: x=540, y=245   (illustration zone y=155–335)
Label:               x=72,  y=385,  font-size=30, weight=600
Headline line 1:     x=72,  y=447,  font-size=52, weight=600
Headline line 2:     x=72,  y=519
Headline line 3:     x=72,  y=591   (if needed)
Body line 1:         x=72,  y=590   (first body line after 2-line headline)
Body line 2:         x=72,  y=648
Body line 3:         x=72,  y=706
Footer rule:         y=965, x1=72,  x2=1008
Footer name:         x=72,  y=1002, font-size=30
```

**Highlight rect sizing.** Estimate width as: character_count × 19. Place the rect before (beneath) the text element. Use `hl(text_baseline_y, estimated_width)`.

**Text wrapping.** SVG does not auto-wrap. Break headline and body lines manually at phrase boundaries. Maximum ~34 characters per line at 52px; ~46 at 36px.

---

### Built-in illustrations (SVG paths, copy as needed)

**Score dots** (hook slide — adjust count filled/open to match the actual score):
```python
# 7 of 10 filled example — cx starts at 369, spacing 38px, radius 16
score_dots = '\n'.join(
    [f'  <circle cx="{369+i*38}" cy="245" r="16" fill="{BLK}"/>' for i in range(7)] +
    [f'  <circle cx="{369+(i+7)*38}" cy="245" r="16" fill="none" stroke="{BLK}" stroke-width="2.2"/>' for i in range(3)]
)
```

**Three-circle triangle** (problem slide):
```python
triangle = f'''  <circle cx="540" cy="178" r="26" fill="none" stroke="{BLK}" stroke-width="2.5"/>
  <circle cx="414" cy="312" r="26" fill="none" stroke="{BLK}" stroke-width="2.5"/>
  <circle cx="666" cy="312" r="26" fill="none" stroke="{BLK}" stroke-width="2.5"/>
  <line x1="540" y1="204" x2="424" y2="288" stroke="{BLK}" stroke-width="1.8"/>
  <line x1="540" y1="204" x2="656" y2="288" stroke="{BLK}" stroke-width="1.8"/>
  <line x1="440" y1="312" x2="640" y2="312" stroke="{BLK}" stroke-width="1.8"/>'''
```

**Compass / target** (decision slide):
```python
compass = f'''  <circle cx="540" cy="245" r="74" fill="none" stroke="{BLK}" stroke-width="3"/>
  <line x1="540" y1="171" x2="540" y2="197" stroke="{BLK}" stroke-width="3" stroke-linecap="round"/>
  <line x1="540" y1="293" x2="540" y2="319" stroke="{BLK}" stroke-width="3" stroke-linecap="round"/>
  <line x1="466" y1="245" x2="492" y2="245" stroke="{BLK}" stroke-width="3" stroke-linecap="round"/>
  <line x1="588" y1="245" x2="614" y2="245" stroke="{BLK}" stroke-width="3" stroke-linecap="round"/>
  <circle cx="540" cy="245" r="14" fill="{BLK}"/>
  <circle cx="540" cy="171" r="9" fill="{BLK}"/>
  <circle cx="540" cy="319" r="9" fill="{BLK}"/>
  <circle cx="466" cy="245" r="9" fill="{BLK}"/>
  <circle cx="614" cy="245" r="9" fill="{BLK}"/>'''
```

**Organic blob vs rectangle** (principle slide — LLM left, math right):
```python
blob_vs_rect = f'''  <path d="M400 190 C368 200 348 228 354 258 C360 288 386 308 416 302 C446 296 464 268 458 238 C452 208 432 180 400 190Z" fill="none" stroke="{BLK}" stroke-width="2.5"/>
  <line x1="537" y1="182" x2="537" y2="308" stroke="{BLK}" stroke-width="1.2" stroke-dasharray="6,4"/>
  <rect x="568" y="192" width="106" height="106" fill="none" stroke="{BLK}" stroke-width="2.5"/>
  <line x1="568" y1="245" x2="674" y2="245" stroke="{BLK}" stroke-width="1.2"/>'''
```

**Receipt / document** (evidence slide):
```python
receipt = f'''  <rect x="478" y="150" width="124" height="185" rx="6" fill="none" stroke="{BLK}" stroke-width="2.5"/>
  <line x1="500" y1="186" x2="582" y2="186" stroke="{BLK}" stroke-width="2.5" stroke-linecap="round"/>
  <line x1="500" y1="213" x2="574" y2="213" stroke="{BLK}" stroke-width="1.8" stroke-linecap="round"/>
  <line x1="500" y1="238" x2="582" y2="238" stroke="{BLK}" stroke-width="1.8" stroke-linecap="round"/>
  <line x1="500" y1="262" x2="558" y2="262" stroke="{BLK}" stroke-width="1.8" stroke-linecap="round"/>
  <line x1="500" y1="286" x2="576" y2="286" stroke="{BLK}" stroke-width="1.8" stroke-linecap="round"/>'''
```

**Arrow** (CTA slide):
```python
arrow = f'''  <line x1="360" y1="245" x2="704" y2="245" stroke="{BLK}" stroke-width="4" stroke-linecap="round"/>
  <line x1="662" y1="203" x2="704" y2="245" stroke="{BLK}" stroke-width="4" stroke-linecap="round"/>
  <line x1="662" y1="287" x2="704" y2="245" stroke="{BLK}" stroke-width="4" stroke-linecap="round"/>'''
```

**Choosing illustrations for non-standard builds.** If the build does not match the default illustrations above, substitute a simple black line illustration that reflects the build's mechanism. Keep it minimal — a few strokes, no fills, centered at x=540 y=245.

---

### Output and presentation

```python
slides = [s1, s2, s3, s4, s5, s6]
for i, body in enumerate(slides, 1):
    p = f'{OUT}/carousel-0{i}.svg'
    open(p, 'w').write(wrap(body))

# Then call present_files with all six paths.
```

**After generating:** present all six files. No further explanation needed — the files speak for themselves.

---

## Gaps & Boosts (closing section, 2 to 4 bullets)

```
- [Missing metric, if any: what to quantify and where it would land]
- [Any claim softened because the dump did not fully support it]
- [NDA note, if anonymization was applied: which entity was stripped]
- [Where 5 more minutes of her input most improves the set]
```
