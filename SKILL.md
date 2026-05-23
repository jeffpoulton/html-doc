---
name: html-doc
description: 'Produce a self-contained HTML file instead of markdown whenever an artifact is intended for human consumption: specs, plans, reports, design docs, code reviews, research writeups, status updates, incident reports, explainers, slide decks, dashboards, and similar long-form work that someone will read, share, print, or open in a browser. Use whenever the user asks for any kind of document, report, writeup, plan, deck, explainer, design doc, or artifact, or whenever they explicitly ask for "HTML" or reference the `html-effectiveness` examples. Markdown remains the right format for outputs another agent will consume (READMEs, code comments, GitHub issue/PR bodies, internal handoffs to other agents) where the renderer or downstream pipeline expects plain text; HTML is the default when humans are the audience.'
---

# html-doc: HTML as the default output for human-consumed documents

You are producing a **single self-contained HTML file** that a person will
open in a browser, share via a link, or print. HTML is the right format
for this work because it is information-denser, visually clearer, easier
to share, and supports interaction in ways markdown cannot.

Reserve markdown for outputs that another agent (or a renderer that
demands plain text) will consume: READMEs, code comments, commit
messages, GitHub issue and PR bodies, and similar agent-to-agent or
machine-rendered surfaces. The distinction is the audience, not the
content. If the artifact is for humans, use this skill.

The visual language is the **stone/green aesthetic** used across every
example in `examples/Green/` — neutral stone-grey neutrals with a deep
forest-green primary accent. Match it. Consistency is the point: these
files should feel like a coherent body of work, not 20 different attempts.


## When to use this skill

Use HTML output for:

- **Specs, PRDs, implementation plans** → see `examples/Green/16-implementation-plan.html`
- **Design explorations** (multiple options side by side) → `Green/02-exploration-visual-designs.html`, `Green/01-exploration-code-approaches.html`
- **Code reviews / PR writeups** → `Green/03-code-review-pr.html`, `Green/17-pr-writeup.html`
- **Codebase understanding / module maps** → `Green/04-code-understanding.html`
- **Design systems & component variants** → `Green/05-design-system.html`, `Green/06-component-variants.html`
- **Prototypes & animations** → `Green/07-prototype-animation.html`, `Green/08-prototype-interaction.html`
- **Slide decks** (arrow-key navigable) → `Green/09-slide-deck.html`
- **SVG illustrations and flowcharts** → `Green/10-svg-illustrations.html`, `Green/13-flowchart-diagram.html`
- **Status & incident reports** → `Green/11-status-report.html`, `Green/12-incident-report.html`
- **Concept explainers & research** → `Green/14-research-feature-explainer.html`, `Green/15-research-concept-explainer.html`
- **Throwaway editor UIs** (triage, flag tuner, prompt editor) → `Green/18-editor-triage-board.html`, `Green/19-editor-feature-flags.html`, `Green/20-editor-prompt-tuner.html`

Before writing, **read at least one example that matches the use case**.
Then adapt. Don't reinvent the design system on each invocation.

Stick with markdown only for: README files, code comments, commit messages,
GitHub issues/PR descriptions where the GitHub renderer is mandatory.

## Hard rules

1. **One file. Self-contained.** No `<link>` to a CDN, no `<script src=…>`,
   no `<img src="https://…">`. Inline all CSS in `<style>`, all JS in
   `<script>`, all art as inline `<svg>`. The file must work when copied
   to `/tmp` with no network.
2. **No build step, no framework.** Vanilla HTML/CSS/JS. The reader opens
   `file://` and it works.
3. **No ASCII diagrams. No Unicode color hacks.** That's what we left
   markdown to escape. Use SVG, CSS gradients, real swatches.
4. **No emojis** unless the user asked. The aesthetic is editorial, not
   marketing.
5. **Mobile responsive.** Add a `@media (max-width: 880px)` collapse so
   the file reads on a phone.
6. **`<meta viewport>` always present.** `<title>` is the document title,
   not "Document".
7. **Save to a sensible path.** Default to the cwd unless the user says
   otherwise. Tell the user the path and offer to `open` it.

## The design system

Every example uses these tokens. Copy them verbatim into `:root` and
*don't* substitute your own palette:

```css
:root {
  --ivory:    #F7F7F7;   /* page background (stone) */
  --paper:    #FFFFFF;   /* cards, panes */
  --slate:    #222222;   /* headings, primary text */
  --clay:     #2F8132;   /* primary accent: links, callouts, highlights (now green) */
  --clay-d:   #1F4E1F;   /* hover/pressed primary */
  --oat:      #C1EAC5;   /* secondary tint (light green) */
  --olive:    #0E5814;   /* deep accent / success-tinted */
  --rust:     #B04A3F;   /* error/danger (semantic, unchanged) */
  --gray-100: #E1E1E1;   /* hairline backgrounds */
  --gray-150: #E1E1E1;
  --gray-200: #CECECE;
  --gray-300: #B1B1B1;   /* borders, rules */
  --gray-500: #7E7E7E;   /* muted text, eyebrows */
  --gray-700: #515151;   /* body text */

  --serif: ui-serif, Georgia, "Times New Roman", Times, serif;
  --sans:  system-ui, -apple-system, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  --mono:  ui-monospace, "SF Mono", Menlo, Monaco, Consolas, monospace;
}
```

Token names are retained for compatibility across every file, so the examples
keep a consistent contract (`--clay` is still the primary-accent slot,
even though its value is now green). Don't rename them.

