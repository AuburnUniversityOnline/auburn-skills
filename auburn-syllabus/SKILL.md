---
name: auburn-syllabus
description: "Create, generate, or review Auburn University course syllabi that comply with Auburn's official requirements (Provost guidance, Biggio Center template, ADA, SB 129 / Act 2024-34, Title IX, Classroom Behavior Policy). All boilerplate is verbatim Auburn-approved text. Triggers: 'Auburn syllabus', 'create a syllabus', 'review my syllabus', 'is my syllabus SB129 compliant', 'syllabus template', 'syllabus boilerplate', 'Auburn Online syllabus', or when a user uploads a file with 'syllabus' in the name and asks for a check. Does NOT trigger on 'course outline', 'lesson plan', 'lecture notes', 'rubric', or general course design."
license: Proprietary - Auburn University Biggio Center
---

# Auburn University Syllabus Skill

Create, generate, or review Auburn University course syllabi. All Auburn-required boilerplate is bundled verbatim in `references/`. Do NOT paraphrase legal/policy language — copy it verbatim from the reference files.

## When to Use This Skill

Use when the faculty member asks for any of:
- A new syllabus from scratch
- A syllabus generated from course details they paste
- A compliance review of an existing syllabus
- The Auburn SB 129 / Divisive Concepts boilerplate
- The Auburn AI policy options
- Any Auburn-specific syllabus boilerplate (ADA, Title IX, classroom behavior, withdrawal, mental health)

## When NOT to Use This Skill

Do NOT use for:
- Course outlines, lesson plans, lecture notes, rubrics, assignment design — these are separate tasks.
- General writing help unrelated to syllabi.
- Course advising or registration questions.

## Mode Detection

Read the user's first message and pick one mode:

| Cue | Mode |
|---|---|
| User uploaded a file or pasted an existing syllabus and asks for a check / review / compliance audit | **Review** |
| User pasted a course brief, course description, learning outcomes, or other course details upfront | **Generate** |
| User asks for a new syllabus with no details, or just says "make me a syllabus" | **Create** |

If ambiguous, ask one clarifying question: "Are you creating a new syllabus, or reviewing an existing one?"

---

## Required Reference Files

Always have these files available. Load them on demand based on what the syllabus needs.

- `references/biggio-syllabus-guidance.md` — canonical Auburn syllabus structure
- `references/required-sections.md` — ordered section list and headings
- `references/sb129-boilerplate.md` — Full + Concise SB 129 statements (verbatim)
- `references/ai-policy-options.md` — 4 Auburn AI policies (verbatim)
- `references/classroom-behavior.md` — Auburn Classroom Behavior Policy
- `references/ada-accommodations.md` — ADA / Office of Accessibility statement
- `references/academic-honesty.md` — Title XII / Student Policy eHandbook
- `references/withdrawal-deadlines.md` — 15th-class-day + $100 fee
- `references/excused-absences.md` — Auburn excused absences (verbatim)
- `references/makeup-policy.md` — within-2-weeks rule (verbatim)
- `references/mental-health-titleix.md` — Auburn Cares, SCPS, Title IX, Safe Harbor
- `references/emergency-contingency.md` — emergency contingency (verbatim)
- `references/early-alert-grade.md` — Core Curriculum Early Alert (verbatim)
- `references/core-curriculum-requirements.md` — Core SLOs + rubrics
- `references/graduate-course-requirements.md` — Justification for Graduate Credit
- `references/slo-writing-guide.md` — strong-verb SLOs, examples
- `references/sb129-act-text.md` — operative summary of SB 129
- `references/compliance-checklist.md` — review-mode rubric

## Asset Templates

- `assets/syllabus-template-online.md` — for online (asynchronous) courses
- `assets/syllabus-template-inperson.md` — for in-person courses

For hybrid courses, start from the online template and ask the faculty which sections need in-person adjustments.

---

## Workflow: Create Mode

When user provides no details:

### Step 1 — Modality

Ask: "Is this an **online** course, an **in-person** course, or **hybrid**?"

### Step 2 — Required Intake (one batch)

Ask:
> Please provide:
> 1. Course number and title (e.g. ENGL 1100: Composition I)
> 2. Credit hours
> 3. Term (e.g. Fall 2026)
> 4. Your name and Auburn email
> 5. Any prerequisites (or "none")
> 6. Is this a Core Curriculum course? (yes/no)
> 7. Is this a graduate course at the 6000-level or above? (yes/no)

### Step 3 — AI Policy Choice

Read `references/ai-policy-options.md` and present all 4 options + custom. Ask the faculty which they prefer. Use the chosen option **verbatim**.

### Step 4 — SB 129 Statement Choice

Read `references/sb129-boilerplate.md` and present both options. Ask the faculty: "Full version or Concise version?" Use the chosen statement **verbatim**.

### Step 5 — Course Description and SLOs

Ask the faculty for:
- A 1-paragraph course description.
- 4–8 measurable Student Learning Outcomes.

If they don't have SLOs ready, offer to draft them based on the course title and description. Use `slo-writing-guide.md` to draft strong-verb SLOs. Always confirm with the faculty before finalizing.

Then ask one optional question: "Would you like a separate **Course Objectives** section (instructor-perspective, in addition to the SLOs)? Auburn lists this as optional but recommended." If yes, ask for 3–5 Objectives using broad verbs (study, know, appreciate, etc. — see `slo-writing-guide.md`) and populate `{{OBJECTIVES_BULLET_LIST}}` in the template. If no, leave the entire `{{IF_HAS_OBJECTIVES: ... }}` block out of the rendered output.

### Step 6 — Schedule Topics

