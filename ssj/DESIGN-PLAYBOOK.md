# Website Design Playbook — Impressive Builds with AI

A repeatable prompting + workflow pattern for producing award-quality websites with AI,
distilled from two sources:

1. **"Claude Fable 5 UI/UX One-Shots"** — how to write the first prompt so the one-shot
   lands at 80% (Part 1)
2. **"Claude Design Workflow"** — how to refine from first draft to polished, intentional
   design (Part 2)

Plus our own project experience (SSJ hero, Daulat demo). Use this every time we start or
redesign a site.

**Core truth from both videos:** the first generation is never the product — it's raw
material. Generic prompts produce generic designs; give the same vague prompt to 100
people and all 100 results look identical. Specificity up front + structured refinement
after is what separates polished from template.

---

## Part 1 — The One-Shot: 6 Rules for the First Prompt

### 1. Name the ambition level in the prompt
Don't say "make a landing page." Say **"design and build a modern, awards-worthy landing
page"** — words like *awards-worthy*, *Awwwards-style*, *cinematic*, *editorial* anchor
the output to a high design bar. A neutral request produces the generic AI aesthetic
(centered hero, three feature cards, purple gradient).

### 2. Name the tech that produces the polish
Motion is what separates "clean" from "impressive." Explicitly ask for:
- **GSAP** — scroll-triggered animations, split-text / per-character reveals, staggered
  entrances, well-tuned easing
- **Three.js** (when it fits) — shaders, 3D scenes, WebGL galleries
- Subtle hover states with good easing on cards, links, buttons

If you don't ask for motion, you get a static page.

### 3. Give visual references, not just words
The strongest results come from attaching a **screenshot, URL, or screen recording** of a
site you admire and saying "recreate this concept" or "match this mood." A reference
communicates layout, spacing, and motion far more precisely than any paragraph.

Good hunting grounds: [awwwards.com](https://www.awwwards.com),
[godly.website](https://godly.website), [land-book.com](https://land-book.com).

### 4. Build verification into the prompt
End the prompt with: **"Check your work in Chrome DevTools and make sure it's fully
responsive on mobile."** This makes the model open the result, resize it, click through
interactions, and fix its own bugs (clipped text, overflow, broken taps) before handing
it back. Mobile-first review is non-negotiable — most traffic is mobile.

### 5. Constrain the personality, don't erase it
When redesigning an existing site, state what must **stay**, not just what should change:
- "Keep it type-heavy, don't go crazy with whitespace" (the Craigslist lesson)
- "Preserve the brand's gold/dark jewel tones" (SSJ)
- "Subtle interactions only, nothing flashy"

Constraints that preserve character prevent the redesign from collapsing into a generic
template.

### 6. Cover the four pillars: Goal, Layout, Content, Audience
Every strong prompt tells the AI four things so it never has to fill gaps with the
safest (most generic) choices:

- **Goal** — what the page must achieve ("get local people to come in and buy beans")
- **Layout** — the sections and their order ("full-width hero → brand story → featured
  products → visit-us block")
- **Content / brand voice** — mood and copy direction ("warm, crafted, slightly premium;
  single-origin, small-batch — keep the copy in that voice")
- **Audience** — who it's for ("local coffee lovers who care about quality and craft,
  not a big chain")

Thirty extra seconds here improves the result more than any trick applied afterward.

---

## Part 2 — The Refinement Workflow: First Draft → Polished

The one-shot gets you to ~80%. The remaining 20% comes from refining in the **right
order**. Golden rule: **large changes before small ones** — get structure and visual
direction right first, or you'll redo every button tweak each time a section moves.

### Step 1 — Fix the structure (big, page-wide changes)
Use broad instructions for anything affecting the whole page: section order, layout,
visual hierarchy, overall presentation.

- Surface what matters early: *"Move the featured products just below the hero — the
  product should be one of the first things people see."*
- Set the visual direction in one sweep: *"Make the whole page feel warmer and more
  editorial. Deeper, richer tones, more generous spacing — the polished look of a
  high-end brand."*

### Step 2 — Polish the details (targeted, element-level changes)
Once structure is settled, refine individual elements. Point at the exact element
(inline comment / click-to-select where available; otherwise name it precisely in chat):

- CTA button: bigger, more padding, primary brand color so it draws attention
- Cards: more internal spacing, slightly softer corners
- Hero headline: larger, tighter typography, stronger presence

No single tweak transforms the page — refinement is small improvements that accumulate.

### Step 3 — Explore alternatives before committing
Beginners pick one direction and endlessly tweak it; designers compare options first.
For any high-stakes section (especially the hero):

1. **Save the current version first** — *"Keep this version safe so we can come back to
   it."* (In git: commit before experimenting.)
2. Ask for variations: *"Show me three alternative layouts for the hero section only.
   Keep everything else the same."*
3. Compare side by side and pick the strongest (e.g., split editorial layout vs.
   centered minimal vs. framed-inset with product card layered in) — often a framed or
   product-forward hero beats the default.

A few minutes comparing directions beats hours tweaking the first idea that appeared.

### Step 4 — Iterate defects by name
Expect misses even in a great one-shot (a hover effect misread as scroll, clipped
descenders, weak intro). Open it in a real browser on desktop **and** mobile, then file
2–5 targeted follow-ups naming the exact defect:

- "The reveal should be hover-driven, not scroll-driven"
- "Descenders (g, p) are clipped on the shimmer headline"
- "The stagger easing feels too slow — tighten to ~0.6s with power3.out"

### Step 5 — Ship it
When the design is final: export standalone HTML or hand off to Claude Code for a real
build; use PDF/share links when collecting feedback from clients before development.

---

## Prompt Template

> Design and build a modern, awards-worthy landing page for **[subject]**.
> **Goal:** [what the page must achieve].
> **Layout:** [sections in order: hero → … → CTA].
> **Brand/content:** [mood + voice the copy must keep].
> **Audience:** [who it's for].
> Reference the attached screenshot of **[site]** for mood and layout.
> Use GSAP for scroll-triggered and split-text animations, with subtle, well-eased hover
> interactions [+ Three.js for [3D element] if wanted].
> Keep **[constraint that must survive: type-heavy / dark / minimal / brand colors]**.
> Check your work in Chrome DevTools and make sure it's fully responsive on mobile.

Then refine in order: **structure → visual direction → element details → compare
alternatives → fix defects by name.**

---

## The meta-lesson

Everyone has access to the same models — the differentiator is **taste**: picking the
right references, hearing when the easing feels off, knowing what to cut, and comparing
directions instead of settling for the first draft. The model gets you in the room; your
eye wins the award.
