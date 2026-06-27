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

In Claude Code, add this repository as a marketplace and install the plugin:

```
/plugin marketplace add dc-shin/visual-docs
/plugin install visual-docs@dc-shin
```

To update later, run `/plugin marketplace update dc-shin` and reinstall.

For local development without installing, you can also load it directly:

```bash
claude --plugin-dir ./visual-docs.zip
```

## Usage

The skill triggers automatically. To invoke it explicitly:

```
/visual-docs:visual-docs
```

Or just ask naturally:

- "결제 서비스 설계 문서 작성해줘"
- "Write an architecture RFC for the new auth service"
- "EDA 결과 분석 보고서 만들어줘"
- "Create a competitive analysis report"
