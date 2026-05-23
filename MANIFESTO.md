# The Unreasonable Effectiveness of HTML

Source: Thariq (@trq212) on X, posted ~May 2026. Reproduced here as the
philosophical backing for the `html-doc` skill.

---

Markdown has become the dominant file format used by agents to communicate
with us. It's simple, portable, has some rich text capability and is easy
for you to edit. Claude has even gotten surprisingly good at using ASCII
to make diagrams inside of markdown files.

But as agents have become more and more powerful, I have felt that markdown
has become a restricting format. I find it difficult to read a markdown
file of more than a hundred lines. I want richer visualizations, color and
diagrams and I want to be able to share them easily.

I'm also increasingly not editing these files myself, but using them as
specs, reference files, brainstorming outputs, etc. When I do make edits,
I'm usually prompting Claude to edit them, which removes one of markdown's
largest benefits.

I've started preferring HTML as an output format instead of Markdown and
increasingly see this being used by others on the Claude Code team, this
is why.

## Why HTML?

### Information Density
HTML can convey much richer information compared to markdown. Tables, CSS
design data, SVG illustrations, code snippets, interactions via JS+CSS,
workflows in SVG, spatial data with absolute positioning, embedded images.
There is almost no information Claude can read that you cannot fairly
efficiently represent in HTML. Without it, the model resorts to ASCII
diagrams or estimating colors with Unicode characters.

### Visual Clarity & Ease of Reading
I tend not to actually read more than a 100-line markdown file. HTML
documents are easier to read — Claude can organize visually with tabs,
illustrations, links, mobile responsiveness.

### Ease of Sharing
Browsers don't render markdown natively. HTML you can upload to S3 and
share a link. Chance someone actually reads your spec is much higher.

### Two-way Interaction
HTML can include sliders, knobs, copy-to-prompt buttons. The document
becomes a control surface.

### Data Ingestion
Claude Code can ingest your file system, MCPs, browser, git history.
That's why the HTML it produces can be richer than a generic web tool.

### It's Joyful
Making HTML documents with Claude is more fun and makes you feel more
involved in the creation.

## How to get started

Don't overthink it — just ask Claude to "make an HTML file" or "make an
HTML artifact." The trick is knowing what you want the artifact to do.

## FAQ

- **Less token efficient?** Yes but worth it — and with 1MM context on
  Opus 4.7 it's not noticeable.
- **When do you use markdown now?** Almost never.
- **How do you view it?** Open locally, or upload to S3 for a link.
- **Doesn't this take longer?** 2-4× longer than markdown. Worth it.
- **Version control?** Biggest downside — diffs are noisy.
- **How do you keep it from being ugly?** Use a design system file as a
  reference. Point Claude at your codebase to derive one.

The real reason: I feel more in the loop with Claude than ever before.
