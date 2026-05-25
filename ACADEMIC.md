# L1 Licence Informatique
## Imperative Programming
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

### Linux basics
Definition:
  - A distro: One distribution of Linux with all that is needed to make a computer usable.
  - An operating system kernel: A program written in binary managing the hardware
  - A terminal: A window containing a shell.
  - A shell: A program written in binary sending commands typed by the user to the kernel.
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

#### Git basis
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
- `git merge <branch_name>`: Merge the branch with into your active branch.

#### Program: input → process → output
Definition: 
  - Program: A set of instructions that transforms input into output via a process.
  - Input: Data or signals received from the user, files, sensors, network, etc.
  - Process: Computation, decision-making, or transformation done by the program.
  - Output: The result produced by the program. Can be visible (screen, file) or invisible
  (system update, internal state).
  - Common mistakes: Confusing process vs output, thinking programs always show results, 
    ignoring multiple input sources.

#### Debugging: bugs and classic errors
Definitions:
- Bug: An error in a program that causes incorrect behaviors or crashes.
- Debugging: The process of finding and fixing bugs.

Types of bugs:
- Syntax bug: The code violate language rules -> makes the program crash / or don't run
  at all
- Logic bugs: The code runs but produce incorrect results (example, incorrect formula)
- Runtime bugs: Code crash while executing (calling a not declared function, dividing 
  by zero, wrong type, etc...)


#### Sequential execution
Definition: 
Code statements run one after the another top to bottom, not simultaneously.
Loops and conditions can change the natural top-down flow but otherwise the execution is
sequential.
Variables and functions must be defined before calling them.


#### Python: syntax and types
##### Numbers: int, float
int: integer -> whole number (3, -2, etc)
float: float -> decimals (2.63, -1.98, etc)

Python automatically switch between int and float when needed. Can do standard arithmetics operations on them.

Operator precedence is applied in Python. 

Mixing int and float in loops or conditions can produce unexpected effects and should be avoided.

Float is a binary approximation of a decimal number so small errors are expected.
So we should not use exact comparison on float but instead use tolerance.

For exact decimal arithmetic (e.g., money), Python provides the decimal module.

We can truncate a float into an integer with `int(3.9)` -> Return 3
We can create a float from an integer with `float(3)` -> Returns 3.0
