# `auburn-syllabus` Skill — Design Document

**Date:** 2026-04-27
**Status:** Design validated, ready for implementation planning
**Owner:** Mazin Salim (mzm0397@auburn.edu)
**Repo:** AuburnUniversityOnline/auburn-skills

## Purpose

A Claude Skill that helps Auburn University faculty **create, generate, and review** course syllabi that comply with Auburn's official requirements (Provost guidance, Biggio Center template, ADA, SB 129 / Alabama Act 2024-34, Title IX, Classroom Behavior Policy). Distributed as a `.skill` archive in the `auburn-skills` repo, runs in Claude.ai's skills sandbox.

## Non-Goals (v1)

- Auburn academic calendar lookup (faculty paste their term's dates)
- Auto-detection of Core Curriculum from course number (faculty declare it)
- PDF output (markdown + .docx is sufficient)
- Canvas API push (out of scope)
- Course design beyond the syllabus (rubrics, assignments, lectures are separate skills)

## Source Material

The skill is grounded in the following Auburn sources:

1. **Auburn Provost — Supplemental Instruction Guidance for Act 2024-34** (SB 129) — provides two pre-approved Divisive Concepts statements (Full + Concise).
2. **Auburn Biggio Center — Syllabus Guidance** — full syllabus structure, section-by-section requirements, four AI policy options, mental health/Title IX/basic needs verbatim language.
3. **Alabama SB 129 / Act 2024-34** (effective Oct 1, 2024) — defines "Divisive Concepts" and prohibits compelled assent; bans diversity statements (with narrow accreditation exception).
4. **Auburn Policy on Classroom Behavior** (effective 5/28/2013) — 9-item list of improper behaviors faculty may reference.

## Three Modes

### Create
No syllabus provided. Skill walks the faculty through:
1. **Required intake batch** (one message): course number + title, modality (online/in-person/hybrid), credit hours, instructor name + Auburn email, term.
2. **AI policy choice** — 4 Auburn options + custom (always asked).
3. **SB 129 statement choice** — Full or Concise (always asked).
4. **Course description + 4–8 measurable SLOs** — faculty paste; if blank, skill drafts and asks for confirmation.
5. **Schedule topics** in any format — skill organizes into 15-week table.
6. **Output:** complete markdown syllabus, with offer to generate branded `.docx` via `auburn-docx`.

### Generate
Faculty pastes a course brief upfront. Skill extracts what it can and asks targeted follow-ups only for missing fields. AI policy + SB 129 choice always asked. Output identical to create mode.

### Review
Faculty uploads or pastes an existing syllabus.
1. Skill produces a **compliance report** (table with ✅ / ⚠️ / ❌ per requirement, citing exact text found or noting absence).
2. Skill ends with: *"Want me to generate a corrected version that fills these gaps while keeping your existing content?"*
3. If yes, skill runs generate-mode logic using the existing syllabus as source-of-truth where compliant, only filling/correcting flagged items.

All three modes end with: *"Want this as a branded Auburn `.docx`?"*

## Design Principles

1. **Verbatim Auburn text only.** All boilerplate (SB 129 statements, AI policies, ADA, Title IX, mental health, classroom behavior, withdrawal language) ships in `references/` as exact verbatim Auburn-approved text. Claude never paraphrases legal/policy language.
2. **Sharp triggers.** Skill activates only on syllabus-specific intent. Does not fire on "course outline", "rubric", "lecture notes", "course design".
3. **Hybrid intake.** Faculty can paste a full course brief and get a draft instantly, or type "I need a syllabus for ENGL 1100" and be walked through the missing fields.
4. **Two-tier review.** Diagnose first, fix on request — faculty trust improves when they see what was wrong before accepting changes.
5. **Always ask, never assume** for AI policy and SB 129 boilerplate — these are personal pedagogical/legal choices, not defaults.
6. **Both modalities** — online and in-person, asked at start.

## Skill Folder Structure

```
auburn-syllabus/
├── SKILL.md                              # triggers, workflow, mode logic
├── references/
│   ├── biggio-syllabus-guidance.md       # full Biggio Center guidance, structured
│   ├── required-sections.md              # ordered list of required sections + headings
│   ├── sb129-boilerplate.md              # Full + Concise statements, verbatim from Provost
│   ├── ai-policy-options.md              # 4 Auburn AI policies, verbatim from Canvas template
│   ├── classroom-behavior.md             # 9-item Auburn Classroom Behavior Policy, verbatim
│   ├── ada-accommodations.md             # ADA / Office of Accessibility statement, verbatim
│   ├── academic-honesty.md               # Title XII / Student Policy eHandbook reference
│   ├── withdrawal-deadlines.md           # 15th-class-day rule + $100 fee 6th–15th day
│   ├── excused-absences.md               # full Auburn excused-absence list, verbatim
│   ├── makeup-policy.md                  # within-2-weeks rule, verbatim
│   ├── mental-health-titleix.md          # Auburn Cares, SCPS, Safe Harbor, Title IX
│   ├── emergency-contingency.md          # Auburn emergency-contingency statement
│   ├── early-alert-grade.md              # Core Curriculum Early Alert Grade language
│   ├── core-curriculum-requirements.md   # 11 Core SLOs + measures + rubric requirement
│   ├── graduate-course-requirements.md   # "Justification for Graduate Credit" addendum
│   ├── slo-writing-guide.md              # weak/strong SLO examples, action verbs
│   ├── compliance-checklist.md           # master review-mode rubric
│   └── sb129-act-text.md                 # SB 129 full text (context only, not for output)
└── assets/
    ├── syllabus-template-online.md       # online template with placeholders + boilerplate baked in
    └── syllabus-template-inperson.md     # in-person template with placeholders + boilerplate baked in
```

## Compliance Checklist (review-mode rubric)

### Hard-required (Auburn or law)
1. Course number, title, credit hours, term
2. Instructor name + Auburn email
3. Course description
4. ≥1 measurable Student Learning Outcome (warn if <4 or >8)
5. Grading scale + grade determination method
6. Withdrawal language (15th-class-day rule + 6th–15th day $100 fee)
7. Excused absences statement (Auburn's list)
8. Make-up policy (within-2-weeks)
9. ADA statement (AIM portal OR `ACCESSIBILITY@auburn.edu` OR (334) 844-2096)
10. Academic Honesty (Student Policy eHandbook / Title XII)
11. Classroom Behavior reference
12. Emergency Contingency statement
13. AI Policy (one of 4 Auburn options OR custom)
14. SB 129 / Divisive Concepts statement (Full, Concise, or substantively equivalent)
15. Mental Health resources (Auburn Cares / SCPS)
16. Title IX / Sexual Misconduct resources
17. Tentative 15-week schedule + final exam slot

### Conditionally required
18. Core Curriculum SLOs + measures (only if Core)
19. Early Alert Grade statement (only if Core)
20. Justification for Graduate Credit (only if 6000-level or above)

### Soft / recommended (warn, don't fail)
21. Virtual office hours + technology (online courses)
22. Response-time statement for emails
23. Prerequisites listed explicitly
24. Textbook edition specificity
25. Basic Needs statement
26. Canvas notification reminder

### Anti-patterns the skill flags
- Diversity statement requiring student assent → ❌ (SB 129 violation)
- Vague SLOs ("gain", "understand", "appreciate") → ⚠️
- Final exam on last day of semester or Study Days → ⚠️
- Major papers due in last three class days → ⚠️
- AI policy missing entirely → ⚠️ (post-2024 Auburn baseline)

## Output Contract

### Default: rendered markdown in chat
Faculty can read in chat, copy into Canvas, save locally, or request `.docx`.

### On request: branded `.docx` via `auburn-docx`
Skill hands the full markdown to `auburn-docx` with:
- Document title: `{{Course Number}} {{Course Title}} — Syllabus`
- Document author: instructor name
- Heading hints: `#` → Title, `##` → Heading 1, `###` → Heading 2

If `auburn-docx` is not installed, the skill produces markdown only and explains how to install it from `AuburnUniversityOnline/auburn-skills`.

### Closing prompt
Every successful run ends with a one-line "what to do next": *"Paste this into your Canvas syllabus tab, or ask me for a branded .docx version."*

## Build Order (for implementation)

1. **Create + Generate modes** (most value, simplest UX)
2. **Reference and asset files** (verbatim Auburn text)
3. **`auburn-docx` handoff**
4. **Review mode** (most complex UX — ship after the simpler modes are stable)
5. **Polish: anti-pattern detection, soft-recommendations, closing prompts**

## Open Questions / Future Work

- Auburn academic calendar awareness (term dates, holidays, study days) — defer to v2
- Course-number → Core Curriculum auto-detection — defer to v2
- Multi-instructor / team-taught course support — defer to v2
- Lab section / recitation handling — defer to v2
- Localization (Spanish-language syllabi) — defer to v2
