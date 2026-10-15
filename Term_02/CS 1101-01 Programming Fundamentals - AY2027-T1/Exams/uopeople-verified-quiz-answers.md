---
inclusion: always
---

# UoPeople CS 1101 — Verified Answer Bank

Answers below are **confirmed by graded attempts**, not inferred, unless marked otherwise.

## Attempt log

| Attempt | Type | Score | Notes |
|---|---|---|---|
| 1 | Unit quiz (5 q) | 5/5 (100%) | All confirmed correct by user |

## Attempt 1 — question-by-question results

| # | Question (topic) | Answer given | Result |
|---|---|---|---|
| 1 | Which of the following is a Boolean value? (10 / True / 3.5 / "True") | True | CONFIRMED CORRECT |
| 2 | Float values do not contain decimals. (True/False) | False | CONFIRMED CORRECT |
| 3 | Programming is only used for developing web applications. (True/False) | False | CONFIRMED CORRECT |
| 4 | Which assignment operator adds and assigns at the same time? (+= / => / =+ / =) | += | CONFIRMED CORRECT |
| 5 | Which function converts a number to a string in Python? (int() / float() / bool() / str()) | str() | CONFIRMED CORRECT |

## Notes

- Basic Python fundamentals (data types, Boolean values, float vs int, assignment operators, type-conversion functions) — trust these directly if these exact questions/options reappear.
- Key distinctions to remember: `True`/`False` (bare, unquoted) = Boolean; `"True"` (quoted) = string. `+=` is the compound assignment operator for add-and-assign. `str()` converts numeric types to string; `int()`/`float()`/`bool()` convert to their respective types.


## Attempt 2 — Unit 2 quiz: Boolean logic & conditionals (5 q)

| # | Question (topic) | Answer given | Result |
|---|---|---|---|
| 1 | Which expression evaluates to True | `5 > 10 or 4 > 2` | CONFIRMED CORRECT |
| 2 | Output of `if x and y:` with x=5, y=0 | B | CONFIRMED CORRECT |
| 3 | Best check for number NOT between 10 and 20 inclusive | `not (num >= 10 and num <= 20)` | CONFIRMED CORRECT |
| 4 | Output of nested if/else with age=17 | Teenager | CONFIRMED CORRECT |
| 5 | Output of nested if with num=45, modulo checks | Valid Number | CONFIRMED CORRECT |

All 5/5 confirmed correct. Key reasoning:
- Short-circuit evaluation: `and`/`or` return one of the actual operands, not always `True`/`False` (e.g., `7 and 0` → `0`).
- `not (num >= 10 and num <= 20)` is the correct De Morgan's-style negation of an inclusive range check.
- Nested `if` statements evaluate outer condition first, then inner condition, printing based on the deepest matching branch.


## Attempt 3 — Unit 3 self-quiz: loops (5 q)

| # | Question (topic) | Answer given | Result |
|---|---|---|---|
| 1 | A while loop checks its condition after executing the body. (True/False) | False | CONFIRMED CORRECT |
| 2 | Which keyword is used in a Python for loop to iterate over a sequence? (to/from/in/over) | in | CONFIRMED CORRECT |
| 3 | How many times will the loop body execute for `for x in [3,1,4,1,5]:`? | 5 times | CONFIRMED CORRECT |
| 4 | Where is the condition checked in a while loop? (Before each iteration / Only when break appears / Only once at start / After each iteration ends) | Before each iteration begins | CONFIRMED CORRECT |
| 5 | Which scenario best suits a while loop? (fixed-length string / fixed numeric range / fixed-size list / read input until 'quit') | Read user input until the user types 'quit' | CONFIRMED CORRECT |

All 5/5 confirmed correct. Key reasoning:
- `while` loops are pre-check (condition tested **before** each iteration, including the first) — never post-check in Python (there is no do-while).
- `for x in sequence:` — `in` is a syntactic component of the for-statement, unrelated to the membership-test `in` operator.
- `for` loops over a list execute once per element, counting duplicates (5 elements → 5 iterations regardless of repeated values).
- `while` is the right choice whenever the number of iterations is unknown in advance (e.g., sentinel-controlled input loops); `for` suits fixed-size/known-length sequences and ranges.