**Type:**
- Headings: `var(--serif)`, `font-weight: 500`, `letter-spacing: -0.01em`.
- Body: `var(--sans)`, 15–16.5px, `line-height: 1.55–1.65`.
- Eyebrows (section labels above headings): `var(--mono)`, 11–12px,
  `letter-spacing: 0.08–0.12em`, `text-transform: uppercase`, `color: var(--gray-500)`.
- Code: `var(--mono)`, 13px, `background: var(--gray-100)`, `padding: 1px 5px`, `border-radius: 4px`.

**Layout:**
- `body { background: var(--ivory); padding: 56px 24px 96px; -webkit-font-smoothing: antialiased; }`
- Page container: `max-width: 980–1120px; margin: 0 auto;`
- Section spacing: `margin-bottom: 48–64px`.
- Cards/panes: `background: var(--paper); border: 1.5px solid var(--gray-300); border-radius: 12px; padding: 14–20px;`
- Hairlines: `border-top: 1px solid var(--gray-300)`.

**Accents:**
- Links: `color: var(--clay)`, `text-decoration-color: var(--oat)`, `text-underline-offset: 3px`.
- A short clay rule before an eyebrow (`width: 24px; height: 1.5px; background: var(--clay)`) is a recurring motif.

## Patterns by artifact type

### Implementation plan / PRD
- Eyebrow ("Implementation plan · 2026-05-13"), serif h1, lead paragraph.
- Optional prompt-box (`background: var(--gray-100); border: 1.5px solid var(--gray-300); border-radius: 12px`) quoting the original request.
- Numbered sections: scope, data model, API surface, migration, rollout, risks, open questions.
- Inline SVG for data flow / sequence diagrams. **Not ASCII.**
- Code snippets in `<pre>` with mono font and `--gray-100` background.
- Mockup blocks: thin-bordered rectangles showing the UI literal.
- Reference `examples/Green/16-implementation-plan.html` for the canonical layout.

### Exploration (multiple options)
- Grid of cards (`grid-template-columns: repeat(auto-fit, minmax(280px, 1fr))`).
- Each card: tiny eyebrow tag with the tradeoff name, mini mockup or code
  block, one-line rationale.
- Don't pick a winner — that's the user's job.

### Code review / PR writeup
- Diff rendered inline: two-column `<table>` or `<pre>` with `+` lines in
  `var(--olive)` background tint, `-` lines in `var(--rust)` tint.
- Margin annotations: floating boxes anchored to diff lines.
- Severity color-code: olive (nit), oat (suggestion), clay (must-fix), rust (blocker).

### Research / explainer
- Sticky left nav (200px) with mono labels, main column (1fr).
- Inline SVG diagrams for the central mechanism. Annotate generously.
- "Gotchas" section at the bottom.

### Editor UI
- Real interactivity: drag/drop, sliders, form bindings.
- **Always end with an export button**: "Copy as JSON", "Copy as prompt",
  "Copy as markdown". The output is what gets pasted back into Claude.
- State lives in JS in-memory only. No localStorage unless asked.

### Slide deck
- One `<section>` per slide, full-viewport.
- Arrow-key + Space navigation in JS.
- Slide counter in the corner. Press `?` for help is a nice touch.

## SVG diagrams

Use SVG for any diagram. Default viewBox `0 0 800 400` or similar.
Stroke nodes with `var(--gray-300)`, fill nodes with `var(--paper)`,
label with serif. Highlight the critical path in `var(--clay)`.

For arrows, define a single `<marker>` and reuse it. Example:

```html
<defs>
  <marker id="arrow" viewBox="0 0 10 10" refX="9" refY="5"
          markerWidth="6" markerHeight="6" orient="auto-start-reverse">
    <path d="M0,0 L10,5 L0,10 z" fill="var(--slate)" />
  </marker>
</defs>
<line x1="..." y1="..." x2="..." y2="..." stroke="var(--slate)"
      stroke-width="1.5" marker-end="url(#arrow)" />
```

## Workflow

1. Confirm scope. If the user said "PRD for X", clarify the audience,
   length expectation, and any unknowns before writing.
2. Pick the closest example from `examples/`. Read it (`Read` tool) to
   internalize the layout.
3. Write the new file, copying the `:root` tokens verbatim. Adapt the
   layout to the content.
4. Save to the cwd unless the user named a path. Use a kebab-case name
   that reflects the artifact (`comment-threads-prd.html`, not `doc.html`).
5. Tell the user the path. Offer to run `open <path>` so they can review.
6. If they ask for revisions, edit the file in place — don't make new ones.

## What not to do

- Don't add a "Generated by Claude" footer. The user will share this; let
  it stand on its own.
- Don't pull in Tailwind, Bootstrap, or any framework CSS. The design
  system above is complete.
- Don't use system emojis as icons. If you need an icon, draw it as inline
  SVG with `stroke="currentColor" fill="none"` (lucide-style).
- Don't autoplay anything, don't request permissions, don't fingerprint.
- Don't add a print stylesheet unless asked — but if you do, suppress nav
  and use `@page { margin: 0.6in; }`.
- Don't keep ASCII tables. Real `<table>` with `border-collapse: collapse`
  and `var(--gray-300)` borders always.

## Reference files in this skill

- `examples/Green/` — all 20 reference HTML files plus an index, repainted
  in the stone/green palette. Read the closest match before writing.
- `examples/Green/index.html` — the canonical catalog page; mirrors the
  design system in its purest form.
- `examples/Green/05-design-system.html` and `examples/Green/14-research-feature-explainer.html`
  also include a built-in palette switcher with named palettes for live
  comparison if you need to evaluate alternatives.
- `MANIFESTO.md` — the philosophical backing (Thariq's original post).
  Skim this if the user pushes back on "why HTML instead of markdown".
