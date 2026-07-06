# L1 Licence Informatique
## Prerequisites
### Linux basics
Definition:
  - A distro: One distribution of Linux with all that is needed to make a computer 
    usable.
  - An operating system kernel: A program written in binary managing the hardware
  - A terminal: A window containing a shell.
  - A shell: A program written in binary sending commands typed by the user to the 
    kernel.
  - Bash (Bourn Again Shell): Default shell on most Linux systems.
  - Current working directory: The directory you are currently in.
  - a flag: An option for a Linux command
  - stdout: The screen or the composant acting as an output for a shell.

#### Navigation
Main commands: 
  - `pwd` (Print Working Directory): Show were you are.
  - `ls` (List): Show what is in the current directory.
  - `cd` (Change Directory): Move you somewhere else

Main `cd` commands:
  - `cd code`: Go into the code folder.
  - `cd ..`: Go up one level (to the parent directory)
  - `cd ~`: Go to your home directory
  - `cd /`: Go to the root of the file system
  - `cd -`: Go to the previous directory you were in. 

Main `ls` commands:
  - `ls -l`: List with details (permissions, size, date)
  - `ls -a`: List including hidden files

#### File management
Main commands:
  - `mkdir` (Make Directory): Create a folder
  - `cp` (Copy): Copy a file or a folder
  - `mv` (Move): Move or rename a file/folder
  - `rm` (Remove): Delete permanently file/folder
  - `less`: Call less pager and allow to read a file

Main `mkdir` commands:
  - `mkdir notes`: Create a folder called 'notes'
  - `mkdir -p root_folder/sub_folder/sub_sub_folder`: Create nested folder in one shot.

Main `cp` commands:
  - `cp file.txt backup.txt`: Copy a file
  - `cp -r folder/ folder_copy/`: Copy an entire folder (need `-r` for recursive)

Main `mv` commands:
  - `mv old.txt new.txt`: Rename a file
  - `mv file.txt ../`: Move up the file by one directory
  - `mv file.txt folder/`: Move a file or folder to an other folder

Main `rm` commands:
  - `rm file.txt`: Delete a file
  - `rm -r folder/`: Delete a folder an everything inside

#### The manual
Linux comes with a built-in manual, those are the commands associated with it:
  - `man cd`: Tell what the command does, its flags and an example
  - `man -k keyword`: Return all commands containing the keyword in their page.

man use the "less" pager

#### Pipes and redirection
By default, command prints its output to the screen, pipes and redirections allow you to
redirect the output elsewhere.

Main commands:
- `|` (pipe): Sends the output of one command as the input of the next
- `>` (redirection): Sends the output into a file (overwrite it) instead of the screen
- `>>`(appending): Send the output into a file appending it instead of the screen
- `<` (input): Use file content as input for a command

Common associations:
- `ls | grep ".py"`: List only files containing `.py` in their name
- `echo "hello" > file.txt`: Write "hello" into `file.txt` (overwrites)
- `echo "world" >> file.txt`: Append "world" to `file.txt`
- `cat file.txt | wc -l`: Count the number of lines in a file

#### Commons traps
- `mv` is also the rename function
- `rm` is permanent
- Forgetting `-r` on `cp` or `rm` cause an error
- `man man` is valid, the manual as a manual page
- Pipes connect only commands, not files
- `grep` is case sensitive by default, use `grep -i` for case insensitive
- `>` silently overwrite without confirmation

### Pagers
Definitions:
  - a pager: An utility program used to view the content of a text file or command
    command output one page at a time.

Common types of pager:
  - Less: The current standard
  - More: The old version of less

Shared commands:
  - `q` (Quit): Quit the pager
  - `h` (Help): Show all the commands of the pager
  - `Space`: Scroll down one page
  - `b` (Back): Go back to the previous page
  - `Enter`: Go one line down
  - `y` or `k`: Go one line up
  - `g`: Go to the beginning of the file
  - `G`: Go to the end of the file
  - `-N`: Allow to see line's numbers
  - `26g`: Go to the line 26
 

#### Less
Features:
  - Can go forward and backward
  - Load only what you see
  - Can search through the file with `/`

