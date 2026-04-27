# Contributing to Auburn Skills

Thanks for your interest in contributing. This repository exists to make Claude more useful for **everyone at Auburn**, so please keep that bar in mind: the skills we accept here should benefit the broader Auburn community, not solve a one-off personal problem.

If you have an idea that's narrow to your own workflow, that's fine — keep it as a personal skill in your own Claude install. This repo is reserved for skills that other Auburn faculty, instructional designers, or staff would realistically reuse.

## What Makes a Good Auburn Skill

A skill is a good fit for this repo if it meets most of these:

- **Broadly useful at Auburn.** Multiple departments, programs, or teams could plausibly use it.
- **Reflects an official standard.** Auburn brand guidelines, accessibility policy (ADA, WCAG), academic formatting, or another university-wide convention.
- **Reduces repeated effort.** Replaces a manual process people are doing today (formatting documents, building decks, generating compliant transcripts, etc.).
- **Self-contained.** Bundles its own template, assets, and instructions so it works without external setup.
- **Documented.** A clear `SKILL.md` with description, triggers, inputs, workflow, and examples.

A skill is **not** a good fit if it:

- Encodes a single person's preferences or a single course's quirks.
- Depends on private credentials, internal-only URLs, or files not included in the skill.
- Duplicates an existing skill in this repo without a meaningful improvement.
- Includes copyrighted material we don't have permission to redistribute.

## How to Contribute

### 1. Open an issue first

Before building a new skill, open an issue describing:

- The problem the skill solves
- Who at Auburn would use it
- What inputs and outputs it produces
- Any official standard or template it relies on

This lets maintainers and the community weigh in early so you don't spend time on something that won't be merged.

### 2. Build the skill

Each skill lives in its own folder and is distributed as a `.skill` archive. The minimum structure:

```
your-skill-name/
├── SKILL.md             # Required: describes what the skill does
├── assets/              # Templates, images, fonts (optional)
├── references/          # Reference docs the skill loads (optional)
└── scripts/             # Helper scripts (optional)
```

Your `SKILL.md` must include YAML frontmatter:

```yaml
---
name: your-skill-name
description: "One paragraph describing what the skill does, when to use it, and what triggers it. Be explicit about trigger phrases so Claude picks the skill up reliably."
license: Proprietary - Auburn University
---
```

Naming conventions:

- Use lowercase, hyphen-separated names: `auburn-docx`, `ada-transcript-docx`.
- Prefix Auburn-branded skills with `auburn-` when the brand is the defining feature.
- Prefix accessibility skills with `ada-` when they enforce ADA rules.

### 3. Test the skill

Before submitting, verify:

- The skill triggers reliably on the phrases listed in its description.
- The output matches the official standard it claims to follow (run a sample through and compare against the source template or rules).
- All assets the skill references are bundled inside the `.skill` archive.
- The skill works from a clean Claude install with no external setup.

### 4. Open a pull request

- Fork the repo or create a branch.
- Add the `.skill` archive at the repo root and update `README.md` with a short entry under "Available Skills".
- Open a PR linking to the issue from step 1.
- Include in the PR description: a one-paragraph summary, sample inputs and outputs, and any standards or templates the skill is based on.

## Review Process

Pull requests are reviewed by repo maintainers. Reviews focus on:

1. **Fit.** Does this benefit Auburn broadly?
2. **Correctness.** Does the output match Auburn standards (brand, ADA, etc.)?
3. **Quality.** Is `SKILL.md` clear, are triggers well-chosen, are assets complete?
4. **Licensing.** Do we have the right to redistribute every asset included?

Expect feedback and iteration. Skills that affect official branding or accessibility policy may also be routed to the relevant Auburn office (Communications and Marketing, Accessibility Services, etc.) for sign-off before merging.

## Updating an Existing Skill

When updating a skill:

- Bump anything version-tracked inside `SKILL.md` if the change is user-visible.
- Note the change in your PR description (what changed and why).
- If you're changing branding, accessibility behavior, or default outputs, call that out explicitly so reviewers can confirm the new behavior matches official standards.

## Reporting Issues

If a skill produces incorrect output, breaks an official standard, or fails to trigger as documented, open an issue with:

- The skill name
- The prompt or input that caused the problem
- The actual output and the expected output
- Your Claude environment (Claude Code, Claude.ai, API)

## Questions

If you're unsure whether your idea is a good fit, open an issue and ask before building. We'd rather have that conversation early.
