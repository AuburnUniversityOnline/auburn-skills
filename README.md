# Auburn Skills

A shared collection of **AI skill bundles** for Auburn University Online — reusable instruction packs that give any AI assistant (Claude, ChatGPT, Codex, etc.) Auburn-specific knowledge, brand standards, and document templates so that anyone at Auburn can produce on-brand, accessible, and consistent work without re-inventing the formatting every time.

This repository is intended as a **community resource** for Auburn faculty, instructional designers, and staff. Skills here should be useful to the broader Auburn community — not personal one-offs.

## What is a "skill"?

A skill is a packaged bundle (a `SKILL.md` instruction file plus any supporting reference text, templates, or assets, all zipped into a `.skill` archive) that an AI assistant loads on demand to perform a specific task with a known set of standards. Think of it as a portable, version-controlled "expert in a folder" — instead of writing a long prompt every time, you install the skill once and the AI knows how to do the job correctly.

The format originated with Anthropic's [Claude Skills](https://www.anthropic.com/news/skills), but the content inside (markdown instructions and references) is plain text — it works in any AI tool that accepts files or system prompts. See [Using these skills](#using-these-skills) below for platform-specific instructions.

## Available Skills

### `auburn-docx`
Creates branded Auburn University Word documents with the official letterhead, War Eagle footer, Auburn Navy / Auburn Orange color palette, and Avenir Next LT Pro typography. Use it for reports, memos, proposals, letters, and any professional documentation that should follow Auburn's brand guidelines.

### `auburn-pptx`
Generates Auburn University PowerPoint presentations using the official "NEW AUBURN" theme with 36 pre-built slide layouts. Supports title slides, content layouts, quotes, stats, charts, tables, timelines, and closing slides — all in the official Auburn palette and typography.

### `ada-transcript-docx`
An all-in-one skill that converts a raw video transcript into an ADA 2025-compliant Word document using the Auburn Online / ADMH branded template. Applies all 10 ADA formatting rules (speaker labels, sound cues, audio descriptions, non-English language tagging, etc.) and outputs a finished, accessible `.docx`.

### `auburn-syllabus`
Creates, generates, or reviews Auburn University course syllabi for compliance with Auburn's official requirements — Provost guidance, Biggio Center template, ADA, SB 129 / Alabama Act 2024-34, Title IX, and the Auburn Classroom Behavior Policy. Three modes: build a new syllabus from scratch, generate one from pasted course details, or review an existing syllabus and produce a compliance report. All boilerplate ships verbatim from Auburn-approved sources. Outputs markdown by default; can hand off to `auburn-docx` for a branded Word version.

## Using these skills

Each skill is distributed as a `.skill` file (a zip archive containing `SKILL.md` plus reference and asset files). The same archive works across multiple AI platforms — pick the one you use.

### Claude.ai (web / desktop) — native support

1. Download the relevant `.skill` file from this repository.
2. In Claude.ai, go to **Settings → Capabilities → Skills** (or the Skills section of your workspace), upload the `.skill` file, and enable it.
3. Trigger it in any conversation by stating the task — e.g. "Create an Auburn-branded report on …" or "Review my syllabus for SB 129 compliance."

### Claude Code (CLI) — native support

```bash
# Per-user (available in all your projects):
mkdir -p ~/.claude/skills && cp <skill>.skill ~/.claude/skills/
unzip -o ~/.claude/skills/<skill>.skill -d ~/.claude/skills/<skill-name>/

# Or per-project (only in this repo): drop the unpacked skill folder into .claude/skills/
```

Claude Code auto-loads the `SKILL.md` and triggers it on matching phrases.

### ChatGPT (web) — manual load

ChatGPT doesn't have a `.skill` installer, but the bundle is just markdown. Two options:

- **Projects (recommended):** create a Project, unzip the `.skill`, and upload `SKILL.md` plus everything in `references/` and `assets/` as project files. Add a one-line custom instruction: *"When the user asks for [skill purpose], follow SKILL.md."*
- **Per-conversation:** unzip the `.skill`, paste the contents of `SKILL.md` into the chat as your first message ("Use the workflow below…"), and attach the reference files when needed.

### Codex (OpenAI CLI) and other CLI tools

Most CLI assistants accept either a system prompt file or a project-level instruction file. Unzip the `.skill` archive into your working directory and:

- **Codex / `gpt` CLI:** point the assistant at `SKILL.md` as a system prompt or project context file.
- **Cursor / Windsurf / similar IDE assistants:** drop the unpacked folder into the project; reference `SKILL.md` in `.cursor/rules` or the equivalent project-rules file.
- **Generic LLM API:** use `SKILL.md` as the system prompt and `references/*.md` as retrieved context when the relevant section is needed.

### What's inside a `.skill`

```
<skill-name>/
├── SKILL.md          # the instruction file — triggers, workflow, rules
├── references/       # verbatim source-of-truth files the AI consults on demand
└── assets/           # templates, logos, source documents the skill produces from
```

`SKILL.md` is the entry point. It tells the AI when to fire, what to ask the user, what reference files to load, and what to output. Read it to understand exactly what the skill does.

## Repository Structure

```
.
├── auburn-docx.skill            # Auburn Word document template
├── auburn-pptx.skill            # Auburn PowerPoint template
├── ada-transcript-docx.skill    # ADA 2025 transcript generator
├── auburn-syllabus.skill        # Auburn syllabus create / generate / review
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
