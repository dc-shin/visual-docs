---
name: visual-docs
description: >-
  Produce any substantive technical or business document as a rich, self-contained HTML file instead of plain Markdown, with inline CSS, a clean readable font via Google Fonts, and conditional CDN libraries (highlight.js for code, Mermaid.js for diagrams, Chart.js for charts/graphs, KaTeX for math).
  Trigger this skill whenever the user requests a document meant to be read and shared: design docs, architecture documents, technical specs, RFCs, implementation plans; data analysis reports (EDA, A/B test results, model performance evaluations, marketing analytics, data pipeline reports); business reports (OKR reviews, HR reports, competitive analyses, feasibility studies, quarterly reports); UX research reports, technical proposals, or any write-up that would benefit from charts, diagrams, code highlighting, tables, or callout boxes.
  Do NOT trigger for: writing code files, answering questions in chat, modifying existing code, short texts like emails or Slack messages, or README files that must stay Markdown.
  Prefer HTML over .md for all qualifying documents, even when the user does not say "HTML" explicitly.
---

# Visual Docs

Design, spec, and implementation documents are usually written as Markdown, but Markdown renders inconsistently and cannot embed diagrams, charts, or formulas without external tooling. The result is hard to read. This skill produces a **single self-contained HTML file** that opens in any browser, looks polished, and includes diagrams/charts/code/math directly — so a reader gets the full picture without rendering steps.

## When to use this

Use this whenever you are asked to produce a substantive technical document: design docs, specs, architecture write-ups, RFCs, implementation plans, technical reports, analyses, proposals. If the user explicitly wants a `.md` file, follow their instruction — but for these document types, default to HTML.

Do **not** use it for short answers in chat, code comments, README files that must stay Markdown by convention, or files where another format is required.

## Core rules

1. **Output a single `.html` file.** Everything (styles, content) lives in one file. No separate CSS/JS files. The only external dependencies are CDN links and Google Fonts, so the file works as long as there is internet access.
2. **Inline CSS in a `<style>` block in `<head>`.** Do not use external stylesheets of your own.
3. **Google Fonts** for body text — pick a clean, readable sans-serif appropriate for the document's language and tone (e.g. Inter, Noto Sans, Roboto).
4. **Load CDN libraries conditionally.** Include a library *only* when the document actually contains that element. A doc with no math must not load KaTeX; a doc with no charts must not load Chart.js. Unused libraries slow the page and add noise. The mapping:
   - Code blocks present → **highlight.js**
   - Diagrams present (flowchart, sequence, ER, state, gantt, etc.) → **Mermaid.js**
   - Charts/graphs present (bar, line, pie, etc.) → **Chart.js**
   - Math formulas present → **KaTeX**

## Workflow

1. Plan the document: outline the sections and decide which visual elements each section needs (code? diagram? chart? math? table? callout?).
2. Write the HTML from scratch with inline CSS. Include only the CDN libraries whose elements actually appear in the document.
3. Write a metadata header (title, author, date, version, status) at the top so the document reads like a real spec.
4. For longer documents (more than ~4 sections), add a sticky table-of-contents sidebar so readers can navigate.
5. Save as a descriptive `*.html` filename and tell the user the path.

## Choosing the right visual

Match the element to the intent instead of decorating for its own sake:

- **Architecture / flow / relationships / states / sequences** → Mermaid diagram. Mermaid covers flowchart, sequence, class, state, ER, gantt, timeline, and mindmap — use the type that fits.
- **Quantitative comparison or trends** (benchmarks, metrics over time, shares) → Chart.js.
- **Source code, config, commands** → fenced code with highlight.js.
- **Equations, complexity, formulas** → KaTeX.
- **Structured comparison of options/fields** → styled HTML table.
- **Warnings, notes, tips, important caveats** → callout boxes.
- **Headline numbers / KPIs** → stat cards.
- **Status, versions, tags** → badges.

A document with no real need for a visual element should not force one. Clear prose and a clean table often beat a gratuitous chart.

## Quality bar

The output should look like an intentional, professional engineering document: generous whitespace, a single readable content column (with the optional TOC sidebar), consistent heading hierarchy, and diagrams/charts that render on first open. Before finishing, mentally check: does every loaded CDN library correspond to content that actually uses it, and does every visual element earn its place?
