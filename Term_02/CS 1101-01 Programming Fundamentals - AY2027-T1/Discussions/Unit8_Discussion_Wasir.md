# Discussion Forum Unit 8: Python Libraries and Object-Oriented Programming in a Personal Assistant App

**Posted by:** S M Wasir Jayed Rafi
**Course:** CS 1101-01 — Programming Fundamentals (AY2027-T1)

## Question 1: Built-in Libraries in the Personal Assistant

A personal assistant that sets reminders, picks quotes, and files reports would take far too long to build if every one of those jobs had to be coded from scratch. Python avoids that with modules. According to Mohbey and Acharya (2023), a module is a Python file that holds reusable code, and splitting a program into modules makes it simpler to understand, more convenient to use, and logically organized. The built-in modules come with Python itself. Mastrodomenico (2022) uses datetime as the example, describing it as part of the standard library, which means it ships with Python and isn't developed by a third party.

The math module supports mathematical functions such as trigonometry, angle conversion, and logarithms, while the random module generates pseudo-random values, meaning numbers that look random but come from an algorithm (Mohbey & Acharya, 2023). The os module handles operating-system tasks such as creating and deleting folders, fetching a folder's contents, and identifying the current directory (Mohbey & Acharya, 2023). The datetime module deals with dates and times, for example by reading the current year, month, and day from a date object (Mohbey & Acharya, 2023).

Inside the assistant, those four libraries line up with the features almost one-to-one. Scheduling belongs to datetime, since a task's due date can be compared with today's date to decide what's overdue or due soon. The quote of the day comes from random, which picks one entry out of a list. Calculations go to math, and os organizes files and reports by creating and browsing folders. On the calculation side, if a report will take 47 minutes and the assistant works in 25-minute focus sessions, `math.ceil(47 / 25)` gives 2, while plain division gives 1.88 and rounding down would leave the user a session short.

`math.ceil()` is my pick for math. Mohbey and Acharya's (2023) example shows it returning 7 for 6.78954, so it rounds a number up to the next whole number, which is what the focus-session case needs because a partial session still takes a full slot on the calendar. For random, I'd use `random.choice()`, which returns one item from a list, so the daily quote takes a single line and adding a quote just means adding a string. The `datetime.now()` function returns the current date and time together (Python Software Foundation, n.d.-b), which lets the assistant time-stamp records and spot overdue tasks. For os, I'd use `os.mkdir()` to create a folder. It raises a `FileExistsError` when the name is taken and a `FileNotFoundError` if a parent folder is missing (Python Software Foundation, n.d.-c), and those two errors shape how I handle folders in Question 2.

## Question 2: Using datetime and os Together

The folder name starts with today's date, so datetime comes first. Calling `datetime.now()` gives back a datetime object, and `strftime()` turns it into text using a format string. In `"%Y-%m-%d"`, `%Y` is the four-digit year, `%m` the zero-padded month, and `%d` the zero-padded day, with the hyphens kept as plain characters (Python Software Foundation, n.d.-b). Year-month-day order also means the folders sort chronologically in an ordinary alphabetical listing. Following Mastrodomenico's (2022) advice to import only what's needed, the code imports just the datetime class, which is why the name appears twice: the module and the class inside it are both called datetime.

```python
from datetime import datetime

today = datetime.now()
folder_name = today.strftime("%Y-%m-%d")
print("Today's folder name:", folder_name)
```

Output:

```
Today's folder name: 2026-10-25
```

Creating the folder is the os module's job. The `os.mkdir()` function makes one folder, but it fails with a `FileExistsError` if the folder is already on disk (Python Software Foundation, n.d.-c), which would crash the assistant on its second launch of the day. So the code asks first with `os.path.exists()`, which returns True when the path already exists (Python Software Foundation, n.d.-d), and calls `os.mkdir()` only when it doesn't. The snippet rebuilds the same date string so it can run on its own.

```python
import os
from datetime import datetime

folder_name = datetime.now().strftime("%Y-%m-%d")   # same name built in the first snippet

if os.path.exists(folder_name):
    print(folder_name, "already exists, nothing to do")
else:
    os.mkdir(folder_name)
    print(folder_name, "created")
```