## Attempt 4 — Unit 3 GRADED quiz: loops, loop control & conditionals review (15 q)

**Score: 15/15 — all CONFIRMED CORRECT by user.**

| # | Question (topic) | Answer given | Result |
|---|---|---|---|
| 1 | Using `continue` in a loop terminates the loop entirely. (True/False) | False | CONFIRMED CORRECT |
| 2 | In nested loops, the inner loop runs exactly once for each outer loop iteration. (options listed False/True — reversed order) | False | CONFIRMED CORRECT |
| 3 | While loop quality-check; stop loop immediately and continue with rest of program (skip/break/continue/pass) | break | CONFIRMED CORRECT |
| 4 | Scanning product IDs; stop as soon as target found (pass/next/break/continue) | break | CONFIRMED CORRECT |
| 5 | Method to access both keys and values iterating a dict (values()/items()/pairs()/keys()) | items() | CONFIRMED CORRECT |
| 6 | ____ is the best way to avoid too much nesting | combining conditions with and/or | CONFIRMED CORRECT |
| 7 | Where would you use if-else over if-elif-else? | When there are only two possible outcomes | CONFIRMED CORRECT |
| 8 | Why is indentation critical in Python conditionals? | Because indentation defines code blocks instead of braces | CONFIRMED CORRECT |
| 9 | Rewrite nested `if x > 10: if x < 20:` efficiently | `if 10 < x < 20: print("In range")` | CONFIRMED CORRECT |
| 10 | Python executes if-elif-else from ____ | top to bottom | CONFIRMED CORRECT |
| 11 | The operator `%=` is a type of assignment operator. (True/False) | True | CONFIRMED CORRECT |
| 12 | Which function displays output to the screen? (read()/print()/open()/input()) | print() | CONFIRMED CORRECT |
| 13 | The symbol `#` in Python is used for ____ | Comments | CONFIRMED CORRECT |
| 14 | The result of `15 % 4` is ____ | 3 | CONFIRMED CORRECT |
| 15 | To convert input into an integer, we use ____ | int() | CONFIRMED CORRECT |

### Key reasoning / reusable notes

- **`continue` vs `break`:** `continue` skips only the remainder of the *current* iteration and proceeds to the next; the loop does NOT exit. `break` exits the nearest enclosing loop immediately and moves control past it. Both Q3 and Q4 are `break` — "stop immediately / exit as soon as found" is always `break`.
- **`pass` is a null statement** — it does nothing at all and never affects loop control. `skip` and `next` are not Python loop-control statements (distractors).
- **Nested loops (Q2 trap):** the inner loop completes its *full* range of iterations on every single outer iteration — total inner-body executions = outer × inner. Verified by running outer `range(3)` × inner `range(4)` → 12 executions, not 3. Note the option order was reversed (False listed first) — read option text, don't click by position.
- **Chained comparison (Q9):** `10 < x < 20` is the exact equivalent of `x > 10 and x < 20`. Verified over x in 0..30. Distractors diverge: `(x >= 10 and x >= 20)` is False at x=15 (should be True); `(x > 10 or x < 20)` is True at x=5 (should be False).
- **`items()`** yields key-value pairs for `for k, v in d.items():`. `keys()`/`values()` give one side only; `pairs()` does not exist.
- **Reducing nesting:** combine conditions with `and`/`or` (or use chained comparisons) to flatten nested `if` blocks.
- **`if-else` vs `if-elif-else`:** two outcomes → `if-else`; three or more → `if-elif-else`. Evaluation is strictly top-to-bottom, first true branch wins, rest skipped.
- **Indentation** is syntactically meaningful in Python — it delimits blocks where other languages use braces. It is not stylistic and has no runtime-speed effect.
- **Compound assignment operators** include `%=` (modulo-and-assign), alongside `+=`, `-=`, `*=`, `/=` — same family as the `+=` confirmed in Attempt 1.
- **Basic I/O & syntax:** `print()` outputs, `input()` reads (always returns a string), `int(input())` converts input to integer, `#` begins a comment.
- **`15 % 4 = 3`** (15 = 4×3 + 3). Verified by execution.


