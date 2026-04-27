# auburn-syllabus Skill — Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Build the `auburn-syllabus` Claude Skill end-to-end — folder structure, verbatim Auburn reference files, syllabus template assets, `SKILL.md` orchestration, packaged `.skill` archive, and integrate it into the `auburn-skills` repo.

**Architecture:** This is a content-driven Claude Skill, not a code project. The "code" is markdown files Claude loads on demand. The skill's correctness depends on (1) verbatim accuracy of Auburn-approved text, (2) sharp trigger phrases in `SKILL.md`, and (3) clean placeholder substitution in templates. There is no test framework — validation is content-equality checks against authoritative sources.

**Tech Stack:** Markdown, YAML frontmatter, zip (for `.skill` archive packaging), git.

**Working directory:** `/Users/mazin/Documents/UNI/AU ONLINE/CODING/SKILLS/`

**Source-of-truth references (all already gathered in design doc and earlier conversation):**
- Auburn Biggio Center syllabus guidance (full text in conversation history paste from 2026-04-27)
- Auburn Provost SB 129 / Act 2024-34 supplemental guidance
- Alabama SB 129 enrolled bill (`additonal_resources/SB129-enr.pdf`)
- Auburn Policy on Classroom Behavior (`additonal_resources/Policy on Classroom Behavior...pdf`)

---

## Task 1: Create the skill folder structure

**Files:**
- Create directory: `auburn-syllabus/`
- Create directory: `auburn-syllabus/references/`
- Create directory: `auburn-syllabus/assets/`

**Step 1: Create the directories**

Run:
```bash
cd "/Users/mazin/Documents/UNI/AU ONLINE/CODING/SKILLS"
mkdir -p auburn-syllabus/references auburn-syllabus/assets
ls -la auburn-syllabus/
```

Expected output: shows `references/` and `assets/` subdirectories.

**Step 2: Commit (empty dirs need a .gitkeep)**

```bash
touch auburn-syllabus/references/.gitkeep auburn-syllabus/assets/.gitkeep
git add auburn-syllabus/
git commit -m "Scaffold auburn-syllabus folder structure"
```

---

## Task 2: Write `references/sb129-boilerplate.md`

**Files:**
- Create: `auburn-syllabus/references/sb129-boilerplate.md`

**Source:** Auburn Provost Supplemental Instruction Guidance — both versions are pre-approved verbatim by the Provost's office. Do NOT paraphrase.

**Step 1: Write the file with both verbatim statements**

Content:
```markdown
# SB 129 / Act 2024-34 — Divisive Concepts Statement (Verbatim)

These two statements are pre-approved by the Auburn University Provost's Office. Use one of them verbatim. Do not paraphrase.

## Option A — Full Version

> Faculty at Auburn University have the academic freedom to explore, discuss, and teach a wide range of topics in an academic setting. This course may engage with challenging or controversial material, but will do so through an objective, scholarly approach designed to promote critical thinking and independent analysis. Students are encouraged to reflect thoughtfully and respectfully on all material. No student will be required to agree with, endorse, or adopt any concept identified under Alabama law as a Divisive Concept, nor will any student be penalized for choosing not to support or endorse such a concept.

## Option B — Concise Version

> This class may address topics that require careful analysis and reflection. Students are not required to agree with any specific viewpoint and will not be penalized for independent thinking. Instruction will be grounded in evidence and presented without endorsement of any idea defined by law as a Divisive Concept.

## Usage Rules

- Always ask the faculty member which version they prefer.
- Do not modify the text.
- Do not combine the two.
- Place the statement in the syllabus under a heading such as "Statement on Divisive Concepts" or "SB 129 / Act 2024-34 Compliance."
- A diversity statement requiring student assent is prohibited under SB 129 (with narrow accreditation exception).
```

**Step 2: Verify the file**

Run:
```bash
cat auburn-syllabus/references/sb129-boilerplate.md | wc -l
```
Expected: roughly 25 lines.

**Step 3: Commit**

```bash
git add auburn-syllabus/references/sb129-boilerplate.md
git commit -m "Add verbatim SB 129 / Act 2024-34 statements"
```

---

## Task 3: Write `references/ai-policy-options.md`

**Files:**
- Create: `auburn-syllabus/references/ai-policy-options.md`

**Source:** Auburn Biggio Center — four AI policy options, verbatim from the Biggio Center's Canvas template.

**Step 1: Write the file**

Content:
```markdown
# Generative AI Tools — Auburn Biggio Center Approved Policies (Verbatim)

The Biggio Center provides four pre-approved AI policy options. Use one verbatim, or work with the faculty member to draft a custom policy that follows Auburn's vetting requirement: "All technology must be vetted through the Auburn University vetting process prior to use. Please contact your IT professional for more guidance."

## Option 1 — Open Use (Permitted with Attribution)

**Heading: AI Policy: Permitted in this Course with Attribution**

> In this course, students are encouraged to use Generative AI Tools like ChatGPT or Copilot to support their work. To maintain academic integrity, students must disclose any AI-generated material they use and properly attribute it, including in-text citations, quotations, and references. Students should exercise caution and avoid sharing any sensitive or private information when using these tools. Examples of such information include personally identifiable information (PII), protected health information (PHI), financial data, intellectual property (IP), and any other data that might be legally protected.
>
> A student should include the following statement in assignments to indicate use of a Generative AI Tool: "The author(s) would like to acknowledge the use of [Generative AI Tool Name], a language model developed by [Generative AI Tool Provider], in the preparation of this assignment. The [Generative AI Tool Name] was used in the following way(s) in this assignment [e.g., brainstorming, grammatical correction, citation, which portion of the assignment]."

## Option 2 — Moderate Use (Permitted when Assigned with Attribution)

**Heading: AI Policy: Permitted when Assigned in this Course with Attribution**

> In this course, students are permitted to use Generative AI Tools such as ChatGPT or Copilot for specific assignments, as designated by the instructor. To maintain academic integrity, students must disclose any use of AI-generated material. As always, students must properly use attributions, including in-text citations, quotations, and references. Students should exercise caution and avoid sharing any sensitive or private information when using these tools. Examples of such information include personally identifiable information (PII), protected health information (PHI), financial data, intellectual property (IP), and any other data that might be legally protected.
>
> A student should include the following statement in assignments to indicate use of a Generative AI Tool: "The author(s) would like to acknowledge the use of [Generative AI Tool Name], a language model developed by [Generative AI Tool Provider], in the preparation of this assignment. The [Generative AI Tool Name] was used in the following way(s) in this assignment [e.g., brainstorming, grammatical correction, citation, which portion of the assignment]."

## Option 3A — Strict Prohibition

**Heading: AI Policy: Not Permitted in this Course**

> In this course, it is expected that all submitted work is produced by the students themselves, whether individually or collaboratively. Students must not seek the assistance of Generative AI Tools like ChatGPT or Copilot. Use of a Generative AI Tool to complete an assignment constitutes academic dishonesty.

## Option 3B — Strict for Assignments, OK as Study Tool

**Heading: AI Policy: Not Permitted in this Course for Assignments**

> In this course, it is expected that all submitted work is produced by the students themselves, whether individually or collaboratively. Students must not seek the assistance of Generative AI Tools like ChatGPT or Copilot for graded assignments. Use of a Generative AI Tool to complete an assignment constitutes academic dishonesty. Students may use Generative AI tools as a study tool, but be forewarned that AI tools are not trustworthy.

## Option C — Custom

If the faculty member wants a custom policy, help them draft one that:
1. Names the specific tools covered.
2. States clearly when use is and is not allowed.
3. Specifies disclosure / attribution requirements if any.
4. Includes the Auburn vetting reminder: "All technology must be vetted through the Auburn University vetting process prior to use."
5. Avoids language that compels assent to a divisive concept (SB 129 compliance).

## Usage Rules

- Always ask the faculty member to pick one of the four options or write a custom policy.
- Never default — AI policy is a personal pedagogical decision.
- Use the heading exactly as specified above for the chosen option.
- Place the AI policy in the syllabus before the SB 129 statement and after the Classroom Policies section.
```