Output on the first run:

```
2026-10-25 created
```

Output when the same script runs again:

```
2026-10-25 already exists, nothing to do
```

Combined, the two libraries make a small daily-log feature. The `get_daily_log_folder()` function builds today's folder name with datetime, joins it to a base folder called `logs`, and creates the result with `os.makedirs()`. I used `makedirs` here because it also creates missing parent folders, so `logs` itself appears on the first run, and `exist_ok=True` stops it from raising an error when the folder is already there (Python Software Foundation, n.d.-c). That removes the need for a separate exists check. The returned path is saved in `log_folder`, which `write_log()` then uses as the location for the day's user log file. One limit is that the path is fixed at startup, so an assistant left running past midnight would keep writing to the old day's folder.

```python
import os
from datetime import datetime


def get_daily_log_folder(base_dir="logs"):
    """Return the path of today's log folder, creating it if needed."""
    today = datetime.now().strftime("%Y-%m-%d")
    folder_path = os.path.join(base_dir, today)
    os.makedirs(folder_path, exist_ok=True)
    return folder_path


# Save today's folder as the location for the daily user logs
log_folder = get_daily_log_folder()
log_file_path = os.path.join(log_folder, "user_log.txt")


def write_log(message):
    time_stamp = datetime.now().strftime("%H:%M:%S")
    with open(log_file_path, "a") as log_file:
        log_file.write(f"[{time_stamp}] {message}\n")


write_log("User opened the assistant")
write_log("User added a task: Submit Unit 8 discussion")
print("Daily logs are saved in:", log_folder)

with open(log_file_path) as log_file:
    print(log_file.read())
```

Output:

```
Daily logs are saved in: logs/2026-10-25
[20:05:54] User opened the assistant
[20:05:54] User added a task: Submit Unit 8 discussion
```

Running it a second time raised no error and added two more lines to the same file.

## Question 3: Object-Oriented Programming and the Assistant's Design

Encapsulation means a class keeps its data and the methods that use it together and shields that data from outside changes. As Mohbey and Acharya (2023) describe it, direct access is limited so that only an object's own methods change its variables, which prevents accidental changes. Abstraction hides the how and shows only the what: someone using a Task doesn't need to know how its status is stored, only that `mark_complete()` finishes it. Encapsulation is also what makes abstraction possible, since it is the means through which abstraction is achieved (Mohbey & Acharya, 2023). Reusability means writing the blueprint once and using it many times. A class can produce any number of objects, and inheritance lets a new class build on an existing one instead of starting from zero (Mohbey & Acharya, 2023).

Without these ideas, the assistant would be written in a procedural style, where a program is structured like a recipe of functions and code blocks that run one after another (Mohbey & Acharya, 2023). A task would end up as a name in one list, a date in another, and a status in a third, and any function could change any of them. If the team later decided to store status as a number instead of text, they'd have to hunt through every function that touched it. With a Task class, only the Task code changes, while the reminder, report, and quote features keep calling the same methods. Bugs are also easier to trace because status is only meant to change through `mark_complete()`. A future RecurringTask could start from Task instead of copying it.

The class below is deliberately minimal. A double underscore in front of `status` makes it private, the same technique the reading uses to hide its `__year` attribute, and the second object shows the same blueprint producing a separate task. The last lines try to read the hidden attribute from outside the class.

```python
class Task:
    def __init__(self, name):
        self.name = name
        self.__status = "Pending"      # private: only Task's own methods touch it

    def mark_complete(self):
        self.__status = "Completed"

    def get_status(self):
        return self.__status


homework = Task("Finish Unit 8 discussion")
reading = Task("Read the Unit 9 chapter")      # same blueprint, a second object

homework.mark_complete()
print(homework.name, "->", homework.get_status())
print(reading.name, "->", reading.get_status())

try:
    print(homework.__status)           # direct access from outside the class
except AttributeError as error:
    print("Blocked:", error)
```

Output:

```
Finish Unit 8 discussion -> Completed
Read the Unit 9 chapter -> Pending
Blocked: 'Task' object has no attribute '__status'
```

