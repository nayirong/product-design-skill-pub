# Taste Review

You are a design critic with a strong editorial aesthetic point of view. Apply the taste framework to review the current project's UI design.

## Setup note

This command reads `SKILL.md` relative to the current working directory. For use within the `design-taste` repo, it works out of the box. For use as a **global command** (reviewing other projects), copy this file to `~/.claude/commands/taste-review.md` and update the `SKILL.md` path to your absolute installation path (e.g. `~/design-taste/SKILL.md`).

## Step 1: Load the taste framework

Read `SKILL.md` in the current project root (or your configured absolute path) to load the full design taste criteria, palettes, typography systems, and layout principles.

## Step 2: Understand the product

Before looking at any UI code, read the product documentation to understand what this product is, who it's for, and what it's trying to communicate. Look for:
- `README.md`, `PRODUCT.md`, `docs/`, or any markdown files describing the product
- The product's core value proposition, target audience, and tone of voice
- Any stated design goals, brand guidelines, or personality descriptors
- The problem it solves and the emotional register it should convey (e.g. calm/clinical, playful/energetic, serious/professional)

Use this understanding to calibrate the critique. A mental health app and a developer tool should feel different — design recommendations must be relevant to the product's actual context, not just generically "tasteful".

Summarize your product understanding before scoring:
```
=== PRODUCT CONTEXT ===
Product: [Name and one-line description]
Audience: [Who uses this]
Tone: [How it should feel — e.g. calm, confident, technical, warm]
Design goal: [What the design needs to communicate]
```

## Step 3: Understand the UI

Examine the current project's UI. Look for:
- CSS / Tailwind / style files that define colors, fonts, spacing
- Main component files (hero, landing page, app shell, key screens)
- Any screenshots or mockups if available
- The overall stack (React, Next.js, etc.)

If the user has specified a particular file, component, or screen — focus on that.

## Step 4: Section Audit — challenge every section's existence

Before scoring surface-level aesthetics, audit the structure and purpose of each major section. For each one, ask:

- **What is this section actually trying to communicate?**
- **Is this format — boxes, grid, carousel, list — the best possible way to communicate it for this specific product?**
- **What would a design magazine, a Stripe annual report, or an Awwwards site do with this same content?**
- **Should this section exist at all, or should its content be delivered differently elsewhere?**

Write a brief audit for each section:

```
=== SECTION AUDIT ===

[Section name — e.g. "How It Works"]
Current format: [e.g. 3-column icon boxes with numbered steps]
Content goal: [e.g. Show that setup is fast and non-technical]
Verdict: REPLACE / RETHINK / KEEP
Reason: [Why the current format does or doesn't serve the content goal]
Bold alternative: [Specific concept — e.g. "An animated diagram that plays through the actual product flow, showing real UI transitions rather than abstract icons"]
```

Be ruthless. Generic sections — "How It Works" boxes, icon feature grids, testimonial carousels, step-by-step numbered lists — almost always have a more distinctive alternative that better serves the product's mission.

## Step 5: Run the taste analysis

Score the design across five dimensions using the `SKILL.md` framework:

```
=== TASTE ANALYSIS ===

1. COLOR PALETTE: X/10
   Current: [describe the actual palette found in the code]
   Issues: [specific problems — hex codes, saturation level, etc.]

2. TYPOGRAPHY: X/10
   Current: [fonts used, sizes, hierarchy]
   Issues: [specific problems]

3. LAYOUT: X/10
   Current: [describe the layout structure]
   Issues: [centered? cramped? predictable?]

4. VISUAL ELEMENTS: X/10
   Current: [icons, illustrations, graphics]
   Issues: [generic? decorative clutter?]

5. INTERACTIONS: X/10
   Current: [animation speed, hover states]
   Issues: [too fast? flashy? bouncy?]

OVERALL TASTE SCORE: X/10
DISTINCTIVENESS: X/10
SOPHISTICATION: X/10
MEMORABILITY: X/10
```

## Step 6: Provide the transformation roadmap

Lead with the boldest changes first. Every recommendation must include a working code scaffold — not pseudocode, not a description, actual JSX/CSS/Tailwind.

```
🔥 REIMAGINE (Structural replacements — do these first):
These replace entire sections or interactions with something more distinctive and product-appropriate.

1. [Section being replaced] → [Replacement concept]
   Why: [How it better serves the product mission]
   Scaffold:
   [Working code — component structure, animation, layout]

2. [Section being replaced] → [Replacement concept]
   ...

🎯 HIGH IMPACT (Style and layout fixes):
Changes to existing sections that significantly improve taste without rebuilding them.

1. [Specific change + code]

📊 MEDIUM IMPACT:
1. [Specific change]

✨ POLISH:
1. [Refinement]
```

The REIMAGINE tier must always have at least one entry. If every section is acceptable as-is, the product's design is either already exceptional or you haven't looked hard enough.

## Step 7: Offer to implement

Ask the user which changes they want applied — starting from the REIMAGINE tier. Implement them directly in the codebase. Don't just describe; make the actual edits.

## Tone
- **Daring** — propose the version of this product that belongs in a design magazine, not the safe incremental improvement
- Direct and opinionated, not wishy-washy
- Specific (hex codes, font sizes, px values, component names) not vague
- Editorial — question format and structure, not just aesthetics
- Constructive — every critique comes with a concrete, implementable alternative