**Step 2: Verify**

Run:
```bash
grep -c "^## Option" auburn-syllabus/references/ai-policy-options.md
```
Expected: 5 (Options 1, 2, 3A, 3B, C).

**Step 3: Commit**

```bash
git add auburn-syllabus/references/ai-policy-options.md
git commit -m "Add verbatim Biggio Center AI policy options"
```

---

## Task 4: Write `references/ada-accommodations.md`

**Files:**
- Create: `auburn-syllabus/references/ada-accommodations.md`

**Source:** Auburn Biggio Center syllabus guidance — verbatim ADA statement.

**Step 1: Write the file**

Content:
```markdown
# Americans with Disabilities Act — Auburn Verbatim Statement

Use this verbatim. Do not paraphrase.

## Heading

**Americans with Disabilities Act** (or **Accessibility Statement**)

## Statement (Verbatim)

> Students who need accommodations should submit their approved accommodations through the AIM Student Portal on AU Access and follow-up with the instructor about an appointment. It is important for the student to complete these steps as soon as possible; accommodations are not retroactive. Students who have not established accommodations through the Office of Accessibility, but need accommodations, should contact the Office of Accessibility at: ACCESSIBILITY@auburn.edu or (334) 844-2096 (V/TT). The Office of Accessibility is located in Haley Center 1228.

## Required Elements (for review-mode validation)

A compliant ADA statement must contain at least one of:
- "AIM Student Portal" reference
- `ACCESSIBILITY@auburn.edu`
- Phone `(334) 844-2096`
- "Office of Accessibility" reference
- "Haley Center 1228" reference

If none of these are present, flag as ❌ Missing.
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/ada-accommodations.md
git commit -m "Add verbatim ADA / Office of Accessibility statement"
```

---

## Task 5: Write `references/academic-honesty.md`

**Files:**
- Create: `auburn-syllabus/references/academic-honesty.md`

**Source:** Auburn Biggio Center — verbatim academic honesty statement.

**Step 1: Write the file**

Content:
```markdown
# Academic Honesty — Auburn Verbatim Statement

Use this verbatim. Do not paraphrase.

## Heading

**Academic Honesty**

## Statement (Verbatim)

> All portions of the Auburn University Student Academic Honesty code (Title XII) found in the Student Policy eHandbook will apply to this class. All academic honesty violations or alleged violations of the SGA Code of Laws will be reported to the Office of the Provost, which will then refer the case to the Academic Honesty Committee.

## Required Elements (for review-mode validation)

A compliant academic honesty statement must reference:
- "Student Policy eHandbook" OR
- "Title XII" OR
- "Auburn University Student Academic Honesty code"

If none are present, flag as ❌ Missing.
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/academic-honesty.md
git commit -m "Add verbatim Academic Honesty / Title XII statement"
```

---

## Task 6: Write `references/classroom-behavior.md`

**Files:**
- Create: `auburn-syllabus/references/classroom-behavior.md`

**Source:** Auburn Policy on Classroom Behavior (effective 5/28/2013, Provost-responsible) AND the Biggio Center syllabus guidance verbatim short statement.

**Step 1: Write the file**

Content:
```markdown
# Classroom Behavior — Auburn Policy

## Short Syllabus Statement (Verbatim from Biggio Center)

Use this for the syllabus body:

> The Auburn University Classroom Behavior Policy is strictly followed in the course; please refer to the Student Policy eHandbook for details of this policy.

## Full Policy Reference (Effective 5/28/2013)

The full policy lists the following examples of improper behavior in the classroom (including the virtual classroom and activities associated with courses). This list is informational — the syllabus only needs to reference the policy, not reproduce it. Faculty may quote any subset if they want to set explicit expectations.

- Arriving after a class has begun
- Use of tobacco products
- Monopolizing discussion
- Persistent speaking out of turn
- Distractive talking, including cell phone usage
- Audio or video recording of classroom activities or the use of electronic devices without the permission of the instructor
- Refusal to comply with reasonable instructor directions
- Employing insulting language or gestures
- Verbal, psychological, or physical threats, harassment, and physical violence

## Required Elements (for review-mode validation)

A compliant classroom behavior statement must reference at least one of:
- "Auburn University Classroom Behavior Policy"
- "Student Policy eHandbook"

If neither is present, flag as ❌ Missing.
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/classroom-behavior.md
git commit -m "Add Auburn Classroom Behavior Policy reference"
```

---

## Task 7: Write `references/withdrawal-deadlines.md`

**Files:**
- Create: `auburn-syllabus/references/withdrawal-deadlines.md`

**Source:** Auburn Biggio Center syllabus guidance.

**Step 1: Write the file**

Content:
```markdown
# Withdrawal Deadlines — Auburn Verbatim Reminders

Use this verbatim. Place under "Grading and Evaluation Procedures."

## Statement (Verbatim, two reminders)

> A reminder that students may withdraw without grade penalty until the 15th class day, and until mid-semester (although a W will appear on the student's transcript if the student withdraws between the 16th and 36th class day).
>
> A reminder that students who withdraw from the course between the 6th class day and the 15th class day will pay a course drop fee of $100.

## Required Elements (for review-mode validation)

A compliant withdrawal section must reference:
- "15th class day" OR equivalent withdrawal deadline language, AND
- The "$100" course drop fee

If both are missing, flag as ❌ Missing. If only one is present, flag as ⚠️ Partial.
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/withdrawal-deadlines.md
git commit -m "Add verbatim withdrawal deadline reminders"
```

---

## Task 8: Write `references/excused-absences.md`

**Files:**
- Create: `auburn-syllabus/references/excused-absences.md`

**Source:** Auburn Biggio Center syllabus guidance — verbatim excused absences statement.

**Step 1: Write the file**

Content:
```markdown
# Excused Absences — Auburn Verbatim Statement

Use this verbatim.

## Heading

**Excused Absences**

## Statement (Verbatim)

> Students are granted excused absences from class for the following reasons: Illness of the student or serious illness of a member of the student's immediate family, death of a member of the student's immediate family, trips for student organizations sponsored by an academic unit, trips for University classes, trips for participation in intercollegiate athletic events, subpoena for a court appearance and religious holidays. Students who wish to have an excused absence from this class for any other reason must contact the instructor in advance of the absence to request permission. The instructor will weigh the merits of the request and render a decision. When feasible, the student must notify the instructor prior to the occurrence of any excused absences, but in no case shall such notification occur more than one week after the absence. Appropriate documentation for all excused absences is required.

## Required Elements (for review-mode validation)

A compliant excused absences statement must mention at least three of:
- Illness
- Family death (or "immediate family")
- Athletic / intercollegiate / sponsored trips
- Religious holidays
- Court / subpoena
- Documentation requirement

If fewer than three present, flag as ⚠️ Partial. If section is absent entirely, flag as ❌ Missing.
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/excused-absences.md
git commit -m "Add verbatim Auburn excused absences statement"
```