Commands:
  - `-i`: Toggle case insensitive search for all following search, to disable, type it 
    again
  - `/pattern`: Search for the word "pattern"
  - `?pattern`: Search backward for the word "pattern"
  - `n`: Find the next occurrence of a search
  - `N`: Find the previous occurrence of a search

#### More
Features:
  - Only goes forward
  - Load the whole file at once
  - Only limited search ability


### Git
Git is a version control system taking snapshot of your projects at given time so you
can go back to any previous state.

Definitions:
  - A repository (repo): Project folder tracked by Git.
  - A remote: A copy of your repository hosted on a server.

When using Git, your file could be in either of this three zone:
- Working directory
- Staging area (`git add`)
- Repository (history (`git commit`))

#### Git basis[]()
Main commands:
  - `git init`: Create a new repo in the current folder
  - `git status`: See what is changed and what is staged
  - `git add file.txt`: Stage one file
  - `git add .`: Stage all changed files
  - `git commit`: Enter Vin or a text editor where you can write a commit message
  - `git log`: See the full history of commits (use "less" pager)

When using `git init`, it create a .git folder containing all your history, if you
delete it, you lose your history.

You need to commit a change for it to be saved, staging it only allow it to be committed
later.

Always make clear commit message so you can easily search through your history.

#### Git remote
Git only save on your machine, to connect your repository to the world (Github, 
university, etc), you need to use `push` and `pull` commands.

The default remote is conventionally named `origin`

Main commands:
  - `git remote add origin <url>`: Link your local repo to a remote for the first time.
    "origin" is a conventional name for a remote.
  - `git push <remote_name> <branch_name>`: Send your branch commits to the remote
  - `git pull origin <branch_name`:	Fetch + merge remote commits into your local branch
  - `git clone <url>`:	Download an entire remote repo to your machine

#### Git ignore
Git saves all the files in the root folder. To avoid saving compromising things and
putting it on GitHub, we should create a `.gitignore` file.

You can enter text enter the name of the files you don't want to save in your git in
here. As a rule of thumb, any large files or personal one shouldn't be uploaded.

Example of a .gitignore file:
```
# The folder where is your environnement (will be recreated using `requirements.txt` or
  pyproject.toml on python)
.venv/

# Personal folder, not useful to upload
.vscode/
*.log
*.code-workspace
*egg-info/
.pytest_cache/
__pycache__/
```

A file already added to a repository will not be suppressed just by updating the 
.gitignore

#### Git branches
Branches are independent lines of development. One can be modified without changing
another. It is very useful to implement new features while keeping a working program.

The default branch is named `main`. You can create an exact copy of it by creating a new
branch from it. Then merge it back into `main`. 

Mains commands:
- `git branch`: List all branches
- `git branch <parent/child>`: Create a branch named `parent/child` from the current
  active branch (the `/` is just cosmetic, there is no parent / child link)
- `git switch <branch_name>`: Define the branch as the active one.
- `git merge <branch_name>`: Merge the branch named into your active branch.


## Imperative Programming: Python concepts
### Fundamental concepts
#### Program: input → process → output
Definition: 
  - Program: A set of instructions that transforms input into output via a process.
  - Input: Data or signals received from the user, files, sensors, network, etc.
  - Process: Computation, decision-making, or transformation done by the program.
  - Output: The result produced by the program. Can be visible (screen, file) or 
    invisible
  (system update, internal state).
  - Common mistakes: Confusing process vs output, thinking programs always show results, 
    ignoring multiple input sources.

##### Debugging: bugs and classic errors
Definitions:
- Bug: An error in a program that causes incorrect behaviors or crashes.
- Debugging: The process of finding and fixing bugs.

Types of bugs:
- Syntax bug: The code violate language rules -> makes the program crash / or don't run
  at all
- Logic bugs: The code runs but produce incorrect results (example, incorrect formula)
- Runtime bugs: Code crash while executing (calling a not declared function, dividing 
  by zero, wrong type, etc...)


##### Sequential execution
Definition: 
Code statements run one after the another top to bottom, not simultaneously.
Loops and conditions can change the natural top-down flow but otherwise the execution is
sequential.
Variables and functions must be defined before calling them.


### Python: syntax and types
#### Numbers: int, float
int: integer -> whole number (3, -2, etc)
float: float -> decimals (2.63, -1.98, etc)

