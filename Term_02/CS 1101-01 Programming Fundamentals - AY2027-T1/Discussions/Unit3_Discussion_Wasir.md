# Discussion Forum Unit 3: Managing Student Grades with Loops

**Posted by:** S M Wasir Jayed Rafi
**Course:** CS 1101-01 — Programming Fundamentals (AY2027-T1)

## Question 1: For Loops

A `for` loop goes through a sequence one item at a time and runs the same block of code for each item, which means printing every name in a class list doesn't need a separate `print()` line written out for each student (Mohbey & Acharya, 2023). Python also doesn't need a counter to track position the way some other languages do — on each pass, the loop variable just moves to the next item in the sequence, and the loop stops by itself once it reaches the last one (Alex The Analyst, 2022a).

```python
students = ["Alice", "Ben", "Chloe", "David"]
for student in students:
    print(student)
```

Output:
```
Alice
Ben
Chloe
David
```

Here, `student` takes on the value `"Alice"` on the first pass, then `"Ben"`, then `"Chloe"`, then `"David"`, printing each one before the loop ends automatically.

## Question 2: While Loops

A `while` loop checks a condition before every iteration and keeps running as long as that condition stays true, which fits a situation where the teacher decides how many grades to enter and the program has no way to know that number in advance (Mohbey & Acharya, 2023). Instead of looping a fixed number of times, the loop can just keep asking for input until the teacher types "done":

```python
grades = []
entry = input("Enter a grade (or 'done' to finish): ")
while entry.lower() != "done":
    grades.append(int(entry))
    entry = input("Enter a grade (or 'done' to finish): ")
print(grades)
```

If the teacher enters 85, 90, and 78 before typing "done," the loop runs three times, appending each number to `grades`, and stops the moment the condition `entry.lower() != "done"` becomes false. Alex The Analyst (2022b) points out that a while loop's condition is what's actually driving the loop, so it's worth double-checking that something inside the loop body eventually makes that condition false — otherwise the loop just keeps running forever.

## Question 3: Break and Continue Statements

`break` and `continue` both interrupt a loop's normal flow, but in different ways: `break` exits the loop immediately and skips everything after it, while `continue` only skips the rest of the current pass and moves on to the next one (Khan Academy, 2024). For the grade-entry program, that difference matters because "stop early" and "skip this one bad entry" are two different problems that shouldn't be handled the same way.

```python
grades = []
while True:
    entry = input("Enter a grade (or 'done' to finish): ")
    if entry.lower() == "done":
        break
    grade = int(entry)
    if grade < 0:
        print("Invalid grade, skipping.")
        continue
    grades.append(grade)
print(grades)
```

Typing "done" hits the `break` and ends the loop completely, regardless of how many grades came before it. A negative number like -10 hits the `continue` instead — the program prints a warning, skips adding that number to the list, and goes straight back to asking for the next grade rather than shutting down. Running this with the inputs 85, -10, 90, then "done" leaves `grades` holding only `[85, 90]`, since -10 never gets appended. Khan Academy (2024) makes a similar point about skipping bad data with `continue` instead of stacking up nested `if` checks, which is really what makes this approach cleaner than trying to validate everything in one giant condition.

## Question 4: Nested Loops

A nested loop is a loop placed inside the body of another loop, so the inner loop finishes all of its passes once for every single pass of the outer loop (Mohbey & Acharya, 2023). That's a natural fit for the `classes` list here, since it isn't just one flat list of names — it's a list of lists, one per class, and printing all the names means handling two levels of structure at once (Simplilearn, 2021).

```python
classes = [["Alice", "Ben"], ["Chloe", "David"]]
for class_number, class_list in enumerate(classes, start=1):
    print(f"Class {class_number}:")
    for name in class_list:
        print(f"  {name}")
```

Output:
```
Class 1:
  Alice
  Ben
Class 2:
  Chloe
  David
```

The outer loop moves through each class ("Class 1," then "Class 2"), and for every one of those, the inner loop moves through that specific class's name list before the outer loop advances again. A nested loop is genuinely useful here rather than just adding complexity, because printing every name means working through two levels of structure at once: which class, then which student in that class. A single loop over `classes` would iterate through the inner lists one at a time, rather than through each student's name individually — the inner loop is what breaks that down further into each student. The nesting lets the program treat "which class" and "which student in that class" as two separate steps instead of trying to flatten everything into one loop and losing track of which student belongs where.

## Closing Thought

Across all four questions, the loop type someone reaches for depends on what's actually known in advance: a `for` loop when the sequence is already defined (the student list, the classes list), and a `while` loop when the stopping point depends on something that happens during runtime, like a teacher deciding when to stop entering grades. `break` and `continue` then give more precise control inside either kind of loop, and nesting lets a program work through multiple levels of structure without losing track of where it is.

## References

Alex The Analyst. (2022a, November 22). *For loops in Python | Python for beginners* [Video]. YouTube. https://www.youtube.com/watch?v=zmIdC0_0BgY

Alex The Analyst. (2022b, November 29). *While loops in Python | Python for beginners* [Video]. YouTube. https://www.youtube.com/watch?v=ECduJk00mUU

Khan Academy. (2024, July 24). *Break and continue | Intro to CS - Python | Khan Academy* [Video]. YouTube. https://www.youtube.com/watch?v=Xnzjr0Pcx-A

Mohbey, K. K., & Acharya, M. (2023). Looping statements. In *Basics of Python programming: A quick guide for beginners*. Bentham Science Publishers.

Simplilearn. (2021, September 17). *Nested loop in Python -15 | Python nested loops tutorial | Python for beginners | Simplilearn* [Video]. YouTube. https://www.youtube.com/watch?v=qk3q8n4EUE4