---

## Task 9: Write `references/makeup-policy.md`

**Files:**
- Create: `auburn-syllabus/references/makeup-policy.md`

**Source:** Auburn Biggio Center syllabus guidance — verbatim make-up policy.

**Step 1: Write the file**

Content:
```markdown
# Make-Up Policy — Auburn Verbatim Statement

Use this verbatim, then add an instructor-specific format line at the end.

## Heading

**Make-Up Policy**

## Statement (Verbatim)

> Arrangements to make up missed major examination (e.g. hour exams, mid-term exams) due to properly authorized excused absences. Except in unusual circumstances, such as continued absence of the student or the advent of University holidays, a make-up exam will take place within two weeks from the time the student initiates arrangements for it. Except in extraordinary circumstance, no make-up exams will be arranged during the last three days before the final exam period begins. The format of the make-up exam will be (as specific by the instructor).

## Instructor-Filled Variable

Replace `(as specific by the instructor)` with the actual format the instructor will use, e.g.:
- "the same format as the original exam"
- "an oral exam"
- "a take-home exam"

## Required Elements (for review-mode validation)

A compliant make-up section must reference:
- "within two weeks" OR equivalent timing
- A format specification (or placeholder for one)

If both missing, flag as ❌ Missing.
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/makeup-policy.md
git commit -m "Add verbatim Auburn make-up policy statement"
```

---

## Task 10: Write `references/mental-health-titleix.md`

**Files:**
- Create: `auburn-syllabus/references/mental-health-titleix.md`

**Source:** Auburn Biggio Center syllabus guidance — verbatim Mental Health, Basic Needs, and Sexual Misconduct (Title IX) statements.

**Step 1: Write the file**

Content:
```markdown
# Mental Health, Basic Needs, Title IX — Auburn Verbatim Statements

Use these verbatim. All three should appear in every Auburn syllabus.

## Mental Health

**Heading: Mental Health**

> If you or someone you know needs support, you are encouraged to contact Auburn Cares at 334-844-1305 or auburn.edu/auburncares. Auburn Cares will help you navigate any difficult circumstances you may be facing by connecting you with the appropriate resources or services.
>
> Student Counseling & Psychological Services provides confidential, no-cost mental health counseling and psychiatric services to Auburn Students. You can speak with a counselor 24/7/365 by calling 334-844-5123. Learn more about mental health information on campus at auburn.edu/scps.

## Basic Needs

**Heading: Basic Needs**

> Any student experiencing food insecurity or an unexpected financial crisis is encouraged to contact Auburn Cares at 334-844-1305 or auburn.edu/auburncares for resources and support.

## Sexual Misconduct Resources (Title IX)

**Heading: Sexual Misconduct Resources Statement**

> Auburn University faculty are committed to supporting our students and upholding gender equity laws as outlined by Title IX. Please be aware that if you choose to confide in a faculty member regarding an issue of sexual misconduct, dating violence, or stalking, we are obligated to inform the Title IX Office, who can assist you with filing a formal complaint, No-Contact Directives, and obtaining supportive measures. Find more information at auburn.edu/titleix.
>
> If you would like to speak with someone confidentially, Safe Harbor (334-844-7233) and Student Counseling & Psychological Services (334-844-5123) are both confidential resources. Safe Harbor provides support to students who have experienced sexual or relationship violence by connecting them with academic, medical, mental health, and safety resources. For additional information, visit auburn.edu/safeharbor.

## Required Elements (for review-mode validation)

- **Mental Health** — must reference Auburn Cares OR SCPS, OR phone numbers 334-844-1305 / 334-844-5123
- **Basic Needs** — must reference Auburn Cares (soft requirement; warn if missing)
- **Title IX** — must reference Title IX, Safe Harbor, or `auburn.edu/titleix`

Missing Title IX = ❌. Missing Mental Health = ❌. Missing Basic Needs = ⚠️.
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/mental-health-titleix.md
git commit -m "Add verbatim Mental Health, Basic Needs, Title IX statements"
```

---

## Task 11: Write `references/emergency-contingency.md`

**Files:**
- Create: `auburn-syllabus/references/emergency-contingency.md`

**Source:** Auburn Biggio Center syllabus guidance — verbatim emergency contingency statement.

**Step 1: Write the file**

Content:
```markdown
# Emergency Contingency — Auburn Verbatim Statement

Use this verbatim.

## Heading

**Emergency Contingency**

## Statement (Verbatim)

> If normal class and/or lab activities are disrupted due to illness, emergency, or crisis situation, the syllabus and other course plans and assignments may be modified to allow completion of the course. If this occurs, an addendum to your syllabus and/or course assignments will replace the original materials.

## Required Elements (for review-mode validation)

A compliant emergency contingency statement must reference:
- "syllabus...may be modified" OR equivalent flexibility language
- "addendum" OR equivalent change-document language

If absent entirely, flag as ❌ Missing.
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/emergency-contingency.md
git commit -m "Add verbatim emergency contingency statement"
```

---

## Task 12: Write `references/early-alert-grade.md`

**Files:**
- Create: `auburn-syllabus/references/early-alert-grade.md`

**Source:** Auburn Biggio Center syllabus guidance — required for Core Curriculum courses only.

**Step 1: Write the file**

Content:
```markdown
# Early Alert Grade — Auburn Verbatim Statement (Core Curriculum Only)

This statement is REQUIRED only for Core Curriculum courses. Do not include in non-Core syllabi.

## Heading

**Early Alert Grade**

## Statement (Verbatim)

> You will receive an "Early Alert Grade" one week prior to midterm (31st class day). The Early Alert Grade represents your current performance on class work graded at that point in the semester. If your Early Alert Grade is a "D," "F," or "FA," you will receive an email from the AU Retention Coordinator. Early Alert Grades can be viewed by logging into AU Access, opening the "tiger i" tab, selecting "Student Records" and opening the "Midterm Grades" window from the drop down box. If the grade appears inaccurate, please contact the instructor.

## Conditional Required Elements (for review-mode validation)

If the faculty member identifies the course as Core Curriculum, the syllabus must contain:
- "Early Alert Grade" reference
- "31st class day" or "midterm" timing
- "AU Access" navigation guidance

If course is Core and statement is missing, flag as ❌ Missing.
If course is not Core, this section should NOT be included.
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/early-alert-grade.md
git commit -m "Add verbatim Early Alert Grade statement (Core only)"
```

---

## Task 13: Write `references/core-curriculum-requirements.md`

**Files:**
- Create: `auburn-syllabus/references/core-curriculum-requirements.md`

**Source:** Auburn Biggio Center syllabus guidance — Core Curriculum SLO requirements.

**Step 1: Write the file**

Content:
```markdown
# Core Curriculum Requirements

If the faculty member identifies the course as part of Auburn's Core Curriculum, the syllabus has additional requirements:

## Required Sections

1. **Listed relevant Core Curriculum SLOs.** Auburn has identified 11 Core Curriculum Student Learning Outcomes. Faculty must list the SLOs the course satisfies and include their measures.
2. **Rubrics for the Core SLO measures** must be included in the syllabus.
3. **Early Alert Grade statement** (see `early-alert-grade.md`).

## Reference URL

Faculty should consult the Auburn Core Curriculum page for the full SLO list and measures. Provide a link in the syllabus rather than reproducing the list inline (the list may change).

## Example SLO Format (from Biggio Center)

> This course satisfies SLO 1: Students will be information literate. It is assessed by the following measures:
>
> - Determine the nature and extent of information needed.
> - Access information effectively and efficiently.
> - Evaluate information critically.
> - Use information to accomplish a specific purpose.
> - Understand the economic, legal, and social issues associated with using information.

## Workflow Note

In create/generate mode, ask: "Is this a Core Curriculum course?" If yes, also ask which Core SLOs the course satisfies. The skill should reproduce the SLO + measures format above for each declared Core SLO.

In review mode, only flag Core requirements if the user has confirmed the course is Core. Do not infer Core status from the course number.
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/core-curriculum-requirements.md
git commit -m "Add Core Curriculum requirements reference"
```

