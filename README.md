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

The `examples/` folder ships 20+ reference HTML files covering every artifact type. Two palette variants:

- **`examples/Green/`** — the active design system (stone neutrals + forest green accent)
- **`examples/Anthropic/`** — original Anthropic ivory/clay set, preserved for reference

`examples/Green/05-design-system.html` and `examples/Green/14-research-feature-explainer.html` include an in-page palette switcher with 17 named alternates (Refactoring UI palettes plus three earthy variants) for live comparison.

Browse the catalog: `examples/Green/index.html`.

## Attribution

The reference HTML files in `examples/` and `MANIFESTO.md` are adapted from [Thariq](https://twitter.com/trq212)'s [html-effectiveness project](https://thariqs.github.io/html-effectiveness/). The original "unreasonable effectiveness of HTML" thesis and the canonical ivory/clay aesthetic are entirely his work. This repo packages those examples as an installable agent skill and adds the stone/green palette variant.

## License

MIT. See [LICENSE](./LICENSE).
