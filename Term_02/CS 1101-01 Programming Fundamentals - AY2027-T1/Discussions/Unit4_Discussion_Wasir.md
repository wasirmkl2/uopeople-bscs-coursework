# Discussion Forum Unit 4: Tracking Fitness Goals with Functions

**Posted by:** S M Wasir Jayed Rafi
**Course:** CS 1101-01 — Programming Fundamentals (AY2027-T1)

## Question 1: Designing Custom Functions

The tracker does the same jobs every day — recording the activity, averaging the week, checking whether the goals were hit, printing a summary — and only the numbers change. That's exactly what a function is for: a named block of code that runs one task when it's called, takes data in through parameters, and hands a result back with a `return` statement (Mohbey & Acharya, 2023). They also draw a distinction the design depends on: parameters are the names listed in the definition, while arguments are the actual values supplied at the moment of the call. The same chapter notes that splitting a long program by what each part does keeps small units easy to test in isolation, so I would write one function per job rather than one long block — the modular structure Programming with Mosh (2018) demonstrates for beginners.

```python
STEP_GOAL, CALORIE_GOAL, MINUTE_GOAL = 10000, 500, 30

def log_day(weekly_totals, steps, calories, minutes):
    """Add one day's activity to the running weekly totals."""
    weekly_totals["steps"] += steps
    weekly_totals["calories"] += calories
    weekly_totals["minutes"] += minutes
    return weekly_totals

def calculate_weekly_average(weekly_totals, days_logged):
    """Return average steps, calories, and minutes for the days logged."""
    return {key: total / days_logged for key, total in weekly_totals.items()}

def check_goals_met(steps, calories, minutes):
    """Return whether each of the three daily goals was met."""
    return {"steps": steps >= STEP_GOAL,
            "calories": calories >= CALORIE_GOAL,
            "minutes": minutes >= MINUTE_GOAL}

def display_summary(day_number, steps, calories, minutes, goals_met):
    """Print one day's activity and which goals were reached."""
    print(f"Day {day_number}: {steps} steps, {calories} cal, {minutes} min")
    for goal, met in goals_met.items():
        print(f"  {goal} goal {'met' if met else 'not met'}")
```

Running all four across two days shows what each call takes in and produces:

```python
weekly_totals = {"steps": 0, "calories": 0, "minutes": 0}

for day, (steps, calories, minutes) in enumerate([(9500, 480, 28),
                                                  (11000, 520, 35)], start=1):
    weekly_totals = log_day(weekly_totals, steps, calories, minutes)
    display_summary(day, steps, calories, minutes,
                    check_goals_met(steps, calories, minutes))

print("Totals:", weekly_totals)
print("Averages:", calculate_weekly_average(weekly_totals, 2))
```

Output:

```
Day 1: 9500 steps, 480 cal, 28 min
  steps goal not met
  calories goal not met
  minutes goal not met
Day 2: 11000 steps, 520 cal, 35 min
  steps goal met
  calories goal met
  minutes goal met
Totals: {'steps': 20500, 'calories': 1000, 'minutes': 63}
Averages: {'steps': 10250.0, 'calories': 500.0, 'minutes': 31.5}
```

`log_day()` takes the running totals plus the day's three values and returns the updated dictionary; because dictionaries are mutable, it updates that same object in place rather than building a new one. `calculate_weekly_average()` takes the totals and a day count and returns a brand-new dictionary of averages, leaving the totals untouched. `check_goals_met()` returns three booleans. `display_summary()` only prints, so it implicitly returns `None`, Python's default when nothing is returned explicitly.

## Question 2: Local vs. Global Variables

Scope describes where a variable can be reached, and lifetime describes how long it survives (Mohbey & Acharya, 2023). A local variable is created inside a function and disappears once that call finishes, while a global variable lives in the program's main body and can be read from anywhere. In this tracker, `steps`, `calories`, `minutes`, and `goals_met` should all stay local, since each belongs to a single day; that's what stops one day's numbers from bleeding into the next.

`weekly_totals` genuinely has to persist across days, but that still doesn't make it a good candidate for global. I create it in the main program and pass it into `log_day()`, keeping the data flow visible in the signature. Assigning to a name that matches a global just creates a separate local variable rather than changing the original (Mohbey & Acharya, 2023), which Bencini (2025) calls shadowing. A global `weekly_totals` is where that bites: a careless reassignment would create a separate local, leave the real totals unchanged, and quietly discard that day's update. So no variable here needs the `global` keyword at all. The only global values are the three goal constants, which sit at the top level so the thresholds live in one place instead of inside `check_goals_met()`, the only function that reads them. Their uppercase names signal constants by convention, though Python doesn't actually prevent reassignment.

Adding a seventh day then costs one function call rather than another copy of the same arithmetic, and the scope choices keep those calls from interfering.

## References

Bencini, N. (2025, March 4). *Variable shadowing in Python*. Medium. https://medium.com/@nicbencini/variable-shadowing-in-python-cfc5457a67c3

Mohbey, K. K., & Acharya, M. (2023). Functions. In *Basics of Python programming: A quick guide for beginners*. Bentham Science Publishers.

Programming with Mosh. (2018, November 6). *Python functions | Python tutorial for absolute beginners #1* [Video]. YouTube. https://www.youtube.com/watch?v=u-OmVr_fT4s