Python automatically switch between int and float when needed. Can do standard 
arithmetics operations on them.

Operator precedence is applied in Python. 

Mixing int and float in loops or conditions can produce unexpected effects and should be 
avoided.

Float is a binary approximation of a decimal number so small errors are expected.
So we should not use exact comparison on float but instead use tolerance.

For exact decimal arithmetic (e.g., money), Python provides the decimal module.

We can truncate a float into an integer with `int(3.9)` -> Return 3
We can create a float from an integer with `float(3)` -> Returns 3.0

#### Booleans
Definition: 
  - Truthiness: A concept that evaluate if an object is `True` or `False`.

Bools are used in every conditions written in Python. They have two values: `True` or 
`False`.

A boolean (bool) is a subclass of integers. `True` behaves as `1` and `False` as `0`. 
For example `isinstance(True, int)` is truthy. 
`True == 1` and `False == 0` are both truthy as well.
However `bool("0")` is also truthy because the string is not empty.

The only falsy values (when NOT in another class) are:
  - `0`
  - `0.0`
  - `""`
  - `[]`
  - `{}`
  - `()`
  - `None`
  - `False`

#### String
##### String basics
Definition: 
  - A string: (str) An ordered immutable sequence of characters.
  - Immutable: Once created, can not be modified.
  - Ordered: Each characters sits at a numbered position named index.
  - Half-open interval: The interval include that starting borne but exclude the ending
    one. The standard annotation is `[start, stop)`.

Indexes starts at 0 from the left to -1 from the right
You can slice any types that are indexables. It allow you to extract information from
specifics indexes.

To slice:
`random_string[<start>, <stop>, <step>]`
- start: Include the index entered, default is 0
- stop: Exclude the index entered, default is -1
- step: Increment, default is 1 (if negative, from right to left). Can be any non zero
  integer. If zero, raise a ValueError.

Out of ranges slices do not raise an error while out of range indexed raise an
IndexError. 

To only change one character in a string: 
`random_string = random_string[:3] + "N" + random_string[4:]`

##### String method
Definitions:
  - A method: A built-in function that is called using a dot notation.

Method does not change the original string but returns a new one instead so you need to
reassign the result or use it immediately.

Main commands (using variable named `test` containing a string):
  - `test.upper()`: Make all characters upper case.
  - `test.lower()`: Make all characters upper case.
  - `test.capitalize()`: Capitalize the first letter of the string.
  - `test.title()`: Capitalize the first letter of each words.
  - `test.strip()`: Remove trailing and leading white spaces.
  - `test.replace('old', 'new')`: Replace old occurrences of `old` by `new` (can add the 
    number of occurrence to replace, default is all)
  - `test.count('old')`: Count all occurrences of `old`.
  - `test.find('old')`: Return the index of the first letter of the word found, return
    `-1` if word is not found.
  - `test.startswith('old')`: Return a bool.
  - `test.endswith('old')`: Return a bool.
  - `test.split('old')`: Return a list of separated strings.

#### Variable
##### Variable assignment
In python, a variable is a reference that point to an object in memory, it is not the
objet itself.

Using `=` make a label point to an object but does not copy it.

Python is dynamically typed, a variable has no fixed type, the object it point to does.

```python
# Basic assignment
score = 42          # label 'score' points to the int object 42

# Dynamic typing — the label can be repointed to any type
score = "forty-two" # now points to a str object — valid in Python

# Augmented assignment
score = 10
score += 3   # equivalent to score = score + 3  → 13
score *= 2   # equivalent to score = score * 2  → 26
score //= 4  # equivalent to score = score // 4 → 6

# Multiple assignment
x = y = z = 0       # all three labels point to the same object 0

# Tuple unpacking (multiple assignment from a sequence)
a, b = 10, 20       # a → 10, b → 20
a, b = b, a         # swap — no temporary variable needed
```

Naming rules for variables:
  - Must start with a letter or underscore _
  - Can contain letters, digits, underscores but no spaces, no hyphens
  - Case-sensitive: Score and score are two different variables
  - Cannot be a reserved keyword: if, for, while, True, False, None, and, or, not… etc.
  - Convention (PEP 8): use snake_case for variables (my_score, not myScore)

