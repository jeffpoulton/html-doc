# html-doc

> Write documents in HTML, not markdown, when humans are the audience.

`html-doc` is an [agent skill](https://github.com/vercel-labs/skills) that teaches coding agents (Claude Code, Cursor, Codex, Gemini, Opencode, and 50+ others) to produce a single self-contained HTML file whenever you ask for a doc, spec, report, plan, writeup, design doc, deck, or any artifact a person will read, share, print, or open in a browser.

Markdown still wins for outputs another agent or renderer will consume (READMEs, code comments, GitHub issue/PR bodies, internal handoffs). HTML wins when the audience is human: it's information-denser, visually clearer, easier to share, and supports interaction in ways markdown cannot.

## Install

One command, any supported agent:

```bash
npx skills add jeffpoulton/html-doc
```

The CLI auto-detects which coding agents you have installed (Claude Code, Cursor, Codex, Gemini-CLI, Opencode, Goose, Continue, Cline, and many more) and places the skill in the right config directory. If none are detected, it prompts you.

For a manual install into Claude Code:

```bash
git clone https://github.com/jeffpoulton/html-doc.git ~/.claude/skills/html-doc
```

## What it does

Once installed, the skill auto-triggers when you ask your agent for any of:

- Specs, plans, implementation plans, PRDs
- Reports: status, incident, research
- Code reviews, PR writeups
- Design docs and design system references
- Explainers and concept walkthroughs
- Slide decks, dashboards, throwaway editor UIs
- Any other long-form artifact intended for a human reader

It produces a single self-contained HTML file: inlined CSS, inlined JS, inlined SVG. No external CDN, no build step, no framework. Open in any browser. The design system is a polished stone-grey / forest-green palette.

## Examples

The `examples/Green/` folder ships 20 reference HTML files covering every artifact type, plus a browsable catalog at [`examples/Green/index.html`](examples/Green/index.html).

- [`01-exploration-code-approaches.html`](examples/Green/01-exploration-code-approaches.html) — Debounced search: three code approaches
- [`02-exploration-visual-designs.html`](examples/Green/02-exploration-visual-designs.html) — Empty state: four visual directions
- [`03-code-review-pr.html`](examples/Green/03-code-review-pr.html) — PR review summary
- [`04-code-understanding.html`](examples/Green/04-code-understanding.html) — Authentication flow walkthrough
- [`05-design-system.html`](examples/Green/05-design-system.html) — Design system reference
- [`06-component-variants.html`](examples/Green/06-component-variants.html) — Card variant matrix
- [`07-prototype-animation.html`](examples/Green/07-prototype-animation.html) — Task-completed micro-interaction
- [`08-prototype-interaction.html`](examples/Green/08-prototype-interaction.html) — Sidebar drag-to-reorder prototype
- [`09-slide-deck.html`](examples/Green/09-slide-deck.html) — Platform engineering weekly slide deck
- [`10-svg-illustrations.html`](examples/Green/10-svg-illustrations.html) — Background job header illustrations
- [`11-status-report.html`](examples/Green/11-status-report.html) — Engineering status report
- [`12-incident-report.html`](examples/Green/12-incident-report.html) — Incident report
- [`13-flowchart-diagram.html`](examples/Green/13-flowchart-diagram.html) — Deploy pipeline flowchart
- [`14-research-feature-explainer.html`](examples/Green/14-research-feature-explainer.html) — Rate limiting feature explainer
- [`15-research-concept-explainer.html`](examples/Green/15-research-concept-explainer.html) — Consistent hashing interactive explainer
- [`16-implementation-plan.html`](examples/Green/16-implementation-plan.html) — Comment threads implementation plan
- [`17-pr-writeup.html`](examples/Green/17-pr-writeup.html) — Notification queue PR writeup
- [`18-editor-triage-board.html`](examples/Green/18-editor-triage-board.html) — Cycle triage board editor UI
- [`19-editor-feature-flags.html`](examples/Green/19-editor-feature-flags.html) — Feature flag editor UI
- [`20-editor-prompt-tuner.html`](examples/Green/20-editor-prompt-tuner.html) — Support reply prompt tuner

`examples/Green/05-design-system.html` and `examples/Green/14-research-feature-explainer.html` include an in-page palette switcher with named alternates for live comparison.

## Attribution

The reference HTML files in `examples/` and `MANIFESTO.md` are adapted from [Thariq](https://twitter.com/trq212)'s [html-effectiveness project](https://thariqs.github.io/html-effectiveness/). The original "unreasonable effectiveness of HTML" thesis is entirely his work. This repo packages those examples as an installable agent skill and adds the stone/green palette.

## License

MIT. See [LICENSE](./LICENSE).