---

## Task 14: Write `references/graduate-course-requirements.md`

**Files:**
- Create: `auburn-syllabus/references/graduate-course-requirements.md`

**Source:** Auburn Biggio Center syllabus guidance — Graduate course addendum.

**Step 1: Write the file**

Content:
```markdown
# Graduate Course Requirements

Required only for courses at the 6000-level or above.

## Required Section

**Heading: Justification for Graduate Credit**

The syllabus must provide justification for graduate credit. Per Biggio Center guidance:

> Graduate course should be progressively more advanced in academic content than undergraduate programs and should foster independent learning, according to SACS guidelines.

## What to Include

The justification paragraph should explain:
1. How the course content is more advanced than undergraduate equivalents.
2. How the course fosters independent learning (research, original analysis, etc.).
3. How assessments require graduate-level work.

## Workflow Note

In create/generate mode, if the course number is 6000-level or above (or the faculty confirms graduate status), ask the faculty for a justification paragraph. Do not draft this without their input — it requires disciplinary judgment.

In review mode, if the course is graduate-level, flag missing "Justification for Graduate Credit" section as ❌.
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/graduate-course-requirements.md
git commit -m "Add graduate course Justification requirement"
```

---

## Task 15: Write `references/slo-writing-guide.md`

**Files:**
- Create: `auburn-syllabus/references/slo-writing-guide.md`

**Source:** Auburn Biggio Center syllabus guidance — SLO writing examples and the Outcomes vs Objectives distinction.

**Step 1: Write the file**

Content:
```markdown
# Student Learning Outcomes — Writing Guide

Use this when helping faculty draft or improve SLOs. Auburn requires 4–8 measurable SLOs.

## What Makes a Good SLO

A good SLO specifies an action by the student (not the instructor) that is **observable and measurable**, and therefore assessable.

### Weak vs Strong (from Biggio Center)

> **Weak SLO:** Students will gain critical thinking skills.
>
> **Better SLO:** Students will demonstrate critical thinking skills by applying X knowledge from the course to Y contexts in order to solve Z problems.

The strong version specifies the **action** (demonstrate), the **context** (applying X knowledge), and the **measurable outcome** (solve Z problems).

## Verbs to Prefer (Outcomes — student perspective)

- demonstrate, identify, calculate, compare, analyze, evaluate, design, construct, write, solve, distinguish

## Verbs to Avoid in SLOs (these belong in Objectives, not Outcomes)

- gain, understand, appreciate, enjoy, believe, grasp, study, know

## Examples (from Biggio Center, verbatim)

**Chemistry:** Students demonstrate understanding of fundamental concepts of chemistry by definition, explanation and use of these ideas in examinations and laboratory exercises.

**Statistics:** When given two events, you will be able to determine whether they are independent or whether there is a relationship between them. On the basis of this determination, you will be able to select and use the appropriate rules of conditional probability to determine the probability that a certain event will occur.

**Art:** When shown a print, students will be able to identify whether it is a woodcut, an etching or a lithograph, and students will be able to list the characteristics on which this identification was based.

**Psychology:** When given a case study, you will be able to identify whether it describes a case of schizophrenia, and if it does, which of the following schizophrenic reactions are involved: hybephrenic, catatonic or paranoia.

## Outcomes vs Objectives (Biggio Center distinction)

- **Outcomes** = end-result learning students must demonstrate. Framed from the student's perspective. Use specific verbs.
- **Objectives** = the means by which students will achieve the outcomes. Framed from the instructor's perspective. Use broad verbs.

A syllabus should include both, but Outcomes are required for assessment.

## Workflow Note

When the faculty member provides SLOs:
- If they all start with weak verbs (gain/understand/appreciate), warn and offer to rewrite using strong-verb format.
- If fewer than 4 SLOs, warn.
- If more than 8 SLOs, warn (Auburn recommends 4–8).
- If a faculty member asks for help drafting, propose strong-verb SLOs based on the course title and description, then ask for their confirmation before finalizing.
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/slo-writing-guide.md
git commit -m "Add SLO writing guide with Biggio Center examples"
```

---

## Task 16: Write `references/required-sections.md`

**Files:**
- Create: `auburn-syllabus/references/required-sections.md`

**Source:** Auburn Biggio Center syllabus guidance — full ordered section list.

**Step 1: Write the file**

Content:
```markdown
# Required Syllabus Sections — Order and Headings

This is the canonical section order for an Auburn syllabus. Use these heading names verbatim where possible.

## Section Order

1. **Course Number and Title** (header)
2. **Instructor Information** — Name, Office (or Virtual), Phone, Email, Office Hours, Response-time policy
3. **Course Description** — including a note that the course is fully online (online courses only)
4. **Credit Hours** — workload correlation
5. **Course Prerequisites / Co-requisites**
6. **Student Learning Outcomes (SLOs)** — 4–8 measurable outcomes
7. **Objectives** (optional but recommended) — instructor-framed
8. **Core Curriculum SLOs** (Core courses only) — with measures and rubrics
9. **Assignments and Grading**
   - List of assignments with brief overviews
   - Grading scale and method
   - Withdrawal reminders (verbatim from `withdrawal-deadlines.md`)
10. **Class Materials** — textbooks (with edition, link, thumbnail if helpful), readings
11. **Classroom Policies**
    - Excused Absences (verbatim from `excused-absences.md`)
    - Make-Up Policy (verbatim from `makeup-policy.md`)
    - Canvas / Email statement
    - Americans with Disabilities Act (verbatim from `ada-accommodations.md`)
    - Academic Honesty (verbatim from `academic-honesty.md`)
    - Classroom Behavior (verbatim from `classroom-behavior.md`)
    - Emergency Contingency (verbatim from `emergency-contingency.md`)
    - Early Alert Grade (Core courses only — verbatim from `early-alert-grade.md`)
12. **Generative AI Tools Policy** — chosen from `ai-policy-options.md`
13. **Statement on Divisive Concepts (SB 129)** — chosen from `sb129-boilerplate.md`
14. **Mental Health** (verbatim from `mental-health-titleix.md`)
15. **Basic Needs** (verbatim from `mental-health-titleix.md`)
16. **Sexual Misconduct Resources** / Title IX (verbatim from `mental-health-titleix.md`)
17. **Tentative 15-Week Schedule** — weekly topics, assessments, final exam slot
18. **Justification for Graduate Credit** (graduate courses only — guidance in `graduate-course-requirements.md`)

## Headings to Use Verbatim

Where the source guidance specifies a heading exactly, use it exactly:
- "Excused Absences"
- "Make-Up Policy"
- "Americans with Disabilities Act"
- "Academic Honesty"
- "Classroom Behavior"
- "Emergency Contingency"
- "Early Alert Grade"
- "Mental Health"
- "Basic Needs"
- "Sexual Misconduct Resources Statement"
- "Justification for Graduate Credit"
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/required-sections.md
git commit -m "Add required section order and heading list"
```