Common traps:
  - Augmented assignment on immutable types still creates a new object. `x += 1`
  - Keywords cannot be used as variable names.
  - Augmented assignment on immutable tye still create a new object 

##### Variable scope
**General case**
The scope is where your variable is visible and accessible. If it is not well defined,
it can cause bugs like `NameError` or overwrite another variable. 

Python resolve variables by searching though scope in this order known as the 
`LEGB rule`:
1) Local
2) Enclosing
3) Global
4) Built-in

The search stop at the first match found

**Global keyword**
A variable outside a function is qualified as `global`.
A variable inside the outer function of a nested functions is called `enclosing`.
One inside a function called `local`.

To use a global variable inside a function, you can use the `global` keyword, however it 
is considered bad practice in production code and should be done sparingly:

```python
# Global scope
counter = 0 

def increment():
  # Declare intent to use the global variable
  global counter
  counter += 1

# counter in the global scope == 1
```
`built-in` functions have their own scope and are available everywhere

The `global` keyword is only needed when assigning, not reading.

**nonlocal keyword**
You can use `nonlocal` keywords inside an inner nested function to use the variable from 
the outer scope of the function.

```python
test_1 = 1

def outer():
    global test_1
    test_1 = 0
    test_2 = 3

    def inner():
        nonlocal test_2
        test_2 = 5
    
    inner()
    return test_1, test_2

print(outer())
```

### Operations
#### Comparison
Definition:
  - Comparison operator: In Python, a symbol used to test the relationship between two 
  entities, resulting in a strict Boolean evaluation (True or False).

##### Equality and inequality
Main commands:
  - `==`: Evaluates if two values are exactly equal.
  - `!=`: Evaluates if two values are strictly not equal.

Common traps:
  - Comparing identical characters stored as completely different data types (e.g., 
  `10 == "10"` evaluates to `False`).
  - Comparing calculated decimals with == (e.g., `0.1 + 0.2 == 0.3` evaluates to `False` 
  due to machine-level memory architecture).

##### Value Comparisons (Order Operators)
Definition:
  - Order Operators: A subset of comparison operators that evaluate the mathematical or 
  lexicographical (alphabetical) ranking between two values.

Main commands/syntax:
  - `<` / `>`: Strict inequalities. Evaluates to `True` only if the values are 
  distinctly different and ordered correctly.
  - `<=` / `>=`: Non-strict (inclusive) inequalities. Evaluates to `True` if the 
  condition is met OR if the values are exactly equal.

Common traps:
  - Strings are evaluated by raw ASCII/Unicode values, meaning uppercase letters 
  evaluate as "less than" lowercase letters (e.g., `"Zebra" < "apple"` is `True`).

##### Memory References (Identity Operators)
Definition:
  - Identity Operators: Operators that evaluate whether two variables point to the exact 
  same physical object (memory address/reference), regardless of their content.

Main commands/syntax:
  - `is`: Evaluates to `True` if both variables reference the exact same object in 
  memory.
  - `is not`: Evaluates to `True` if the variables reference different objects in 
  memory.

Common traps:
  - Python reuses memory for small integers (0-256) for optimization, causing 
  unpredictable `is` evaluations for numbers. Never use `is` for integers.
  - Assuming copies share identity. Creating `list_b = list(list_a)` makes identical 
  content (`==` is True) but distinct objects (`is` is False). Modifying one will not 
  affect the other.
  - Using `== None` is academically discouraged and potentially unsafe due to custom 
  object overrides. The formal PEP 8 standard dictates always using `is None` to check 
  for null values.

##### Chained Comparisons
Definition:
  - Chained Comparisons: A Python syntax feature allowing multiple comparison operators 
  to be linked continuously (e.g., `x < y <= z`) to evaluate ranges directly.

Main commands/syntax:
  - `a < b < c`: Syntactic sugar translated internally by the interpreter to 
  `(a < b) and (b < c)`.

Mechanics:
  - Short-circuit Evaluation: The interpreter evaluates the chain from left to right. If 
  any condition evaluates to `False`, the system instantly stops checking the rest of 
  the chain to save CPU cycles.

