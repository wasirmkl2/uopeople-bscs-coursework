---
inclusion: always
---

# Quick Reference — How This Household Works With the Assistant

This is a short, practical note for Wasir and Saira, distilled from a real session where
cost and turn-count grew larger than necessary. It doesn't replace the detailed rules in
`assignment-writing-rules.md` — it's the "before you start" checklist for using this
assistant efficiently on assignment work.

## 1. One chat per person, per assignment
Draft each person's assignment in its own session rather than doing both people's work in
one long combined chat. A single long session keeps reprocessing the *entire* history on
every turn (both papers, every past review, every past fix), which gets expensive fast.
Exception: the cross-household overlap check (Section 15 of `assignment-writing-rules.md`)
still needs to happen once both drafts exist — do that as its own short, separate step
(a fresh lightweight chat, or a focused message with both finalized drafts pasted in) rather
than keeping both papers "live" in the same session the whole time.

## 2. Don't paste a whole outside AI review — paste the claim
If a second AI tool or reviewer gives feedback, don't paste the entire multi-paragraph
review. Per the standing rule, its score and word-count numbers get ignored anyway (see
Section 6 of `assignment-writing-rules.md`), so pasting the whole thing just adds cost for
no benefit. Instead, extract only the *specific factual claims* worth checking, e.g.:

> "It says Tsui & Chen's study measured kitchen speed directly — is that actually what
> they measured?"

That's cheaper to process and gets the same real verification done.

## 3. Batch edit requests instead of one-fix-per-message
When asking for revisions, bundle them: "reword these two paragraphs for variety, and also
double check the Meiser citation has a working link" in one message, rather than sending
each fix separately. Every edit triggers a full re-verification pass (word count, phrase
overlap, citation match) per the rules — fewer, larger edit batches means fewer full
re-verification cycles.

## 4. Build the `.docx` file last, push last
Don't ask for the Word document to be built until the text content itself is fully approved.
Rebuilding the formatted file while the text is still changing wastes effort. Finalize the
plain-text/markdown draft first, get explicit sign-off on the content, *then* ask for the
`.docx` build and git push in the same final step.

## 5. Model effort level
Medium reasoning effort is the right default for this kind of work (drafting, citation
verification, n-gram/overlap checks, moderate research) — it's not a place where deeper
reasoning effort meaningfully helps. The real cost lever is turn/context volume (points 1–4
above), not the effort setting itself.

## 6. HARD RULE — never create the file or touch git until the user says the content is final
This rule was violated once already in this project: a Unit 4 discussion draft was written
straight into a repo file, committed, pushed to a new branch, and opened as a PR in the same
turn the draft was first produced — before the user had seen or approved a single word of it.
The PR had to be closed and the branch deleted afterward. Treat this as a hard gate, not a
preference:

- **Step 1 — draft only.** The very first version of any discussion post, peer reply, or
  written assignment is pasted directly into the chat response as plain text/markdown. No
  file is created on disk for it. No `git` command of any kind (`add`, `commit`, `push`,
  branch creation, `gh api` PR creation) runs at this stage, regardless of how confident the
  draft feels or how much verification (word count, citations, code testing) has already
  been done on it.
- **Step 2 — revise in chat.** Any requested changes are applied to the in-chat draft and
  re-pasted in full. Still no file, still no git.
- **Step 3 — explicit go-ahead required.** Only create the `.md`/`.docx` file and run `git`
  commands after the user gives an explicit, unambiguous instruction to do so (e.g., "push
  this," "commit it," "make the file," "this is final, go ahead"). Finishing a checklist,
  passing verification, or the assistant's own judgement that the draft is "ready" does
  **not** count as that instruction — only the user's own words do. If it's ambiguous
  whether the user meant "this looks good" vs. "go ahead and push it," ask which one before
  touching a file or git.
- This applies to every deliverable type covered elsewhere in this file: discussion posts,
  peer replies, and standalone written assignments (`.docx`) alike. It supersedes the
  softer "only at final push time" phrasing that used to be here — that phrasing was
  demonstrably not strict enough to prevent the violation described above.

## 7. Due-date offset (confirmed, both students)
Both students' assignment portals display due dates in their local timezone, which runs one
calendar day ahead of UoPeople's own reference timezone. Always print **the displayed due
date minus one day** on the title page (e.g., portal says "Sep 17, 2026" → title page says
"September 16, 2026"). This is now recorded per-student in each repo's
`assignment-writing-rules.md` (Section 1) — don't re-derive it from scratch each time.