---

## Task 17: Write `references/biggio-syllabus-guidance.md`

**Files:**
- Create: `auburn-syllabus/references/biggio-syllabus-guidance.md`

**Source:** Auburn Biggio Center syllabus guidance — full text reproduced for Claude's context. The user pasted this verbatim during the brainstorm session on 2026-04-27. This file is the canonical reference Claude should consult when answering "why does Auburn require X" or making judgment calls.

**Step 1: Write the file**

Content (paste the full Biggio Center content the user provided in the brainstorm session, formatted as a structured markdown reference):

```markdown
# Auburn Biggio Center — Syllabus Guidance (Canonical Reference)

Source: Auburn University Biggio Center syllabus template, captured 2026-04-27. This document is the source-of-truth for Auburn-required syllabus structure. When in doubt about why a section is needed or what the exact wording should be, consult this file.

## Course Number and Title

This is the title that appears in the Bulletin and on student transcripts. The abbreviated title should be abbreviated in a way that is clear to the average user (a potential employer reading a student transcript). Use Roman numerals to designate first, second and third course in a sequence.

## Your Name and Contact Information

- Office number and building
- Office telephone number
- Email address
- Virtual Office Hours (and what technology to use to have them)
- A statement about when and how quickly you respond to email

It is important to get students to contain their correspondence to Canvas when possible, but you need to include your email to contact you if they are struggling to get into Canvas and have questions for you.

## Course Description

This can be the brief description from the Bulletin, or you can write a longer description. The description should indicate course content and not outcomes of the course. The goals are not only to ensure that students know what the course is about but also to clarify its rigor and scope.

For online courses, ensure students recognize the course is fully online in addition to the traditional description.

## Credit Hours

Define the number of hours of the course. Online time is flexible, so correlating this to a face to face workload time is what is necessary here.

## Course Prerequisites

Indicate whether the course has prerequisites, co-requisites (course(s) that must be taken the same semester), or prerequisites with concurrency.

Consider what to do if a student has the necessary pre-reqs but hasn't mastered the foundational knowledge. Where can a student go to get caught up?

## Student Learning Outcomes (SLOs)

Clear statements of what students should learn. Presented as a bulleted list of 4–8 comprehensive learning goals. SLOs specify what students should KNOW and DO by the end of the course.

An effective SLO specifies an action by the student that is observable and measurable.

(See `slo-writing-guide.md` for detailed examples.)

## Objectives

Objectives describe the means by which students will achieve the outcomes. They are framed from the instructor's perspective and use broad verbs (study, know, appreciate, etc.).

## Core Curriculum SLOs

Auburn has 11 Core Curriculum SLOs. For Core courses, relevant SLOs and their measures must be listed on the syllabus, and rubrics must be included.

(See `core-curriculum-requirements.md`.)

## Assignments, Grading, and Class Materials

- List of assignments with brief overviews
- Grading scale and method
- Schedule for examinations (other than final)
- Policy on unannounced quizzes
- Withdrawal reminders (see `withdrawal-deadlines.md`)
- List of textbooks, readings, and required/recommended materials with edition specificity

## Classroom Policies

Includes:
- Excused Absences (see `excused-absences.md`)
- Make-Up Policy (see `makeup-policy.md`)
- Canvas/email notification statement
- Americans with Disabilities Act (see `ada-accommodations.md`)
- Academic Honesty (see `academic-honesty.md`)
- Classroom Behavior (see `classroom-behavior.md`)
- Emergency Contingency (see `emergency-contingency.md`)
- Early Alert Grade (Core only — see `early-alert-grade.md`)

## Tentative 15-Week Schedule

- Due dates for reading assignments (with reminder to complete before lecture/discussion)
- Due dates for written work, exams, papers, projects
- Final examination at University-established date and time
- No exams during final three class days
- No major papers due so late they can't be returned by last day of class
- No final exams on last day of semester or Study Days

## Generative Artificial Intelligence Tools

The Biggio Center suggests one of four syllabus statements depending on the instructor's desired level of AI use. (See `ai-policy-options.md`.)

> All technology must be vetted through the Auburn University vetting process prior to use. Please contact your IT professional for more guidance.

## Mental Health, Basic Needs, Sexual Misconduct

Required statements (see `mental-health-titleix.md`).

## Graduate Courses

Graduate course syllabi must include a "Justification for Graduate Credit" section (see `graduate-course-requirements.md`).
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/biggio-syllabus-guidance.md
git commit -m "Add canonical Biggio Center syllabus guidance reference"
```

---

## Task 18: Write `references/sb129-act-text.md`

**Files:**
- Create: `auburn-syllabus/references/sb129-act-text.md`

**Source:** Alabama SB 129 Enrolled (effective Oct 1, 2024). Full text is in `additonal_resources/SB129-enr.pdf`. This file summarizes the operative provisions; Claude consults this when explaining WHY a syllabus rule exists, not for direct quote.

**Step 1: Write the file**

Content:
```markdown
# Alabama SB 129 / Act 2024-34 — Operative Summary

**Effective:** October 1, 2024
**Full text:** `additonal_resources/SB129-enr.pdf`

This file summarizes the operative provisions for syllabus authors. It is NOT for direct inclusion in syllabi — use `sb129-boilerplate.md` for the syllabus statement.

## What SB 129 Prohibits (Section 2)

Public institutions of higher education in Alabama may not:

1. Sponsor any DEI program or maintain any office promoting DEI programs.
2. Direct or compel a student, employee, or contractor to personally affirm, adopt, or adhere to a "divisive concept."
3. Require students/employees/contractors to attend DEI programs or training that requires assent to a divisive concept.
4. Require a student/employee/contractor to share their personal point of view on any divisive concept outside of an academic setting.
5. Require participation in lobbying activities related to a divisive concept.
6. Penalize students/employees/contractors for refusing to support a divisive concept or diversity statement.
7. Condition enrollment or attendance solely on race or color.
8. Authorize/expend funding to compel assent to a divisive concept.

## "Divisive Concepts" (Section 1, Subdivision 2)

The 8 concepts SB 129 defines as divisive — institutions cannot compel assent to any of these:

a. Any race/color/religion/sex/ethnicity/national origin is inherently superior or inferior.
b. Individuals should be discriminated against because of these traits.
c. Moral character is determined by these traits.
d. Individuals are inherently racist/sexist/oppressive due to these traits.
e. Individuals are responsible for past actions of others sharing these traits.
f. Fault/blame/bias should be assigned based on these traits.
g. Individuals should accept guilt/complicity/apology based on these traits.
h. Meritocracy or hard work ethic are racist or sexist.

## What SB 129 Allows (Section 4)

- Student/staff/faculty organizations can host DEI discussions if no state funds are used.
- Faculty can respond to questions about divisive concepts in coursework.
- Public institutions can teach divisive concepts **objectively, without endorsement**, as part of larger academic instruction (provided no compelled assent).
- Accreditation-required instruction is permitted.
- Historically accurate teaching is permitted.
- Research, recruiting, academic support, clinical services targeted to specific demographics are permitted.

## Key Implications for Syllabi

1. **No diversity statement requiring student assent** — except for narrow accreditation purposes.
2. **A "Divisive Concepts" statement is required** — Auburn's Provost provides two pre-approved versions in `sb129-boilerplate.md`.
3. **SLOs and grading must focus on critical thinking** — not adoption of viewpoints.
4. **Faculty may teach controversial material** — but objectively, without endorsement.

## Authoritative Source

When Auburn updates its Provost guidance for SB 129 compliance, update `sb129-boilerplate.md` first. This summary is for context; the boilerplate file is what gets used in syllabi.
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/sb129-act-text.md
git commit -m "Add SB 129 / Act 2024-34 operative summary"
```