Common traps:
  - Attempting to chain comparisons in strictly typed languages (C/Java) evaluates the 
  first pair to a literal boolean (`1` or `0`), breaking the math on the second pair.
  - Chaining mathematically opposing operators (e.g., `a < b > c`) is valid syntax but 
  violates readability standards; chains should always represent a continuous range.
  - A function placed in the middle of a chain (e.g., `a < func() < b`) is strictly 
  evaluated only *once*, unlike using manual `and` operators where the function would 
  execute twice.

#### Logical operators
##### The `not` Operator (Logical Negation)
**Definition:**
- Logical Negation: A unary operator (requiring only one value) that performs an
absolute inversion of a Boolean state. `True` becomes `False`, and `False` becomes 
`True`.

**Main mechanics/syntax:**
`not [condition]`: Flips the evaluated Boolean result of the condition.
`if not [variable]:`: The standard, Pythonic (PEP 8) way to check if a value is `False`, 
empty, or null.

**Common traps:**
- The Redundancy Trap: Writing `if not is_admin == True:`. This wastes processing power 
and violates academic formatting. The correct syntax is `if not is_admin:`.
- The Bitwise Trap: Using the tilde `~` instead of `not`. `~` manipulates binary 1s and 
0s at the hardware level, while `not` is strictly for Boolean logic.
- The Precedence Trap: Misunderstanding that `not` is evaluated *after* comparison 
operators but *before* `and`/`or`. For example, `not 5 > 10` is evaluated as 
`not (5 > 10)` -> `not False` -> `True`.

##### The `and` Operator (Logical Conjunction)
**Definition:**
- Logical Conjunction: A binary operator that evaluates to `True` strictly if both the 
left operand AND the right operand are `True`. If either side is `False`, the entire 
expression is `False`.
- Binary Operator: An operator that requires exactly two complete, independent 
expressions to evaluate (one on the left, one on the right).

**Main mechanics/syntax:**
`[condition_A] and [condition_B]`: Evaluates both conditions independently before 
determining the final Boolean state.

**Common traps:**
- The Human Language Trap: Writing `if a == b and c:` instead of explicitly writing 
`if a == b and a == c:`. 
- The Binary Syntax Error: Writing `if score > 10 and < 50:`. The right side must be a 
fully complete expression (e.g., `score < 50`).
- The Bitwise Trap: Using `&` instead of `and`. `&` is for binary math (1s and 0s) and 
will break logical evaluations.

##### The `or` Operator (Logical Disjunction)
**Definition:**
- Logical Disjunction: A binary operator that evaluates to `True` if **at least one** of 
its independent operands evaluates to `True`. It strictly returns `False` only if both 
sides evaluate to `False`.
- Inclusive OR: In computer science, `or` allows for both conditions to be true 
simultaneously, unlike the spoken human language "exclusive or" (XOR).

**Main mechanics/syntax:**
`[condition_A] or [condition_B]`: Evaluates the left and right conditions independently. 
If either is truthy, the statement passes.

**Common traps:**
- The Human Language Syntax Trap: Writing `if target == "A" or "B":`. The compiler 
evaluates `"B"` independently. Since `"B"` is a non-empty string, it is inherently 
`True`, causing the `if` statement to always trigger. Explicit variables are required: 
`if target == "A" or target == "B":`.
- The XOR Trap: Assuming `or` will fail if *both* conditions are met. If you need 
strictly one or the other (but not both), you must use the exclusive-or operator 
(`^`), not `or`.
- The Bitwise Disjunction Trap: Using the pipe symbol `|` instead of `or`. `|` 
manipulates binary numbers at the hardware level and will corrupt standard logical 
evaluations.

##### Truthy/Falsy values & Short-Circuiting
**Definition:**
- Truthy/Falsy: The inherent Boolean state of any Python object. Only `0`, `""` (empty 
string), `[]` (empty list/data structures), and `None` evaluate to `False`. Absolutely 
everything else evaluates to `True`.
- Short-Circuit Evaluation: An optimization where logical operators (`and`, `or`) stop 
evaluating left-to-right the exact millisecond the final logical outcome is 
mathematically certain.
- The Return Value Secret: `and`/`or` do not return the Boolean words `True` or `False`. 
They return the literal value of the object that caused the evaluation to stop.

**Main mechanics/syntax:**
`x = a or b`: Returns the first Truthy value it finds. (Often used for setting default 
fallbacks).
`y = a and b`: Returns the first Falsy value it finds. (If all are Truthy, it returns 
the very last value).

