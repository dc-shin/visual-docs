# visual-docs

A Claude Code plugin that produces design, analysis, and specification documents as rich, self-contained HTML files instead of plain Markdown.

## What it does

When you ask Claude to write a design doc, architecture document, technical spec, data analysis report, or any document meant to be read and shared, this skill outputs a single `.html` file with:

- Inline CSS and a clean readable font via Google Fonts
- Mermaid.js diagrams (flowchart, sequence, ER, state, gantt, ...)
- Chart.js charts and graphs
- highlight.js syntax-highlighted code blocks
- KaTeX math formulas
- Callout boxes, stat cards, badges, styled tables, TOC sidebar

Libraries are loaded from CDN only when the document actually uses them.

## Install

From the Claude Code community marketplace:

```
/plugin marketplace add anthropics/claude-plugins-community
/plugin install visual-docs@claude-community
```

Or install straight from this repository (works immediately, before the community listing is live):

```
/plugin marketplace add dc-shin/visual-docs
/plugin install visual-docs@dc-shin
```

To update the direct install later, run `/plugin marketplace update dc-shin` and reinstall.

For local development without installing, load the plugin directly:

```bash
claude --plugin-dir ./visual-docs.zip
```

## Usage

The skill triggers automatically. To invoke it explicitly:

```
/visual-docs:visual-docs
```

Or just ask naturally:

- "Write a design doc for the payment service"
- "Write an architecture RFC for the new auth service"
- "Create an EDA analysis report from this dataset"
- "Create a competitive analysis report"