## Attempt 5 — Unit 4 self-quiz: functions, scope, lambda, *args (5 q)

**Score: 5/5 — all CONFIRMED CORRECT by user.**

| # | Question (topic) | Answer given | Result |
|---|---|---|---|
| 1 | Output of global `x = 50`, `outer()` sets `x = 20`, nested `inner()` sets `x = 10` and prints; then `outer` prints, then global print (10 20 50 / 50 20 10 / 10 10 10 / 20 20 20) | 10 20 50 | CONFIRMED CORRECT |
| 2 | What happens if a function has no return statement? (raises error / prints automatically / returns 0 / returns None) | It returns None | CONFIRMED CORRECT |
| 3 | Output of `x = lambda a, b: a + b; print(x(2, 3))` (5 / 23 / a + b / Error) | 5 | CONFIRMED CORRECT |
| 4 | Which best describes "scope"? (range of values / part of program where a variable is accessible / data type / number of uses) | The part of a program where a variable is accessible | CONFIRMED CORRECT |
| 5 | Special symbol for variable-length arguments in Python functions (# / & / * / %) | * | CONFIRMED CORRECT |

### Key reasoning / reusable notes

- **Variable shadowing (Q1):** each assignment inside a function creates a new *local* name, so nothing changes the outer variables unless `global`/`nonlocal` is used. Prints happen innermost first: `10` (inner), `20` (outer), `50` (global). Verified by execution.
- **LEGB rule:** name lookup order is Local → Enclosing → Global → Built-in.
- **No `return`** → function implicitly returns `None` (verified: `def f(): pass; print(f())` → `None`). Not `0`, not an error.
- **`lambda`** creates an anonymous single-expression function; `x(2, 3)` evaluates `2 + 3` → `5` (numeric addition, not string concatenation `"23"`).
- **`*args`** collects extra positional arguments into a tuple; **`**kwargs`** collects extra keyword arguments into a dict. `#` = comment, `%` = modulo, `&` = bitwise AND (distractors).


## Attempt 6 — Unit 5 self-quiz: lists & tuples (5 q)

**Score: 5/5 — all CONFIRMED CORRECT by user.**

| # | Question (topic) | Answer given | Result |
|---|---|---|---|
| 1 | In `nums = [10,20,30,40,50]`, what is `nums[2]`? (10 / 20 / 30 / 40) | 30 | CONFIRMED CORRECT |
| 2 | Result of `fruits = ['apple','banana']; fruits.insert(1,'mango')` | `['apple','mango','banana']` | CONFIRMED CORRECT |
| 3 | How to access the first element of `t = ('x','y','z')`? (`t(0)` / `t[0]` / `t{0}` / `t.0`) | `t[0]` | CONFIRMED CORRECT |
| 4 | Which operation will cause an error? (`t = (1,2,3); t[1]=4` / `len(t)` / `t[0]` / `t+(4,5)`) | `t = (1,2,3); t[1]=4` | CONFIRMED CORRECT |
| 5 | Process of assigning multiple values to a tuple at once is called ____ (packing / unpacking / grouping / stacking) | packing | CONFIRMED CORRECT |

### Key reasoning / reusable notes

- **Indexing starts at 0:** `nums[2]` is the third element (`30`). Verified by execution.
- **`list.insert(i, x)`** puts `x` at index `i` and shifts later elements right (does not replace). Verified: `['apple', 'mango', 'banana']`.
- **Tuple indexing uses square brackets** — `t[0]`. Round brackets would be a call, curly braces a syntax error, `t.0` invalid.
- **Tuples are immutable:** item assignment raises `TypeError: 'tuple' object does not support item assignment`. `len(t)`, `t[0]`, and `t + (4,5)` (builds a *new* tuple `(1, 2, 3, 4, 5)`) all work.
- **Packing vs unpacking (Q5 trap):** *packing* = putting several values INTO a tuple (`atoms = ("Hydrogen", 1, "Helium", 2)`); *unpacking* = pulling a tuple's values OUT into separate variables (`a, b, c = t`). Wording "assigning multiple values **to a tuple**" → packing. Wording "assigning a tuple's values **to multiple variables**" would be unpacking. Source: Parker, Ch. 3 "Tuple Assignment"; Mohbey & Acharya "Tuple Assignment".


## Attempt 7 — Unit 6 self-quiz: dictionaries & sets (5 q)

**Score: 5/5 — all CONFIRMED CORRECT by user.**

| # | Question (topic) | Answer given | Result |
|---|---|---|---|
| 1 | Result of `len({'a':1, 'b':2, 'a':3})` (2 / 3 / Error: Duplicate key / 1) | 2 | CONFIRMED CORRECT |
| 2 | Output of `print(set('aba'))` (`{'a','b'}` / `{'a','b','a'}` / `{'aba'}` / `{'b','a'}`) | `{'a','b'}` | CONFIRMED CORRECT |
| 3 | Output of `print(sorted({'c':3,'a':1,'B':2}.keys()))` | `['B','a','c']` | CONFIRMED CORRECT |
| 4 | Both `s1=set()` and `s2={}` create an empty set. (True/False) | False | CONFIRMED CORRECT |
| 5 | Output of `d = {'a':1, 'b':2}; d['a'] += d['b']; print(d)` | `{'a':3, 'b':2}` | CONFIRMED CORRECT |

### Key reasoning / reusable notes

- **Duplicate keys in a dict literal (Q1):** no error — the later value overwrites the earlier one, so `{'a':1,'b':2,'a':3}` becomes `{'a':3,'b':2}` and `len()` is `2`. Verified by execution.
- **Sets drop duplicates (Q2 trap):** `set('aba')` has the two elements `a` and `b`. Set display order is not guaranteed, so both `{'a','b'}` and `{'b','a'}` are the same set; the option confirmed correct was `{'a','b'}` (Python 3 prints `{'a', 'b'}` here). Not `{'a','b','a'}` (duplicates) or `{'aba'}` (that would be a one-element set holding the string).
- **Sorting is by character code (Q3):** uppercase letters sort before lowercase (`'B'`=66 < `'a'`=97 < `'c'`=99), so `['B','a','c']`. Keys here are all strings, so they are sortable; `sorted()` returns a list.
- **Empty set vs empty dict (Q4 trap):** `{}` creates an empty **dict**; an empty set must be made with `set()`. Verified: `type({})` → `dict`, `type(set())` → `set`.
- **Augmented assignment on a dict value (Q5):** `d['a'] += d['b']` → `d['a'] = 1 + 2 = 3`; `'b'` unchanged. Dict *values* are mutable and can be reassigned; only dict *keys* must be immutable/hashable.


## Attempt 8 — Quiz: lists, tuples, dictionaries, functions & scope review (15 q)

**Score: 15/15 — all CONFIRMED CORRECT by user.**

| # | Question (topic) | Answer given | Result |
|---|---|---|---|
| 1 | In `nums = [10,20,30,40,50]`, what is `nums[2]`? (10 / 20 / 30 / 40) | 30 | CONFIRMED CORRECT |
| 2 | Once created, a tuple's elements can be modified. (True/False) | False | CONFIRMED CORRECT |
| 3 | Which operation will cause an error? (`t = (1,2,3); t[1]=4` / `len(t)` / `t[0]` / `t+(4,5)`) | `t = (1,2,3); t[1]=4` | CONFIRMED CORRECT |
| 4 | `my_list[1:-1]` excludes the first and last element. (True/False) | True | CONFIRMED CORRECT |
| 5 | List method that counts occurrences of an element (find() / count() / search() / index()) | count() | CONFIRMED CORRECT |
| 6 | Which statement accurately describes dict keys? | Keys must be immutable (e.g., strings, tuples, numbers) and unique within the dictionary | CONFIRMED CORRECT |
| 7 | Output of `d = {'a':1}; print(d.pop('b', 5))` (1 / None / Error / 5) | 5 | CONFIRMED CORRECT |
| 8 | `d = {'a':1}; 'a' in d.values()` returns? (True / False / None / Syntax Error) | False | CONFIRMED CORRECT |
| 9 | Create a dict from `['x','y']` and `[1,2]` with keys as 1 and 2 | `dict(zip([1,2],['x','y']))` | CONFIRMED CORRECT |
| 10 | Result of `len({'a':1, 'b':2, 'a':3})` (2 / 3 / Error: Duplicate key / 1) | 2 | CONFIRMED CORRECT |
| 11 | Which of the following prevents shadowing effectively? (global everywhere / ignoring scope / consistent naming conventions / avoiding functions) | Using consistent naming conventions | CONFIRMED CORRECT |
| 12 | Lambda functions can have multiple expressions. (True/False) | False | CONFIRMED CORRECT |
| 13 | Argument type that provides default values when not passed (positional / keyword / default / variable-length) | Default argument | CONFIRMED CORRECT |
| 14 | Output of nested `outer()`/`inner()` with `x = 50 / 20 / 10` (10 20 50 / 50 20 10 / 10 10 10 / 20 20 20) | 10 20 50 | CONFIRMED CORRECT |
| 15 | Variable shadowing occurs when: | A local variable hides a global variable of the same name | CONFIRMED CORRECT |

### Key reasoning / reusable notes

- **Repeat questions:** Q1, Q3 (Attempt 6), Q10 (Attempt 7) and Q14 (Attempt 5) were exact repeats of earlier confirmed entries — the bank-first lookup was right; trust them if they reappear.
- **Tuples are immutable (Q2, Q3):** item assignment raises `TypeError`; `t + (4,5)` just builds a new tuple.
- **Slicing (Q4):** `my_list[1:-1]` starts at index 1 and stops *before* the last element, so first and last are excluded (`[1,2,3,4,5][1:-1]` → `[2,3,4]`).
- **`count()` (Q5):** counts occurrences of a value; `index()` returns a position; lists have no `find()` or `search()`.
- **Dict keys (Q6):** must be immutable/hashable and unique. A list key raises `TypeError: unhashable type: 'list'`. Keys are not limited to strings. Source: Mohbey & Acharya, Tuples and Dictionaries chapter.
- **`dict.pop(key, default)` (Q7):** returns the default when the key is missing instead of raising `KeyError`.
- **`in d.values()` (Q8 trap):** checks *values*, not keys. `'a' in d.values()` is False for `{'a':1}`, while `'a' in d` (keys) would be True.
- **`dict(zip(keys, values))` (Q9):** the first list becomes the keys. `zip([1,2],['x','y'])` → `{1:'x', 2:'y'}`. Option `dict([('x','y'),(1,2)])` gives `{'x':'y', 1:2}`; `dict({'x':1,'y':2})` has string keys; `{'x','y':[1,2]}` is a `SyntaxError`.
- **Shadowing prevention (Q11):** the Unit 4 reading (Bencini, "Variable shadowing in Python") recommends clear variable names and understanding scope boundaries — "consistent naming conventions" was the confirmed key answer. `global` everywhere makes shadowing/scope bugs worse.
- **Lambda (Q12):** any number of arguments but only ONE expression. Source: Mohbey & Acharya, Functions chapter.
- **Default argument (Q13):** a parameter given a value with `=` in the `def` (`def f(a, b=10)`); used when the caller omits it.
- **Shadowing (Q14, Q15):** a local variable with the same name as an outer/global one hides it inside that scope without changing the outer one. Prints go innermost first: `10 20 50`.