---

## Task 19: Write `references/compliance-checklist.md`

**Files:**
- Create: `auburn-syllabus/references/compliance-checklist.md`

**Source:** Design doc Section 5 (this file is the operational rubric the skill uses in review mode).

**Step 1: Write the file**

Content:
```markdown
# Auburn Syllabus Compliance Checklist (Review-Mode Rubric)

This is the master rubric for review mode. The skill loads this file when reviewing an existing syllabus and produces a markdown table with one row per item, scoring each as ✅ Present / ⚠️ Partial / ❌ Missing, citing exact text from the syllabus or noting absence.

## Hard-Required Items (Auburn or Law)

| # | Item | Pass Criteria |
|---|------|---------------|
| 1 | Course number, title, credit hours, term | All four present |
| 2 | Instructor name + Auburn email | Auburn email format (`@auburn.edu`) |
| 3 | Course description | At least 1 sentence describing content |
| 4 | Measurable SLOs | 4–8 SLOs using strong verbs (see `slo-writing-guide.md`); fewer = ⚠️, more = ⚠️ |
| 5 | Grading scale + method | Numeric scale present and grade computation explained |
| 6 | Withdrawal reminders | "15th class day" + "$100" both present (see `withdrawal-deadlines.md`) |
| 7 | Excused absences statement | Mentions ≥3 of: illness, family death, athletics, religious, court, documentation |
| 8 | Make-up policy | "Within two weeks" + format specification |
| 9 | ADA / Office of Accessibility | Mentions AIM Portal OR `ACCESSIBILITY@auburn.edu` OR (334) 844-2096 |
| 10 | Academic Honesty | References Student Policy eHandbook OR Title XII |
| 11 | Classroom Behavior | References Auburn Classroom Behavior Policy OR Student Policy eHandbook |
| 12 | Emergency Contingency | References syllabus modification + addendum |
| 13 | AI Policy | One of 4 Auburn options OR a custom policy |
| 14 | SB 129 / Divisive Concepts statement | Full or Concise version, or substantively equivalent |
| 15 | Mental Health | References Auburn Cares OR SCPS |
| 16 | Title IX | References Title IX, Safe Harbor, or `auburn.edu/titleix` |
| 17 | 15-week schedule + final exam slot | Tentative schedule present with final exam date |

## Conditionally Required Items

| # | Item | When Required |
|---|------|---------------|
| 18 | Core Curriculum SLOs + measures + rubrics | Course is Core (faculty must declare) |
| 19 | Early Alert Grade statement | Course is Core |
| 20 | Justification for Graduate Credit | Course is 6000-level or above |

## Soft / Recommended (Warn but Don't Fail)

| # | Item | Pass Criteria |
|---|------|---------------|
| 21 | Virtual office hours + technology | Online courses |
| 22 | Email response-time statement | Any course |
| 23 | Prerequisites listed | If course has any |
| 24 | Textbook edition specificity | If textbooks listed |
| 25 | Basic Needs statement | All courses (warn if missing) |
| 26 | Canvas notification reminder | If course uses Canvas |

## Anti-Patterns (Flag These)

| Anti-Pattern | Severity | Reason |
|--------------|----------|--------|
| Diversity statement requiring student assent | ❌ | SB 129 violation |
| SLOs starting with "gain", "understand", "appreciate" | ⚠️ | Not measurable; Biggio guidance |
| Final exam scheduled on last day of semester or Study Days | ⚠️ | Auburn policy violation |
| Major papers due in last 3 class days | ⚠️ | Auburn policy guidance |
| AI policy missing entirely | ⚠️ | Post-2024 Auburn baseline expectation |

## Report Output Format

The review mode produces:

1. A markdown table with the columns: `#`, `Item`, `Status`, `Found`, `Recommendation`.
2. A summary count line: e.g. `**Summary: 14/17 hard-required, 0 anti-patterns. 3 critical issues, 5 warnings.**`
3. A closing offer: *"Want me to generate a corrected version that fills these gaps while keeping your existing content?"*

## Scoring Decision Rules

