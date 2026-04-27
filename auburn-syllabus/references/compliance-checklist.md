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
