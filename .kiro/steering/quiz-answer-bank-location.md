# Quiz Answer Bank Location

**Quiz answer bank content may be freely shared/mirrored between this repo and the
household's other UoPeople repo (`uopeople-bsba-coursework`)** — this is an explicit
exception to the assignment/discussion no-cross-referencing policy found in
`assignment-writing-rules.md` and the student-profile steering, which exists for
academic-integrity reasons around graded original writing. Quiz questions and their verified
answers are reference material, not graded submissions, so no such concern applies here — the
user has confirmed sharing this content between repos is fine, with no restrictions.

Verified quiz answer banks live per-course, out of `.kiro/steering/`, at:

- **UNIV 1002-01:** `Term_01/UNIV 1002-01 Online Education Strategies for Non-Native English Speakers - AY2026-T5/Exams/uopeople-verified-quiz-answers.md`
- **CS 1111-01:** `Term_01/CS 1111-01 Introduction to Computer Science - AY2026-T5/Exams/uopeople-verified-quiz-answers.md`
- **ENGL 1102-01:** `Term_02/ENGL 1102-01 English Composition 2 - AY2027-T1/Exams/uopeople-verified-quiz-answers.md`
- **CS 1101-01:** `Term_02/CS 1101-01 Programming Fundamentals - AY2027-T1/Exams/uopeople-verified-quiz-answers.md`

**When the user sends quiz questions for any of these courses, read that course's file first** before answering — it contains confirmed correct/incorrect answers from real graded/self-quiz attempts, plus trap notes for tricky/absolute-wording questions. Treat entries marked CONFIRMED CORRECT as ground truth; treat entries marked UNVERIFIED/REASONED GUESS as inferences that still need confirmation. If a new question doesn't match an existing entry (different wording, different image, different option set), it must be worked from scratch — do not assume a similar-sounding past question applies.

## Answering process — first-pass sourcing order

For every new quiz question, work through sources in this order before answering:

1. **This course's `uopeople-verified-quiz-answers.md` file** — check for an exact or
   near-exact match first (same question, same or reordered options).
2. **The course's actual assigned Readings** (unit reading HTML pages, textbook chapters/
   sections named in them, video transcripts) — read the real material, don't answer from
   general recollection of the subject.
3. **The open internet**, only if steps 1–2 don't resolve it — and say explicitly when an
   answer relies on this step rather than the course's own materials, since course-specific
   quiz keys sometimes diverge from the strict/standard textbook definition (see the Q6
   functional-relationship trap note in the ENGL 1102-01 file as a concrete example).

## Logging rule — confirm before logging, every time, no exceptions

**Do not write a new answer into any `uopeople-verified-quiz-answers.md` file until the user
has explicitly confirmed the real result of that specific question** (i.e., told you it was
scored correct or incorrect on an actual quiz attempt). Do not log:

- Answers the assistant is only reasoning about and hasn't heard back on yet.
- Answers from a batch where the user hasn't yet replied to confirm results.

When a user does confirm a batch, log each item with the right label:
**CONFIRMED CORRECT**, **CONFIRMED WRONG**, or (only if explicitly instructed to log a
not-yet-graded guess for future reference) **REASONED (unconfirmed)**. If a previously
logged CONFIRMED entry turns out to have been wrong (e.g., the option set changes, or the
same question is later confirmed incorrect), correct that entry in place rather than leaving
the outdated line standing — note both the old and new answer so the trap is documented (see
the Q1/functional-relationship correction in the ENGL 1102-01 file as the pattern to follow).

## Verification discipline — always re-derive, never eyeball, especially for images/diagrams

A real graded attempt on CS 1111 scored 19/20, with the **one miss being an image-based logic
gate circuit question (Q15)**. The wrong answer was given because the wiring in the circuit
image was traced too quickly — pattern-matching to "looks like a standard OR-OR-AND circuit"
instead of tracing each wire individually from source to destination. The correct answer was
(A+B)(A+C); the answer given was (A+B)(B+C) — a swap of which input (A vs. B) was the "shared/
common" branching line feeding both OR gates.

**Before presenting any answer derived from an image, diagram, circuit, or table (not just
plain text), do all of the following, every time, no exceptions:**

1. Re-read the actual image file with the read tool immediately before answering — do not
   rely on a description or a memory of the image from earlier in the conversation.
2. Trace every single connection/wire/line individually from its source to its destination.
   For circuits specifically: identify every gate, every input line, and exactly which gate(s)
   each input line feeds, one at a time. Do not assume a "typical" or "expected" wiring pattern
   just because the layout looks familiar.
3. Re-derive the final answer from that explicit trace (e.g., write out the boolean expression
   term by term) rather than jumping straight to matching one of the multiple-choice options
   by eye.
4. Cross-check the derived answer against each answer option individually, confirming exactly
   why the other options are wrong, not just why the chosen one seems right.
5. If there is any uncertainty in a trace (a wire that's ambiguous, a low-resolution image, an
   unclear label), say so explicitly rather than presenting a guess with full confidence.

This same discipline (re-derive from scratch, don't pattern-match) applies to every question
type, not just circuits — boolean algebra simplifications, SDLC step ordering, and any other
question with a precise, checkable derivation should be worked out step by step and the
derivation shown, rather than answered from a confident-sounding recollection.



## Efficiency rule — extract PDF text before reading, don't over-verify clean matches

**Never read a `.pdf` reading file directly with a raw file-read tool.** Raw reads return
the undecoded PDF byte stream (compressed binary), which is not usable text and tends to
blow past output limits after burning a large number of tokens for zero signal. Before
reading any assigned-reading PDF for source-checking, extract its text first (e.g. a short
Python snippet using `pypdf`: install if missing, then `PdfReader(...).pages[i].extract_text()`
joined across pages) and read/search that extracted text instead of the PDF file itself.

**Don't multiply verification steps once a question is already resolved.** If the course's
own `uopeople-verified-quiz-answers.md` file or the assigned Readings give an unambiguous,
exact/near-exact match for a question, answer from that and stop — do not also run
redundant web searches "just to be sure" for questions with no ambiguity. Reserve extra
web verification (multiple searches, cross-checking several sources) for cases where:
- the assigned readings are silent or unclear on the question, or
- the question smells like a potential course-specific trap (absolute/unusual wording,
  an option set that doesn't cleanly match the textbook's own phrasing, a question type
  similar to a previously-logged trap in this file).

Getting a generic question right isn't evidence the sourcing process was unnecessary — the
bank-first → readings → web order exists specifically to catch the cases where this course's
quiz key diverges from the standard/generic answer (see the Unit 1 Q6 functional-relationship
trap as the concrete precedent). The point is to spend verification effort where divergence
risk is real, not to verify every question to the same depth regardless of how clear-cut it is.
