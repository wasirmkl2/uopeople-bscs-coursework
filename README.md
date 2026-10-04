# uopeople-bscs-coursework

Personal repository for coursework in the **Bachelor of Science in Computer Science
(BS-CS)** program at the **University of the People (UoPeople)**.

## Student

- **Name:** S M Wasir Jayed Rafi
- **Program:** BS-CS, University of the People
- **Term 1 start date:** June 18
- **Term structure:** 9 units per term, 1 week per unit

See `.kiro/steering/student-profile-wasir.md` for the full, up-to-date profile (current
unit progress, course/instructor list, discussion deadlines).

## Repository structure

Coursework is organized by term, then by course, then by content type:

```
Term_01/
  <Course Code and Title - Term Code>/
    README.md
    Readings/       # provided reading assignments (course material)
    Assignments/    # written assignments submitted for grading
    Discussions/    # discussion board posts and peer replies
    Exams/          # MCQ / True-False exam material and notes
```

- Each **term** gets its own top-level folder (e.g., `Term_01`, `Term_02`, ...).
- Each **course** inside a term gets its own folder, named after the official course code
  and title (e.g., `CS 1111-01 Introduction to Computer Science - AY2026-T5`), with its own
  `README.md` describing that course (instructor, unit breakdown, deliverables).
- Within `Assignments/`, `Discussions/`, and `Exams/`, group files by unit as the term
  progresses so a given unit's work stays together.

## Term 1 Courses (AY2026-T5) — COMPLETED

**Term 1 coursework is finished and final grades are posted.**

| Course | Instructor | Credits | Grade |
|---|---|---|---|
| [CS 1111-01 — Introduction to Computer Science](<Term_01/CS 1111-01 Introduction to Computer Science - AY2026-T5>) | Mohamadou Bassirou Jean-Baptiste Sanfo | 3 | 98 / A+ |
| [UNIV 1002-01 — Online Education Strategies for Non-Native English Speakers](<Term_01/UNIV 1002-01 Online Education Strategies for Non-Native English Speakers - AY2026-T5>) | Mustapha Kammouss | 3 | 100 / A+ |

## Term 2 Courses (AY2027-T1) — IN PROGRESS

**Term 2 is underway; Unit 1 is currently running.**

| Course | Instructor |
|---|---|
| ENGL 1102-01 — English Composition 2 | Aparna Rajith (aparna.rajith@uopeople.edu) |
| CS 1101-01 — Programming Fundamentals | Hussam Al Khouja (hussam.alkhouja@uopeople.edu) |

## Discussion deadlines

Unless a specific unit's instructions say otherwise, both courses follow this pattern:

- **Main/initial discussion post:** due Sunday.
- **Peer replies:** due Wednesday.

## Steering / Kiro configuration

This repo uses [Kiro](https://kiro.dev) steering files under `.kiro/steering/` to keep
writing-quality rules and student-specific context available across sessions:

- `assignment-writing-rules.md` — general, name-agnostic rules for citations, tone, word
  count, discussion posts, and peer replies, learned from real instructor feedback on past
  submissions.
- `student-profile-wasir.md` — this student's program, courses, instructors, and schedule.
