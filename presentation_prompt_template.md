# Prompt template: interactive, offline, scrolling technical presentation

This template reproduces the style of [`LPS_Local_Positioning_Systems.html`](LPS_Local_Positioning_Systems.html): one HTML file that scrolls freely but is split into presentable sections, with plain-language explanations, typeset math, a live figure in every section, and no internet needed when presenting.

**How to use it**
1. Copy everything below the line into a new session.
2. Fill in the `{…}` fields and delete the lines you don't need.
3. Give the whole scope at once: every topic, every name you expect to see, every exclusion. Adding topics or exclusions halfway through forces rework, so if you think of more, send them together in one message.
4. If this repository is available to the session, keep the "Reference" line: pointing at the existing file is the most reliable way to get the same look.

---

Write a single self-contained HTML presentation on **{SUBJECT}**.

**Hard requirement: it must work fully offline.** I will present it from a laptop with no internet. The final file must open by double-click (a `file://` URL) and look and work exactly the same with the network unplugged: equations typeset, fonts correct, every figure and animation working. Network access is allowed while you build it, never when the page is viewed. If any part cannot be made to work offline, tell me before delivering.

## Inputs

- **Audience:** {e.g. a novice engineer who knows basic algebra and vectors but nothing about the field}
- **Purpose:** {e.g. explain the subject from first principles, show the math graphically, and survey current technology and companies}
- **Scope:** {e.g. "outdoor and wide-area systems only" — say what is in and what is out}
- **Length:** about {20–27} sections
- **Language:** {English}
- **File name:** `{FILENAME}.html`
- **Reference:** match the structure, components and visual style of `LPS_Local_Positioning_Systems.html` in this repository (read it first).

## Content

Cover these topics in a teaching order: foundations → math → real-world effects → platforms or applications → design and limits → history → industry → summary.

- **Title section:** the subject's name, a one-paragraph thesis, topic tags, how to navigate, and an animated hero figure showing the subject's core mechanism.
- **Introduction:** what {SUBJECT} is, why it matters, how it compares with {RELATED/CONTRASTING SUBJECT}, and an auto-generated table of contents.
- {Topic 1}
- {Topic 2 — the core concept, explained in depth: meaning, derivation, special cases with closed forms, and an interactive playground}
- {Topic 3}
- …
- **Worked numerical example:** {describe the case, e.g. "4 sensors at given coordinates, noisy measurements, solve step by step"}. Show every intermediate number: inputs table, matrices, each iteration, the result, the error estimate and how to interpret it. Add a short iteration log and a to-scale figure with a zoomed view of the answer.
- **Real-world effects and limits:** {e.g. error sources, resolution limits, theoretical vs real hardware size, physical bounds}.
- **History / legacy systems:** {list, or delete}, with a comparison table (origin, years, method, coverage, accuracy).
- **Leading current technologies and companies**, as cards (key parameters, short description, company chips), plus a milestones timeline.
- **Spotlights:** {companies or systems that deserve their own subsection, with a figure each}.
- **Emerging technologies and companies to watch.**
- **Use cases**, with a requirements map (e.g. needed accuracy vs update rate) and cards per domain.
- **Regulation / standards:** {e.g. E911, relevant standards bodies, or delete}.
- **Summary:** the 5 things to remember, a glossary, and one figure that ties the whole subject together.

**Must include:** {names, systems, standards and companies the audience expects to see}
**Exclude:** {areas to leave out}

## Page format and navigation

- One long page that **scrolls freely**, divided into numbered **sections**, each one a unit you could present on its own. Section height follows its content (no forced full-screen panels).
- A sticky top bar: short brand label, current section number and title, prev/next buttons, a **Focus** toggle and a **Sections** menu; below it, a segmented progress bar (one segment per section) and a thin overall scroll bar.
- **Focus mode**, on by default and remembered per viewer: sections not in view are dimmed so the audience looks at the current one.
- Keyboard: ←/→, PageUp/PageDown and `n`/`p` jump between sections; Home/End go to first/last; `F` toggles focus mode; `M` opens the section list; Esc closes it. Ignore these keys while a slider, select or text field has focus.

## Section anatomy

Every section uses the same building blocks:

- A **kicker**: section number plus part name (e.g. "08 · Geometry").
- An **h2 heading** that states the idea, not just the topic.
- An **"In plain words"** box first: intuition and an analogy, no jargon.
- **Math boxes**: each equation has a small uppercase label above it saying what it is ("Covariance of the estimate", "Example: …"). Derive key results step by step and box the formulas engineers actually use.
- A **figure card**: title, the canvas, controls (sliders, selects, preset buttons, checkboxes), a row of result **chips** coloured good / moderate / bad, an optional colour legend, and a one- or two-sentence caption saying what to look at.
- Supporting blocks where useful: comparison tables, note boxes, numbered step lists for derivations, and cards for technologies or companies.
- Layout: usually two columns (text and math on one side, figure on the other, alternating sides), collapsing to one column on narrow screens.

## Teaching style

- Teach from first principles, one idea at a time, building on the previous section and referring back to it by section number.
- Give real numbers with units everywhere, including quick checks such as "20 ppm × 300 µs → 3 ns → 0.9 m".
- Show both the formula and what it means physically; when a closed form exists for a special case, derive it and plot it.
- Write plainly: short sentences, active voice, no filler, no hype.
- Keep facts accurate. Where a number, date or company status is uncertain, use approximate wording or hedge it rather than inventing precision. Label qualitative charts as qualitative.