- ✅ Present: language matches source verbatim or is substantively equivalent.
- ⚠️ Partial: section exists but is missing required elements (per the per-reference "Required Elements" sub-sections).
- ❌ Missing: section is absent entirely or so minimal it doesn't satisfy the requirement.
```

**Step 2: Commit**

```bash
git add auburn-syllabus/references/compliance-checklist.md
git commit -m "Add review-mode compliance checklist rubric"
```

---

## Task 20: Write `assets/syllabus-template-online.md`

**Files:**
- Create: `auburn-syllabus/assets/syllabus-template-online.md`

**Source:** Section order from `required-sections.md`, with placeholders for variable content and pointers to `references/*` for verbatim boilerplate.

**Step 1: Write the file**

Content:
```markdown
# {{COURSE_NUMBER}}: {{COURSE_TITLE}}
## Auburn University — {{TERM}}

**Modality:** Online (asynchronous)
**Credit Hours:** {{CREDIT_HOURS}}
**Prerequisites:** {{PREREQUISITES_OR_NONE}}

---

## Instructor Information

- **Instructor:** {{INSTRUCTOR_NAME}}
- **Email:** {{INSTRUCTOR_EMAIL}}
- **Virtual Office Hours:** {{OFFICE_HOURS}} (via {{OFFICE_HOURS_TECH}})
- **Response Time:** {{RESPONSE_TIME_STATEMENT}}

> Please contain correspondence to Canvas when possible. Use email only if you cannot access Canvas.

## Course Description

{{COURSE_DESCRIPTION}}

This course is delivered fully online.

## Student Learning Outcomes

By the end of this course, students will be able to:

{{SLO_BULLET_LIST}}

{{IF_HAS_OBJECTIVES:
## Course Objectives

In this course, students will:

{{OBJECTIVES_BULLET_LIST}}
}}

{{IF_CORE_COURSE:
## Core Curriculum Student Learning Outcomes

This course satisfies the following Auburn Core Curriculum SLOs:

{{CORE_SLO_LIST_WITH_MEASURES}}

Rubrics for these measures are included as appendices to this syllabus.
}}

---

## Assignments and Grading

{{ASSIGNMENTS_LIST}}

**Grading Scale:** {{GRADING_SCALE}}

**Grading Method:** {{GRADING_METHOD_DESCRIPTION}}

{{INSERT references/withdrawal-deadlines.md — verbatim statement}}

## Class Materials

{{TEXTBOOKS_AND_MATERIALS_WITH_EDITIONS}}

---

## Classroom Policies

### Excused Absences

{{INSERT references/excused-absences.md — verbatim statement}}

### Make-Up Policy

{{INSERT references/makeup-policy.md — verbatim statement, with format specified by instructor}}

### Canvas and Email

Students are responsible for checking class emails and Canvas. Configure your Canvas notification settings to alert you when an Announcement is posted, an Assignment is due, or a grade is released.

### Americans with Disabilities Act

{{INSERT references/ada-accommodations.md — verbatim statement}}

### Academic Honesty

{{INSERT references/academic-honesty.md — verbatim statement}}

### Classroom Behavior

{{INSERT references/classroom-behavior.md — verbatim short statement}}

### Emergency Contingency

{{INSERT references/emergency-contingency.md — verbatim statement}}

{{IF_CORE_COURSE:
### Early Alert Grade

{{INSERT references/early-alert-grade.md — verbatim statement}}
}}

---

## Generative AI Tools Policy

{{AI_POLICY_BLOCK}}
<!-- AI_POLICY_BLOCK = chosen verbatim option from references/ai-policy-options.md -->

---

## Statement on Divisive Concepts (SB 129 / Act 2024-34)

{{SB129_STATEMENT_BLOCK}}
<!-- SB129_STATEMENT_BLOCK = chosen verbatim Full or Concise from references/sb129-boilerplate.md -->

---

## Mental Health

{{INSERT references/mental-health-titleix.md — Mental Health section}}

## Basic Needs

{{INSERT references/mental-health-titleix.md — Basic Needs section}}

## Sexual Misconduct Resources Statement

{{INSERT references/mental-health-titleix.md — Title IX section}}

---

## Tentative 15-Week Schedule

{{SCHEDULE_TABLE}}

**Final Exam:** {{FINAL_EXAM_DATE_PER_AU_CALENDAR}}

> Per Auburn policy, the final exam is held at the University-established date and time, not on the last day of the semester or on Study Days.

{{IF_GRADUATE_COURSE:
---

## Justification for Graduate Credit

{{GRADUATE_JUSTIFICATION}}
}}
```

**Step 2: Verify all placeholders use `{{}}` format**

Run:
```bash
grep -E '\{\{[A-Z_]+\}\}' auburn-syllabus/assets/syllabus-template-online.md | wc -l
```
Expected: at least 18 placeholders.

**Step 3: Commit**

```bash
git add auburn-syllabus/assets/syllabus-template-online.md
git commit -m "Add online course syllabus template"
```

---

## Task 21: Write `assets/syllabus-template-inperson.md`

**Files:**
- Create: `auburn-syllabus/assets/syllabus-template-inperson.md`

**Source:** Same structure as online template, with adjustments for in-person modality.

**Step 1: Write the file (copy of online template with these substitutions)**

Substitutions vs online template:
- `**Modality:** Online (asynchronous)` → `**Modality:** In-Person`
- Replace "Virtual Office Hours" with "Office Hours" and add `**Office Location:** {{OFFICE_LOCATION}}` and `**Office Phone:** {{OFFICE_PHONE}}`
- Replace `(via {{OFFICE_HOURS_TECH}})` with empty
- Remove `This course is delivered fully online.` line from Course Description section
- Replace `Please contain correspondence to Canvas...` callout with: `Email is the preferred method of out-of-class communication.`

Full content:
```markdown
# {{COURSE_NUMBER}}: {{COURSE_TITLE}}
## Auburn University — {{TERM}}

**Modality:** In-Person
**Credit Hours:** {{CREDIT_HOURS}}
**Prerequisites:** {{PREREQUISITES_OR_NONE}}
**Class Meeting Time and Location:** {{MEETING_TIME_AND_LOCATION}}

---

## Instructor Information

- **Instructor:** {{INSTRUCTOR_NAME}}
- **Office Location:** {{OFFICE_LOCATION}}
- **Office Phone:** {{OFFICE_PHONE}}
- **Email:** {{INSTRUCTOR_EMAIL}}
- **Office Hours:** {{OFFICE_HOURS}}
- **Response Time:** {{RESPONSE_TIME_STATEMENT}}

> Email is the preferred method of out-of-class communication.

## Course Description

{{COURSE_DESCRIPTION}}

## Student Learning Outcomes

By the end of this course, students will be able to:

{{SLO_BULLET_LIST}}

{{IF_HAS_OBJECTIVES:
## Course Objectives

In this course, students will:

{{OBJECTIVES_BULLET_LIST}}
}}

{{IF_CORE_COURSE:
## Core Curriculum Student Learning Outcomes

This course satisfies the following Auburn Core Curriculum SLOs:

{{CORE_SLO_LIST_WITH_MEASURES}}

Rubrics for these measures are included as appendices to this syllabus.
}}

---

## Assignments and Grading

{{ASSIGNMENTS_LIST}}

**Grading Scale:** {{GRADING_SCALE}}

**Grading Method:** {{GRADING_METHOD_DESCRIPTION}}

{{INSERT references/withdrawal-deadlines.md — verbatim statement}}

## Class Materials

{{TEXTBOOKS_AND_MATERIALS_WITH_EDITIONS}}

---

## Classroom Policies

### Class Attendance

{{ATTENDANCE_POLICY}}

### Excused Absences

{{INSERT references/excused-absences.md — verbatim statement}}

### Make-Up Policy

{{INSERT references/makeup-policy.md — verbatim statement, with format specified by instructor}}

### Canvas and Email

Students are responsible for checking class emails and Canvas. Configure your Canvas notification settings to alert you when an Announcement is posted, an Assignment is due, or a grade is released.

### Americans with Disabilities Act

{{INSERT references/ada-accommodations.md — verbatim statement}}

### Academic Honesty

{{INSERT references/academic-honesty.md — verbatim statement}}

### Classroom Behavior

{{INSERT references/classroom-behavior.md — verbatim short statement}}

### Emergency Contingency

{{INSERT references/emergency-contingency.md — verbatim statement}}

{{IF_CORE_COURSE:
### Early Alert Grade

{{INSERT references/early-alert-grade.md — verbatim statement}}
}}

---

## Generative AI Tools Policy

{{AI_POLICY_BLOCK}}

---

## Statement on Divisive Concepts (SB 129 / Act 2024-34)

{{SB129_STATEMENT_BLOCK}}

---

## Mental Health

{{INSERT references/mental-health-titleix.md — Mental Health section}}

## Basic Needs

{{INSERT references/mental-health-titleix.md — Basic Needs section}}

## Sexual Misconduct Resources Statement

{{INSERT references/mental-health-titleix.md — Title IX section}}

---

## Tentative 15-Week Schedule

{{SCHEDULE_TABLE}}

**Final Exam:** {{FINAL_EXAM_DATE_PER_AU_CALENDAR}}

> Per Auburn policy, the final exam is held at the University-established date and time, not on the last day of the semester or on Study Days.

{{IF_GRADUATE_COURSE:
---

## Justification for Graduate Credit

{{GRADUATE_JUSTIFICATION}}
}}
```

**Step 2: Commit**

```bash
git add auburn-syllabus/assets/syllabus-template-inperson.md
git commit -m "Add in-person course syllabus template"
```

---

## Task 22: Write `SKILL.md`

**Files:**
- Create: `auburn-syllabus/SKILL.md`

**This is the most important file.** It's the orchestration logic — Claude reads this every time the skill triggers and follows the workflow exactly.

**Step 1: Write the file**

Content:
```markdown
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
- "Is this primarily online, in-person, or hybrid?" (affects items 21)

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
```

**Step 2: Verify the SKILL.md frontmatter**

Run:
```bash
head -5 auburn-syllabus/SKILL.md
```
Expected: YAML frontmatter with `name`, `description`, `license`.

**Step 3: Commit**

```bash
git add auburn-syllabus/SKILL.md
git commit -m "Add SKILL.md orchestration with create/generate/review workflows"
```

---

## Task 23: Validate the skill structure

**Files:**
- No new files. Validation only.

**Step 1: Verify all expected files exist**

Run:
```bash
cd "/Users/mazin/Documents/UNI/AU ONLINE/CODING/SKILLS"
find auburn-syllabus -type f | sort
```

Expected output (19 files total):
```
auburn-syllabus/SKILL.md
auburn-syllabus/assets/.gitkeep
auburn-syllabus/assets/syllabus-template-inperson.md
auburn-syllabus/assets/syllabus-template-online.md
auburn-syllabus/references/.gitkeep
auburn-syllabus/references/academic-honesty.md
auburn-syllabus/references/ada-accommodations.md
auburn-syllabus/references/ai-policy-options.md
auburn-syllabus/references/biggio-syllabus-guidance.md
auburn-syllabus/references/classroom-behavior.md
auburn-syllabus/references/compliance-checklist.md
auburn-syllabus/references/core-curriculum-requirements.md
auburn-syllabus/references/early-alert-grade.md
auburn-syllabus/references/emergency-contingency.md
auburn-syllabus/references/excused-absences.md
auburn-syllabus/references/graduate-course-requirements.md
auburn-syllabus/references/makeup-policy.md
auburn-syllabus/references/mental-health-titleix.md
auburn-syllabus/references/required-sections.md
auburn-syllabus/references/sb129-act-text.md
auburn-syllabus/references/sb129-boilerplate.md
auburn-syllabus/references/slo-writing-guide.md
```

**Step 2: Verify SKILL.md frontmatter parses**

Run:
```bash
python3 -c "
import re, sys
with open('auburn-syllabus/SKILL.md') as f:
    content = f.read()
m = re.match(r'^---\n(.*?)\n---', content, re.DOTALL)
assert m, 'No YAML frontmatter found'
fm = m.group(1)
for required in ('name:', 'description:', 'license:'):
    assert required in fm, f'Missing {required}'
print('Frontmatter OK')
"
```

Expected: `Frontmatter OK`

**Step 3: Verify no Vercel/external skill references leaked into files**

Run:
```bash
grep -ril 'vercel\|next.js\|nextjs\|tailwind' auburn-syllabus/ || echo "Clean — no leaked tech stack references"
```

Expected: `Clean — no leaked tech stack references`

**Step 4: Commit (no changes, just validation pass)**

If validations pass, no commit needed. Move to Task 24.

---

## Task 24: Package the `.skill` archive

**Files:**
- Create: `auburn-syllabus.skill` (zip archive at repo root)

**Step 1: Build the archive**

Run:
```bash
cd "/Users/mazin/Documents/UNI/AU ONLINE/CODING/SKILLS"
rm -f auburn-syllabus.skill
# Remove .gitkeep before packaging — they're git-only artifacts
find auburn-syllabus -name '.gitkeep' -delete
cd auburn-syllabus && zip -r ../auburn-syllabus.skill . -x ".DS_Store" && cd ..
ls -la auburn-syllabus.skill
```

Expected: `auburn-syllabus.skill` exists, size between 30KB and 100KB.

**Step 2: Verify the archive contents**

Run:
```bash
unzip -l auburn-syllabus.skill
```

Expected: lists `SKILL.md`, `references/*.md` (18 files), `assets/*.md` (2 files).

**Step 3: Restore .gitkeep files in source folder for git history**

Run:
```bash
touch auburn-syllabus/references/.gitkeep auburn-syllabus/assets/.gitkeep
```

**Step 4: Commit the archive**

```bash
git add auburn-syllabus.skill auburn-syllabus/
git commit -m "Build auburn-syllabus.skill archive v1.0"
```

---

## Task 25: Update README.md with the new skill

**Files:**
- Modify: `README.md` (add fourth entry under "Available Skills"; update "Repository Structure" diagram)

**Step 1: Add the new skill entry**

Edit `README.md` — add this entry under "Available Skills" after the `ada-transcript-docx` section:

```markdown
### `auburn-syllabus`
Creates, generates, or reviews Auburn University course syllabi for compliance with Auburn's official requirements — Provost guidance, Biggio Center template, ADA, SB 129 / Alabama Act 2024-34, Title IX, and the Auburn Classroom Behavior Policy. Three modes: build a new syllabus from scratch, generate one from pasted course details, or review an existing syllabus and produce a compliance report. All boilerplate ships verbatim from Auburn-approved sources. Outputs markdown by default; can hand off to `auburn-docx` for a branded Word version.
```

**Step 2: Update the Repository Structure diagram**

Replace the existing Repository Structure block with:

```
.
├── auburn-docx.skill            # Auburn Word document template
├── auburn-pptx.skill            # Auburn PowerPoint template
├── ada-transcript-docx.skill    # ADA 2025 transcript generator
├── auburn-syllabus.skill        # Auburn syllabus create / generate / review
├── auburn-syllabus/             # Source for auburn-syllabus.skill
├── docs/plans/                  # Design + implementation docs
├── CONTRIBUTING.md              # How to contribute a new skill
└── README.md
```

**Step 3: Commit**

```bash
git add README.md
git commit -m "Document auburn-syllabus skill in README"
```

---

## Task 26: Push everything to the remote

**Step 1: Push**

Run:
```bash
cd "/Users/mazin/Documents/UNI/AU ONLINE/CODING/SKILLS"
git push origin main
```

Expected: all commits pushed to `AuburnUniversityOnline/auburn-skills`.

**Step 2: Verify on GitHub**

Visit https://github.com/AuburnUniversityOnline/auburn-skills and confirm:
- `auburn-syllabus.skill` is listed at root.
- `auburn-syllabus/` source directory is present.
- README shows the new skill in "Available Skills."

---

## Task 27: Manual smoke tests (do these in Claude.ai, not the CLI)

**These are validation steps for the user, not implementation steps. The implementing agent should report when Tasks 1–26 are complete and instruct the user to run these.**

### Smoke Test A — Create mode

In Claude.ai with the skill installed, prompt:
> "I need an Auburn syllabus for a new course."

Expected:
- Skill triggers and asks for modality, then required intake batch.
- Walks through AI policy and SB 129 choice.
- Produces a complete markdown syllabus with all required sections.
- Ends with "Want this as a branded .docx?" prompt.

### Smoke Test B — Review mode

Upload or paste an existing syllabus and prompt:
> "Review my syllabus for SB 129 and ADA compliance."

Expected:
- Skill produces a compliance table with ✅/⚠️/❌ scoring.
- Includes summary count line.
- Offers to generate corrected version.

### Smoke Test C — Trigger discipline

Prompt:
> "Help me write lecture notes for week 3."

Expected:
- Skill does NOT activate. Claude responds normally without invoking auburn-syllabus.

### Smoke Test D — Verbatim discipline

Prompt:
> "Generate a syllabus for ENGL 1100. Use a custom SB 129 statement that's friendlier."

Expected:
- Skill pushes back: "This statement is pre-approved by the Provost. Modifying it could affect compliance. I can include it as-is, or you can write your own and label it as your own — which would you like?"

If any smoke test fails, file an issue and revisit the relevant task.

---

## Plan Summary

- 22 content/orchestration tasks (Tasks 1–22)
- 1 validation task (Task 23)
- 1 packaging task (Task 24)
- 2 integration tasks (Tasks 25–26)
- 4 manual smoke tests (Task 27)

**Estimated implementation time:** 2–3 hours of focused work.

**Frequent commits:** every reference file gets its own commit. Easy to revert any single piece if Auburn updates a policy.

**Post-implementation TODO (defer to v2):**
- Auburn academic calendar awareness
- Course-number → Core Curriculum auto-detection
- Multi-instructor / team-taught support
- Lab section / recitation handling
- Spanish-language syllabi