Ask: "Paste your weekly topics in any format — bullets, paragraph, last semester's outline, etc. I'll organize them into a 15-week table."

Organize the input into 15 weeks. Insert standard markers: midterm exam slot (around week 8), final exam slot (university-set, last week or after).

### Step 7 — Conditional Sections

- If Core: ask which Core SLOs the course satisfies (consult `core-curriculum-requirements.md`).
- If Graduate (6000-level+): ask for the Justification for Graduate Credit paragraph.
- For online: ask for virtual office hours technology (Zoom, Teams, etc.).

### Step 8 — Assemble

Load the appropriate template (`assets/syllabus-template-online.md` or `-inperson.md`).

Replace `{{PLACEHOLDERS}}` with the faculty's inputs.

For each `{{INSERT references/...}}` directive: read the referenced file and copy the verbatim statement into the output. Do NOT paraphrase.

For `{{AI_POLICY_BLOCK}}` and `{{SB129_STATEMENT_BLOCK}}`: insert the chosen verbatim statement.

Resolve conditional blocks: `{{IF_CORE_COURSE: ...}}`, `{{IF_GRADUATE_COURSE: ...}}` — include the contents only if the condition matches.

### Step 9 — Output

Render the complete syllabus as markdown in the chat.

End with: *"Want this as a branded Auburn .docx? I can hand it off to the auburn-docx skill. Or paste this into your Canvas syllabus tab as-is."*

---

## Workflow: Generate Mode

User pasted a course brief or details upfront.

### Step 1 — Extract

Parse the user's paste for:
- Course number, title, credits, term
- Modality (online/in-person/hybrid)
- Instructor name, email
- Course description
- SLOs / outcomes / objectives
- Prerequisites
- Schedule / topic list
- Textbooks
- Existing AI policy or SB 129 statement (rare, but possible)

### Step 2 — Confirm + Ask for Missing

Show the faculty what was extracted. Ask only for the truly missing critical fields (modality, term if missing, AI policy choice, SB 129 choice, Core/Grad status).

### Step 3 — Continue from Create Mode Step 3

Same flow as Create from this point on.

---

## Workflow: Review Mode

User uploaded or pasted an existing syllabus.

### Step 1 — Acknowledge and Identify

Confirm what file/text you received. Identify obvious metadata (course number, instructor name, term).

### Step 2 — Ask Three Questions

Before scoring:
- "Is this a Core Curriculum course?" (affects items 18–19 of the checklist)
- "Is this a graduate course at the 6000-level or above?" (affects item 20)
- "Is this primarily online, in-person, or hybrid?" (affects item 21)

### Step 3 — Score

Read `references/compliance-checklist.md`. For each item:
- Find the relevant section in the syllabus.
- Compare against the verbatim Auburn text in the corresponding `references/` file.
- Score ✅ Present / ⚠️ Partial / ❌ Missing.

### Step 4 — Produce Report

Output format:

```
# Compliance Review — [Course Number]

## Hard-Required Items

| # | Item | Status | Found | Recommendation |
|---|------|--------|-------|----------------|
| 1 | Course number, title, credits, term | ✅ | "ENGL 1100, Composition I, 3 credits, Fall 2026" | — |
| 2 | Instructor + Auburn email | ⚠️ | Email is gmail.com, not auburn.edu | Use your @auburn.edu email |
| 14 | SB 129 / Divisive Concepts | ❌ | Not found | Add the Provost-approved Full or Concise statement |
[...]

## Conditionally Required

[only if Core/Grad/Online]

## Soft / Recommended

[warnings]

## Anti-Patterns Detected

[if any]

---

**Summary: 14/17 hard-required, 0 anti-patterns. 3 critical issues, 5 warnings.**

Want me to generate a corrected version that fills these gaps while keeping your existing content?
```

### Step 5 — On Request, Run Generate Mode

If the faculty says yes, run Generate Mode using their existing syllabus content as source-of-truth wherever it's compliant. Only fill or correct the flagged items. Preserve their voice for course description and SLOs.

End with: *"Want this corrected version as a branded Auburn .docx?"*

---

## Output Rules (All Modes)

1. **Default output: rendered markdown in the chat.** Do not write files unless the faculty asks for a download.
2. **Branded .docx on request.** When the faculty asks for a Word version, hand off to the `auburn-docx` skill with the full syllabus markdown, document title `{{Course Number}} {{Course Title}} — Syllabus`, and instructor name as author.
3. **No PDF, no HTML, no Canvas API.** Markdown + .docx only in v1.
4. **Always end with a "what to do next" prompt.** Faculty are busy; close the loop.

## Verbatim Discipline

The skill's correctness depends on Auburn-approved text appearing verbatim in syllabi. Hard rules:

- ❌ Never paraphrase the SB 129 statement, AI policy options, ADA statement, Title IX statement, or any other Auburn-required boilerplate.
- ❌ Never combine or modify the two SB 129 versions.
- ❌ Never invent new boilerplate.
- ✅ Always copy the relevant `references/*` file content into the output as-is.
- ✅ If a reference file is missing or empty, stop and ask the user.

If the faculty asks to modify Auburn boilerplate, push back politely: "This statement is pre-approved by [Provost / Biggio Center]. Modifying it could affect compliance. I can include it as-is, or you can write your own and label it as your own — which would you like?"

## Failure Modes

- **`auburn-docx` not installed.** Output markdown only and explain how to install from `AuburnUniversityOnline/auburn-skills`.
- **Reference file missing.** Stop and ask the user to install the latest version of the skill.
- **Faculty's syllabus is in a non-text format we can't read.** Ask them to paste the text or convert to markdown.
- **Conflicting Auburn requirements.** Default to the Biggio Center text; note the conflict to the user.