## Figures and interactivity

- At least one figure in **every** section, drawn live with `<canvas>` (or inline SVG) and computed from the actual equations, never static images.
- Make most figures interactive: draggable points, sliders, presets, hover readouts. Patterns that work well:
  - a playground where moving the inputs updates a computed result, with a Monte Carlo point cloud checked against the predicted error ellipse or distribution;
  - an animation of the mechanism (signals propagating, iterations converging, objects moving);
  - a closed-form curve with a marker that follows a slider;
  - a side or top view of a real scenario with adjustable dimensions;
  - a heat map over an area with hover values and a colour legend;
  - log-scale range bars comparing technologies;
  - a to-scale size comparison;
  - a timeline that animates through the years;
  - a qualitative bubble chart, clearly labelled as qualitative.
- Pause animations when off-screen; respect `prefers-reduced-motion` by drawing one representative still frame.
- Charts to scale, with labelled axes and units; log axes where values span decades. Keep labels from overlapping and inside the canvas.

## Visual design

- Clean engineering look: one sans-serif body font (e.g. Inter) and one monospace font for labels, chips and numbers (e.g. JetBrains Mono); tabular numbers.
- All colours as CSS tokens on `:root`, with a full **light and dark theme** (`prefers-color-scheme` plus `data-theme="light|dark"` overrides). Canvas figures read the tokens and redraw on theme change. Equations follow the theme colour.
- A small palette with fixed meanings across all figures (e.g. blue = reference / infrastructure, orange = the unknown being estimated, yellow = noise / error, violet = math, aqua = satellites or the secondary system, red = blocked / bad).
- Works from 390 px phone width up: no horizontal page scroll; wide tables and display equations scroll inside their own container; long inline equations scale down; chips wrap.

## Offline and technical requirements

- **One `.html` file that works fully offline**, with no external URLs at all, because it will be presented without internet.
- **Math:** write TeX in the source with `\( … \)` and `\[ … \]`, then **pre-render every equation to inline SVG at build time** with MathJax in Node (`mathjax-full`, TeX input with all packages, SVG output with a global font cache) and inline the MathJax SVG stylesheet. No MathJax script loads at runtime. Only process the body content, not the `<script>`.
- **Fonts:** embed them as base64 `woff2` `@font-face` rules: variable fonts, one face per family and subset with a weight range, Latin + Latin Extended + Greek subsets. Redraw all canvases once `document.fonts.ready` resolves. Every `font-family` also lists a system fallback stack.
- **Fallbacks if the build machine cannot download something:** if `mathjax-full` cannot be installed, inline the complete MathJax `tex-svg` bundle in a `<script>` (larger file, still offline) instead of loading it from a CDN; if the fonts cannot be downloaded, use system font stacks only. Never fall back to a CDN or a Google Fonts link.
- **Nothing else external either:** no images, icons, scripts, stylesheets, iframes or fetches from the web. Images, if any, are inline SVG or `data:` URIs. Canvas text uses the embedded font names.
- **No frameworks or libraries at runtime**; all CSS and JS inline. Organise the JS as a small framework: a theme-token reader, a figure registry with a shared `requestAnimationFrame` loop, `ResizeObserver` and `IntersectionObserver`, a drag helper, slider binding, chip rendering, drawing primitives, a world-to-screen fit helper, a chart-frame helper, and shared math (matrix inverse, least squares, eigenvalues of 2×2, determinants).
- Use browser storage only for per-viewer conveniences (e.g. the focus-mode setting), wrapped in try/catch.

## Build approach

- Write the page in parts, not one giant file: head and CSS, the section HTML (in a few files), and the JS (in a few files). Assemble them with a small build script, then run the offline step (embed fonts, pre-render math) to produce the final file.
- Keep a copy of each part so later edits (renumbering sections, adding or removing a topic) are quick, targeted replacements instead of rewrites.
- Compute the worked-example numbers independently first (e.g. in Python) and use exactly those values in the text, tables and figures.

## Verification checklist (do all of it before delivering)

- [ ] The main script parses (syntax check).
- [ ] Every canvas id in the HTML has a figure in the JS, and every element id the JS looks up exists.
- [ ] The math pre-render reports zero TeX errors.
- [ ] Headless browser render with **all network requests blocked**: no console or page errors, both fonts load, every equation is present.
- [ ] Screenshots of the sections in **light and dark** themes look right: no overlapping labels, nothing clipped, legends readable.
- [ ] No horizontal overflow at desktop width and at 390 px.
- [ ] The final file contains no `http://` or `https://` resource references (`src=`, `href=`, `url(`, `@import`, `fetch(`); plain hyperlinks in the text are allowed.
- [ ] **Offline acceptance test:** open the final file from disk (`file://`) in a headless browser with every non-`file:` request aborted, and report the number of blocked requests (must be 0), whether each embedded font loaded, and how many equations rendered.
- [ ] Section numbers are continuous, and every "see section N" cross-reference points to the right place.

## Deliverables

1. Save it as `{FILENAME}.html` in the repository.
2. Add a short README section: how to open and navigate it, that it works offline, and a table of parts and topics.
3. Commit and push.
4. Publish it as a viewable page if the environment supports it, but make clear that an online link is only for previewing: for offline presenting I use the `.html` file itself, downloaded to my machine.
5. In your reply, list the facts you were unsure about and any interpretation you made of an ambiguous request.
