# Auburn Skills

A shared collection of [Claude Skills](https://www.anthropic.com/news/skills) for Auburn University Online. These skills extend Claude with Auburn-specific knowledge, brand standards, and document templates so that anyone using Claude across the university can produce on-brand, accessible, and consistent work without re-inventing the formatting every time.

This repository is intended as a **community resource** for Auburn faculty, instructional designers, and staff. Skills here should be useful to the broader Auburn community — not personal one-offs.

## What is a Claude Skill?

A Claude Skill is a packaged folder (`SKILL.md` plus any supporting assets, scripts, or references) that Claude loads on demand to perform a specific task with a known set of standards. Skills in this repo are distributed as `.skill` files (zip archives) that can be installed in Claude or used directly with the Claude API.

## Available Skills

### `auburn-docx`
Creates branded Auburn University Word documents with the official letterhead, War Eagle footer, Auburn Navy / Auburn Orange color palette, and Avenir Next LT Pro typography. Use it for reports, memos, proposals, letters, and any professional documentation that should follow Auburn's brand guidelines.

### `auburn-pptx`
Generates Auburn University PowerPoint presentations using the official "NEW AUBURN" theme with 36 pre-built slide layouts. Supports title slides, content layouts, quotes, stats, charts, tables, timelines, and closing slides — all in the official Auburn palette and typography.

### `ada-transcript-docx`
An all-in-one skill that converts a raw video transcript into an ADA 2025-compliant Word document using the Auburn Online / ADMH branded template. Applies all 10 ADA formatting rules (speaker labels, sound cues, audio descriptions, non-English language tagging, etc.) and outputs a finished, accessible `.docx`.

### `auburn-syllabus`
Creates, generates, or reviews Auburn University course syllabi for compliance with Auburn's official requirements — Provost guidance, Biggio Center template, ADA, SB 129 / Alabama Act 2024-34, Title IX, and the Auburn Classroom Behavior Policy. Three modes: build a new syllabus from scratch, generate one from pasted course details, or review an existing syllabus and produce a compliance report. All boilerplate ships verbatim from Auburn-approved sources. Outputs markdown by default; can hand off to `auburn-docx` for a branded Word version.

## Installation

Each skill is distributed as a `.skill` file. To use a skill:

1. Download the relevant `.skill` file from this repository.
2. Install it in your Claude environment (Claude Code, Claude.ai, or the API) following the [Claude Skills documentation](https://docs.claude.com/en/docs/claude-code/skills).
3. Trigger the skill by referencing it in your prompt (for example: "Create an Auburn-branded report on …").

The `SKILL.md` inside each archive describes the exact triggers, inputs, and workflow.

## Repository Structure

```
.
├── auburn-docx.skill            # Auburn Word document template
├── auburn-pptx.skill            # Auburn PowerPoint template
├── ada-transcript-docx.skill    # ADA 2025 transcript generator
├── auburn-syllabus.skill        # Auburn syllabus create / generate / review
├── auburn-syllabus/             # Source for auburn-syllabus.skill
├── CONTRIBUTING.md              # How to contribute a new skill
└── README.md
```

## Contributing

We welcome contributions from anyone at Auburn. Skills here should be **reusable across teams** and reflect official Auburn standards (branding, accessibility, academic policy, etc.). See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines, the skill template, and the review process.

## License

Materials, logos, fonts, and templates are property of Auburn University and are provided for use within Auburn University Online. Do not redistribute Auburn brand assets outside the university without permission from the Office of Communications and Marketing.

## Maintainers

Maintained by Auburn University Online.

- Mazin Salim — [mzm0397@auburn.edu](mailto:mzm0397@auburn.edu)

For questions, open an issue in this repository.
