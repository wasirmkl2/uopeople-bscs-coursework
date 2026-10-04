# Session Starter Prompts

Copy-pasteable prompts for starting new Kiro sessions on recurring UoPeople tasks. These are
reference text, not auto-loaded instructions — paste the relevant one as your first message
in a **new** session (see `workflow-quick-reference.md` for why separate sessions per person/
task are recommended).

Fill in the bracketed placeholders before sending. Paste the actual assignment prompt/rubric
text as instructed in each one — don't summarize it, since exact rubric wording matters.

---

## 1. Starting a new written assignment (single student, single session)

```
This is [Wasir/Saira], continuing the recurring UoPeople assignment workflow. Read the
steering files in .kiro/steering/ first (assignment-writing-rules.md, this repo's
student-profile file, workflow-quick-reference.md).

We're doing the [Unit N] Assignment for [Course Code — Course Name]. I'll paste the actual
assignment prompt and rubric next — read it and the real Unit [N] reading materials in the
Readings folder before asking me anything.

[paste the full assignment prompt + rubric here]
```

Then, once the assistant asks its batched topic/angle questions, answer them directly rather
than letting it guess. Expect: a short set of questions → a few genuinely distinct
topic/angle options → a full draft → an explicit checks report (word count, phrase
repetition, citation/reference match, APA formatting, paragraph-opening variety) before the
draft is presented.

## 2. Starting a discussion forum initial post

```
This is [Wasir/Saira]. Read the steering files first. This is the Unit [N] Discussion for
[Course Code]. Here's the actual discussion prompt:

[paste the full discussion prompt here]
```

## 3. Requesting a peer reply

```
Here's the peer's post I need to reply to for Unit [N] [Course Code] (posting the full
thread — their post plus any existing replies already on it):

[paste peer's post + any existing replies here]
```

Per the standing rule, peer replies skip the "ask before drafting" step — expect a
ready-to-review reply in the same turn, not a round of clarifying questions first.

## 4. Requesting changes to an existing draft (batch, not one-at-a-time)

```
A few changes to the current draft, all at once:
1. [change 1 — e.g., "reword paragraph 3 for sentence variety, keep the content"]
2. [change 2 — e.g., "double check the [Author] citation has a working link"]
3. [change 3, if any]
Give me the full updated assignment after.
```

## 5. Checking a specific claim from an outside AI review (don't paste the whole review)

```
An outside review claims [the specific factual claim, e.g., "Tsui & Chen's study measured
kitchen speed directly" or "the word count is 605"]. Can you verify that against the actual
saved draft/source before I trust it?
```

## 6. Final pre-submission check for a single student's assignment

```
Check everything thoroughly one more time before submission: word count (with real buffer,
not just under the ceiling), phrase repetition, citation-to-reference matching, APA
formatting, paragraph-opening variety. Then build the .docx and push to main.
```

---

## 7. Cross-household comparison (ENGL 1102-01 specific — run in its own short session)

Use this once **both** household members have a finalized draft for the same unit. Paste
both full finalized drafts (body + references) into a **new, separate, lightweight session**
— don't run this inside either person's drafting session.

```
This is a cross-household overlap check for ENGL 1102-01, Unit [N]. Both Wasir and Saira
have finalized drafts for the same assignment prompt. Diff these two drafts for shared 3+
word phrases (beyond citation names and unavoidable required assignment terms, like a
phrase lifted directly from the assignment prompt itself). Flag anything that isn't
unavoidable, and tell me exactly which sentences need rewording on which side. Don't touch
either file yet — just report the diff first.

--- WASIR'S FINALIZED DRAFT ---
[paste full draft]

--- SAIRA'S FINALIZED DRAFT ---
[paste full draft]
```

Once the diff comes back, ask for fixes explicitly (e.g., "reword these on Saira's side,
not Wasir's, since his is already submitted") rather than letting the assistant guess which
side to edit. If one assignment has already been pushed/submitted, say so explicitly —
edits should generally go to whichever one hasn't been finalized/submitted yet.
