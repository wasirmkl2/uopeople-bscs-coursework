---
inclusion: always
---

# UoPeople CS 1111 — Verified Answer Bank

Answers below are **confirmed by graded attempts**, not inferred, unless marked otherwise.

## Attempt log

| Attempt | Type | Score | Notes |
|---|---|---|---|
| 1 | Cumulative/mixed quiz (20 q) | 19/20 (95%) | Only Q15 (logic gate circuit diagram) was wrong |

## Attempt 1 — question-by-question results

| # | Question (topic) | Answer given | Result |
|---|---|---|---|
| 1 | Primary challenge in debugging logical errors | Understanding the program's overall logic | CONFIRMED CORRECT |
| 2 | Errors identified/corrected during debugging phase | Logical errors | CONFIRMED CORRECT |
| 3 | Boolean simplification: XY'Z + XY'Z' | XY' | CONFIRMED CORRECT |
| 4 | NOT an actuator example | Pressure sensor | CONFIRMED CORRECT |
| 5 | Main focus of abstraction | Separating the interface from the implementation | CONFIRMED CORRECT |
| 6 | Primary benefit of VR in employee training | Reduced training costs | CONFIRMED CORRECT |
| 7 | Primary goal of Supervised Learning | Minimize prediction errors | CONFIRMED CORRECT |
| 8 | Primary purpose of ASCII | To represent alphanumeric characters and symbols | CONFIRMED CORRECT |
| 9 | OS feature enabling concurrent execution of multiple OS instances on one machine | Virtualization | CONFIRMED CORRECT |
| 10 | SDLC step where actual programming happens | Development and documentation | CONFIRMED CORRECT |
| 11 | Analyzing a programming problem — step beyond initial requirements | Exploring additional features | CONFIRMED CORRECT |
| 12 | Primary purpose of a database schema | Define the structure of the database | CONFIRMED CORRECT |
| 13 | Optical discs (CD/DVD) storage type | Optical storage | CONFIRMED CORRECT |
| 14 | Transparency is key to Blockchain integrity/security | TRUE | CONFIRMED CORRECT |
| 15 | **Logic gate circuit output (image-based question)** | (A+B)(B+C) — **WRONG** | **CONFIRMED WRONG — correct answer is (A+B)(A+C)** |
| 16 | Topology with greatest flexibility for wired device connections | Mesh topology | CONFIRMED CORRECT |
| 17 | Purpose of if-else statement | Conditional execution | CONFIRMED CORRECT |
| 18 | Microsoft Word is an example of | Application software | CONFIRMED CORRECT |
| 19 | Distributed file system in Big Data — main advantage is low latency | FALSE | CONFIRMED CORRECT |
| 20 | Multitasking OS is a logical extension of the ___ OS | Multiprogramming | CONFIRMED CORRECT |

## Q15 — Logic gate circuit diagram (CONFIRMED WRONG, corrected)

**Correct answer: (A+B)(A+C)**

Image reference: `q15.png` in this same folder. The circuit has three inputs (A, B, C) and one output (Y), built from two OR gates feeding a final AND gate.

**What I got wrong:** I misread the wiring and traced it as top-OR-gate = (A+B), bottom-OR-gate = (B+C), giving Y = (A+B)(B+C). This was incorrect.

**Correct trace:** Top OR gate inputs = A, C → output = (A+C). Bottom OR gate inputs = A, B → output = (A+B) [or the equivalent arrangement where A is the shared/branching input feeding both OR gates, with B and C as the other respective inputs]. Final AND gate combines both OR outputs: Y = (A+B)(A+C).

**Lesson:** When tracing multi-input gate diagrams from an image, do not assume which input branches to which gate — trace each wire individually from source to destination before concluding the boolean expression. This question type (3-input circuit, 2 ORs feeding 1 AND, answer options differing only in which two inputs share the AND-side vs OR-side) is a recurring trap; the wrong intuitive read swaps which input (A vs B) is the "shared/common" one across both OR gates. Verify by checking which single input line visually splits/branches to feed both OR gates — that one is the "common" term appearing in both parenthetical groups of the answer, e.g., (A+B)(A+C) means A is the common branching input.

## Notes

- 19/20 (95%) — every other topic (debugging, Boolean algebra, robotics actuators, abstraction, VR training, supervised learning, ASCII, virtualization, SDLC phases, database schema, optical storage, blockchain transparency, network topology, if-else, application software, distributed file systems, multitasking/multiprogramming) is now graded-confirmed correct and can be trusted directly if these exact questions/options reappear.
- Only the image-based logic gate question (Q15-style) needs careful re-tracing each time rather than pattern-matching to a prior answer, since the specific wiring (which input branches where) varies between versions of this question.