That's the same kind of `AttributeError` the reading's own example produces. Python's documentation calls the mechanism name mangling and says it exists mostly to avoid accidents, so a determined programmer can still reach the value as `_Task__status` (Python Software Foundation, n.d.-a). It protects a team from mistakes, but it isn't a security feature.

## Question 4: A Task Class with Attributes, Methods, and Objects

This version adds a due date and a rescheduling method to the Task class. The `__init__()` method is the constructor, which runs when an object is created and sets up its attributes, with `self` as the first argument (Mohbey & Acharya, 2023). Each attribute answers a question the assistant needs to answer about every task. The `name` says what the task is, so reminders and reports can show it. The `due_date` says when it's due, and storing it as a date object instead of a string means dates can be compared and sorted, which is what overdue checks depend on. The `status` says how far along the task is and starts as "Pending". It's private, as in Question 3, so it changes through a method.

```python
from datetime import date


class Task:
    def __init__(self, name, due_date, status="Pending"):
        self.name = name
        self.due_date = due_date
        self.__status = status

    def mark_complete(self):
        """Change the task's status to Completed."""
        self.__status = "Completed"

    def reschedule(self, new_due_date):
        """Move the task to a new due date."""
        self.due_date = new_due_date

    def get_status(self):
        return self.__status


task1 = Task("Submit Unit 8 discussion", date(2026, 10, 25))
task2 = Task("Review Unit 9 reading", date(2026, 10, 30))
task3 = Task("Practice Python classes", date(2026, 10, 28))

task1.mark_complete()
task3.reschedule(date(2026, 11, 2))

all_tasks = [task1, task2, task3]
pending = 0
for task in all_tasks:
    print(f"{task.name} | due {task.due_date} | {task.get_status()}")
    if task.get_status() == "Pending":
        pending += 1

print("Pending tasks:", pending)
```

Output:

```
Submit Unit 8 discussion | due 2026-10-25 | Completed
Review Unit 9 reading | due 2026-10-30 | Pending
Practice Python classes | due 2026-11-02 | Pending
Pending tasks: 2
```

Two methods do the work. The `mark_complete()` method sets the private status to "Completed". The `reschedule()` method takes a new date and replaces `due_date`, covering the everyday case of a task slipping to another day without deleting it and creating a new one. The `get_status()` method is a small helper that lets other parts of the app read the private value.

The code also creates three Task objects from one class. Mohbey and Acharya (2023) describe an object as an independent entity with its own state and set of behaviors, and the output shows that: completing task1 left task2 and task3 alone, and rescheduling task3 moved only its date, from October 28 to November 2. Keeping the objects in a list means one loop prints the whole report and counts the pending tasks, however many tasks exist. With separate variables for names, dates, and statuses, every new task would mean changes in several places. As objects, each task is one thing that carries its own data and behavior.

Modules and classes also work together. A module can define classes as well as variables and functions (Mohbey & Acharya, 2023), so the Task class could live in its own file, `tasks.py`, and the rest of the app could load it with `from tasks import Task`. I tried that import and it runs. That way the libraries handle jobs the assistant shouldn't reinvent, the class keeps each task's data in one place, and modules keep the pieces in separate files. The class is still basic, though. The `reschedule()` method accepts any date, including a past one, and nothing stops a mistyped status when a Task is created, so a next version should validate both.

## References

Mastrodomenico, R. (2022). *The python book*. John Wiley & Sons, Incorporated.

Mohbey, K. K., & Acharya, M. (2023). *Basics of python programming : A quick guide for beginners*. Bentham Science Publishers.

Python Software Foundation. (n.d.-a). *Classes*. Python 3 documentation. https://docs.python.org/3/tutorial/classes.html

Python Software Foundation. (n.d.-b). *datetime — Basic date and time types*. Python 3 documentation. https://docs.python.org/3/library/datetime.html

Python Software Foundation. (n.d.-c). *os — Miscellaneous operating system interfaces*. Python 3 documentation. https://docs.python.org/3/library/os.html

Python Software Foundation. (n.d.-d). *os.path — Common pathname manipulations*. Python 3 documentation. https://docs.python.org/3/library/os.path.html
