# Prompt template: interactive scrolling technical presentation

Copy everything below the line, fill in the `{…}` fields, and delete any optional lines you don't need. Give the whole scope up front: changing it mid-way (adding topics or excluding areas) forces rework.

---

Write a single self-contained HTML presentation on **{SUBJECT}**.

**Audience:** {e.g. a novice engineer who knows basic algebra and vectors but nothing about the field}.

**Purpose:** {e.g. to explain the subject from first principles, with the mathematics shown graphically, and to survey current technology and companies}.

## Content

Cover these topics, in a logical teaching order (foundations → math → real-world effects → applications → industry → summary):

- Introduction: what {SUBJECT} is, why it matters, and how it compares with {RELATED/CONTRASTING SUBJECT}.
- {Topic 1}
- {Topic 2 — the core concept to explain in depth, e.g. "the meaning and math of X, with extensive explanation"}
- {Topic 3}
- …
- A **worked numerical example**: {describe the case, e.g. "4 sensors at given coordinates, noisy measurements, solve step by step"}. Show every intermediate number (inputs, matrices, iterations, final result, error estimate). Verify all numbers with an independent calculation before putting them in the page.
- History / legacy systems: {list, or delete}.
- Leading current technologies and the companies behind them.
- Emerging technologies and companies to watch.
- Use cases, with the requirements that drive each one.
- Limits: {e.g. resolution limits, theoretical vs real hardware size, physical bounds}.
- Summary: the 5 things to remember, plus a glossary.

**Must include:** {specific names, systems, standards, companies the audience expects to see}.
**Exclude:** {areas to leave out, e.g. "indoor-only solutions"}.

## Format and structure

- One long page that **scrolls freely**, but divided into numbered **sections**, each one a unit you could present on its own.
- A sticky top bar with the current section number and title, prev/next buttons, a progress bar with one segment per section, and a section menu.
- Keyboard: ←/→ (and PageUp/PageDown) jump between sections, `F` toggles "focus mode" (sections not in view are dimmed), `M` opens the section list. Don't capture keys while a slider or select has focus.
- An auto-generated table of contents in the introduction, grouped by part.
- Each section has a small kicker (number + part name), a heading, and usually a two-column layout: explanation and math on one side, figure on the other.

## Teaching style

- Each conceptual section opens with an **"In plain words"** box: intuition and an analogy, no jargon.
- Then the **math**, rendered with MathJax in visually distinct boxes, with short labels above each equation saying what it is. Derive key results step by step; box the formulas engineers actually use.
- Then a **figure**. At least one figure, animation or interactive visualization in **every** section.
- Use tables for comparisons (specs, accuracy, history, companies).
- Give real numbers with units everywhere: worked checks like "20 ppm × 300 µs → 3 ns → 0.9 m".
- Write plainly: short sentences, active voice, no filler.

## Figures and interactivity

- Draw figures live in the browser with `<canvas>` (or inline SVG), computed from the actual equations, not static pictures.
- Make most of them interactive: draggable points, sliders, preset buttons, hover readouts. Show key computed values as small "chips" under each figure (good/moderate/bad coloured).
- Use animation where motion explains something (signals propagating, iterations converging, objects moving). Pause animations when off-screen and respect `prefers-reduced-motion`.
- Every figure has a title and a one- or two-sentence caption saying what to look at.
- Charts drawn to scale, with labelled axes and units; log axes where values span decades.

## Visual design

- Clean engineering look: one sans-serif body font, one monospace font for labels and numbers (Google Fonts), tabular numbers.
- All colours as CSS tokens, with a full **light and dark theme** (`prefers-color-scheme` plus `data-theme` overrides). Canvas figures read the tokens and redraw on theme change.
- A small consistent palette with fixed meanings across all figures (e.g. blue = reference/infrastructure, orange = the unknown being estimated, yellow = noise/error, violet = math, red = blocked/bad).
- Responsive down to 390 px phone width with no horizontal page scroll; wide tables scroll inside their own container.

## Technical constraints

- One `.html` file. The only external resources: MathJax from cdnjs and Google Fonts. All other JS/CSS inline, no frameworks.
- Organise the JS as a small framework: a figure registry, a shared render loop, a resize observer, a drag helper, slider binding, and shared math helpers (e.g. matrix inverse, least squares, eigenvalues).
- Keep facts accurate. Where a number, date or company status is uncertain, use approximate wording or hedge it rather than inventing precision. Label qualitative charts as qualitative.

## Process and deliverables

1. Before writing the page, compute the worked-example numbers independently (e.g. in Python) and use exactly those values.
2. Build the page; check the script for syntax errors; render it headlessly and check every section for console errors, overlapping labels and horizontal overflow at desktop and phone widths. Fix what you find.
3. Save it as `{FILENAME}.html` in the repository, add a short section to the README (how to open and navigate it, plus a table of parts and topics), commit and push.
4. Also publish it as a viewable page if the environment supports it, and tell me which facts you were unsure about.