**Common traps:**
- The Boolean Assumption Trap: Assuming a logical operation will output `True`/`False`. 
If you write `result = "Data" and "Admin"`, the variable `result` holds the string 
`"Admin"`. 
- The Falsy Zero Trap: Using implicit boolean checks (e.g., `if user_score:`) when `0` 
is a valid, expected piece of data. Because `0` is Falsy, the `if` block will fail. 
You must explicitly check `if user_score is not None:`.

### Control structures
#### Conditions : `if`, `elif`, `else`

**Conditional control flow** : A decision-making structure that execute specific blocks of code based on truth value of Boolean expression. It flow sequentially until a `True` condition is met.

**Complexity**:
- Time: O(N) where N is the number of conditions evaluated
- Space: O(1)

**Main commands**:
- `if` execute the indented code bloc below if `True`
- Same for `elif` but can be chained after an `if` statement and will only be executed if `if` is not `True` 
- `else` will execute its code bloc only if above `if` and `elif` are not executed
- `elif` and `else` can be omitted.

**Logic**:
- You can enclose multiple `if` statements one inside the other
- Most critical conditions must be evaluated first
- `if` / `elif` are used only when only one action can be accomplished at a time (mutually exclusive)
- Separate if blocs only if all actions can be accomplished at the same time (non-mutually exclusive)

Common traps:
- Using `elif` before an `if` statement = `SyntaxError`
- Placing low-priority or broad condition before high priority and specifics ones.


#### Loops: `for`, `while`
##### Exercises : 
Consider these two methods to make an agent move a set number of times:

**Approach A:**

Python

```
steps = 0
while steps < 100:
    move()
    steps += 1
```

**Approach B:**

Python

```
for i in range(100):
    move()
```

**The Challenge:**

1. **Big O Rigor:** Determine the Time Complexity of _both_ approaches in terms of $N$ (where $N$ is the target number of steps).
    
2. **Logic Puzzle:** Imagine a new scenario where your agent must keep moving forward _until it detects a wall_. You do not know how far away the wall is. Which loop structure (`while` or `for`) is logically and syntactically required for this behavior, and why?

**Answer**
1. 
	A.  
	- Time :  O(2<sup>N</sup>)
	- Space : O(N)
	B.
	- Time : O(N)
	- Space : O(1)
2. `while` because the loop must continue until a condition is met but `for` loop are predefined in length

**Correction**
1. 
	A.
	- Time : O(N) because it grows linearly
	- Space : O(1) 



##### Lesson
Loops allow you to execute a sequence of instructions multiple times in a row.

**Complexity:** 
	- Time : O(N)
	- Space : O(1)

Two types of loop:
	- `for` : definite iteration = execute a defined number of time
	- `while` : indefinite iteration = execute until a condition is met

Common traps:
	- Infinite iterations with the `while` if the condition is not updated
	-  Missing by one in the `while` and `for` loops


##### Exercise
**Question**
Imagine an agent inside a `while` loop that runs $N$ times. Inside that loop, the agent evaluates a hierarchical `if/elif/else` block consisting of $C$ different conditions to decide its next move.

**Your Task:**

1. What is the combined Time Complexity of this integrated system in terms of $N$ and $C$?
    
2. In the context of coding self-improving simulations, why is it mathematically critical to keep $C$ (the number of rules an agent checks per step) as small and prioritized as possible?

**Answer**
while:
	- time : O(N)
	- space : O(1)

if:
	- time: O(1)
	- space: O(1)

1. Time = O(N<sup>C</sup>)
2. Because it will take exponentially more time to process the entire while loop

**Correction**
1. Time : O(N*C)
2. Because as C grow it will linearly take more time for N to compute

### Functions
#### Functions parameters and `return`
**definition: ** 
- A function is a named reusable block of code that perform a specific task

You define a function with the `def` keyword and the choosen name for the function, you can then call it as many time as you want with specifics parameters.

You can use the `return` keyword at the end of your function to send it at the line where the function is called. If you don't capture the result, it is discarded.

Exemple: 
```python
def multiplication_by_ten(number):
  return number * 10

print(multiplication_by_ten(20))
# 200
```
