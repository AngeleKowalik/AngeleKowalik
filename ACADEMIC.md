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

  - [ ] Booleans: True/False
  - [ ] Strings: text manipulation
  - [ ] Variables, assignment, scope
- [ ] Operations
  - [ ] Arithmetic: +, -, *, /, %, **
  - [ ] Comparisons: ==, !=, >, <, >=, <=
  - [ ] Logical: and, or, not
- [ ] Control structures
  - [ ] Conditions: if, elif, else
  - [ ] Loops: for, while
- [ ] Functions
  - [ ] Define a function, parameters, return
- [ ] Collections
  - [ ] Lists, tuples, dictionaries, sets
- [ ] Notion of simple algorithms
  - [ ] Sum, max, min, linear search
  - [ ] Introduction to sorting: bubble, insertion
- [ ] Modules and libraries
  - [ ] math, random, os

### 2. Mathematics for Computer Science
- [ ] Revision of the basics
  - [ ] Integers, rationals, decimals
  - [ ] Fractions, powers, square roots
- [ ] Basic logic
  - [ ] AND, OR, NOT
  - [ ] Truth tables
- [ ] Notions of matrices and vectors (2D)
  - [ ] Addition, multiplication
- [ ] Basic probability and statistics
  - [ ] Mean, median, variance, standard deviation
  - [ ] Elementary probability (dice, drawing)

### 3. Beginner Data Structures

- [ ] Lists and arrays: index, slicing, manipulations
- [ ] Stacks: LIFO
- [ ] Queues: FIFO
- [ ] Dictionaries (hash map)
- [ ] Sets: operations (union, intersection, difference)

### 4. Introduction to the Web

- [ ] HTML: basic structure
- [ ] CSS: styling
- [ ] Notion of client/server

### 5. S1 Synthesis Project

- [ ] Simple project combining Python + logic + collections
- [ ] Example: mini calculator, grade manager

---

## Semester 2: Deepening and First Advanced Concepts

### 1. Recursive Algorithms and Advanced Programming

- [ ] Recursion: factorial, Fibonacci
- [ ] Advanced search and sorting
- [ ] Simple complexity analysis: O(n), O(log n)
- [ ] Error handling: try/except
- [ ] File reading and writing

### 2. Fundamentals of Discrete Mathematics

- [ ] Sets, relations, formal functions
  - [ ] Subsets, union, intersection, complement
  - [ ] Relations: reflexive, symmetric, transitive
  - [ ] Functions: injective, surjective, bijective
- [ ] Introduction to combinatorics: permutations, combinations
- [ ] Reasoning by induction
  - [ ] Simple proofs
- [ ] Graphs: formal definition (nodes/edges)
- [ ] Introduction to modular arithmetic
- [ ] Basic concepts in number theory (division, GCD, LCM)

### 3. Introduction to C and Memory Management

- [ ] Basic C syntax
  - [ ] Variables, types, operators
- [ ] Pointers
  - [ ] malloc / free
- [ ] Arrays and structures
- [ ] Stack vs heap
- [ ] Segmentation fault

### 4. Introduction to Databases

- [ ] Concepts: table, row, column
- [ ] Primary key / foreign key
- [ ] Basic SQL: SELECT, INSERT, UPDATE, DELETE
- [ ] Simple projects: create and query a table

### 5. S2 Synthesis Project

- [ ] Project combining Python/C + structures + logic
- [ ] Example: contact manager with file storage + CRUD operations

---

# L2: Deepening and Transition to Structured and Object-Oriented Programming

## Semester 3 (S3): Advanced Foundations and Formal Logic

### 1. Algorithms and Complexity

- [ ] Advanced algorithms
  - [ ] Quicksort, Merge sort
  - [ ] Binary search and search in complex structures
  - [ ] Complexity analysis: O(n), O(n²), O(log n)
- [ ] In-depth recursion
  - [ ] Factorial, Fibonacci, Tower of Hanoi
  - [ ] Recursion on lists, trees and graphs
- [ ] Introduction to algorithmic optimization
  - [ ] Notion of memory and time
  - [ ] Space/time trade-off

### 2. Fundamentals of Object-Oriented Programming (OOP)

- [ ] Fundamental concepts
  - [ ] Classes and objects
  - [ ] Attributes and methods
  - [ ] Encapsulation
  - [ ] Inheritance and polymorphism
- [ ] Project organization
  - [ ] Modules and packages
  - [ ] Simple program design
- [ ] Practical exercises
  - [ ] Example: Animal class with Dog and Cat subclasses
  - [ ] Managing collections of objects

### 3. Advanced Discrete Mathematics

- [ ] Sets, relations, functions (revision + deepening)
  - [ ] Equivalence relations and partitions
  - [ ] Partial orders and chains
- [ ] Formal graphs
  - [ ] Directed and undirected graphs
  - [ ] Degree, path, cycle
  - [ ] Adjacency matrices
- [ ] In-depth modular arithmetic
  - [ ] Congruences, modulo n
- [ ] Basic number theory
  - [ ] Divisibility, GCD, LCM
  - [ ] Prime numbers
- [ ] Reasoning by induction
  - [ ] Simple and double induction proofs

### 4. Formal Logic

- [ ] Propositional logic
  - [ ] Syntax and semantics
  - [ ] Complete truth tables
  - [ ] Normal forms: CNF, DNF
- [ ] First-order logic
  - [ ] Variables, quantifiers ∀, ∃
  - [ ] Predicates and functions
- [ ] Formal proofs
  - [ ] Natural derivation, resolution
  - [ ] Simple examples: proving properties on sets or graphs

### 5. Computer Architecture (Practical Introduction)

- [ ] Binary representation of numbers
  - [ ] Signed integers (two's complement)
  - [ ] Floating point numbers (IEEE 754)
- [ ] CPU
  - [ ] Registers, ALU, pipeline
- [ ] Memory
  - [ ] Cache, RAM, virtual memory
- [ ] Simple assembler
  - [ ] Basic instructions: MOV, ADD, SUB

### 6. S3 Synthesis Project

- [ ] Example: Implementation of a small graph manager
  - [ ] Representation by lists and matrices
  - [ ] Functions for DFS/BFS traversal
  - [ ] Analysis of paths and cycles
  - [ ] Using OOP to organize the code

---

## Semester 4 (S4): Systems, Networks, AI and Practical Applications

### 1. Graph Algorithms

- [ ] Traversal: DFS, BFS
- [ ] Shortest path: Dijkstra (basic concept)
- [ ] Trees and forests
- [ ] Applications: networks, maps, social relations

### 2. Systems

- [ ] Processes and threads
  - [ ] Thread creation and termination
  - [ ] Synchronization: mutex, semaphores
  - [ ] Classic problems: producer-consumer
  - [ ] Deadlock and prevention
- [ ] Memory management
  - [ ] Static and dynamic allocation
  - [ ] Stack vs heap
  - [ ] Segmentation and fragmentation

### 3. Graphical User Interfaces (GUI)

- [ ] Concepts: window, widgets, events
- [ ] Python: Tkinter or PyQt (basics)
- [ ] Events: clicks, keyboard input
- [ ] Simple projects: mini-calculator, graph visualization

### 4. Introduction to Artificial Intelligence

- [ ] Fundamental concepts
  - [ ] What is a model?
  - [ ] Dataset, features, labels
- [ ] Simple algorithms
  - [ ] Linear regression
  - [ ] Supervised classification
  - [ ] Clustering: K-means
- [ ] Simulation and evolutionary algorithms
  - [ ] Population of solutions, mutation, selection
  - [ ] Fitness, evolution of a solution over time

### 5. Networks (Lower Layers)

- [ ] Basic concepts
  - [ ] IP, MAC address
  - [ ] Protocols: TCP, UDP, HTTP
- [ ] Simple socket programming in Python
- [ ] Client/server and communication
- [ ] Ping, connectivity tests

### 6. Databases

- [ ] SQL: complex queries
  - [ ] JOIN, subqueries
  - [ ] Index and query optimization
- [ ] Introduction to NoSQL databases
  - [ ] MongoDB: documents and collections

### 7. Applied Probability

- [ ] Conditional probabilities
- [ ] Law of large numbers (concept)
- [ ] Simple random variables
- [ ] Application: simulation, simple AI

### 8. S4 Synthesis Project

- [ ] Example 1: Multi-agent simulation
  - [ ] Agents interact in an environment
  - [ ] State tracking in a database
  - [ ] Visualization of results with graphs
- [ ] Example 2: Small network + database project
  - [ ] Server that stores client information
  - [ ] Statistical analysis and visualization

---

# L3: Specialization and Professional Development

## Semester 5 (S5): Advanced Design and Consolidation

### 1. Networks: Upper Layers

- [ ] OSI vs TCP/IP model
  - [ ] Application, presentation, session
- [ ] Common protocols
  - [ ] HTTP/HTTPS, FTP, SMTP, DNS
- [ ] Socket management
  - [ ] Multiple clients, simultaneous communication
- [ ] Routing and subnets
  - [ ] Notion of network mask and CIDR
- [ ] Basic network security
  - [ ] SSL/TLS, simple encryption, authentication

### 2. Advanced Object-Oriented Design

- [ ] Simple design patterns
  - [ ] Singleton, Factory, Observer
- [ ] Exception handling in OO projects
- [ ] Modularity and packaging
- [ ] Unit tests
  - [ ] unittest in Python or Java/C++ equivalent

### 3. Advanced Logic

- [ ] Complete first-order logic
  - [ ] Quantifiers ∀ and ∃, substitution rules
  - [ ] Proofs by resolution and derivation
- [ ] Combinational logic
  - [ ] Applications to program verification
  - [ ] Examples: logic circuits, algorithm validation

### 4. Advanced Databases

- [ ] Relational design
  - [ ] Normalization (1NF → 3NF)
  - [ ] Integrity constraints
- [ ] Advanced queries
  - [ ] Complex joins, aggregations, transactions
- [ ] NoSQL databases
  - [ ] Indexing, performance
  - [ ] Example project: mini-DBMS or data management for simulation

### 5. Systems: Processes and Synchronization

- [ ] Advanced processes and threads
  - [ ] Semaphores, mutex, conditions
  - [ ] Inter-process communication
  - [ ] Deadlock: detection and prevention

### 6. Statistics for Computer Science

- [ ] Discrete and continuous random variables
- [ ] Conditional probabilities and Bayes
- [ ] Applications in machine learning
  - [ ] Model evaluation: precision, recall, F1-score

### 7. S5 Synthesis Project

- [ ] Example: simulated multi-agent system with database storage + graphical interface
- [ ] Example: mini network server with concurrent processing and statistical visualization

---

## Semester 6 (S6): Expertise, Optimization and Final Project

### 1. Compilation

- [ ] Lexing, parsing
- [ ] Syntactic analysis: abstract syntax trees (AST)
- [ ] Semantic analysis
- [ ] Code optimization
- [ ] Machine code or bytecode generation
- [ ] Compilation error handling
- [ ] Introduction to modern compilers

### 2. Introduction to Computer Security

- [ ] Basic concepts
  - [ ] Confidentiality, integrity, availability
  - [ ] Authentication and authorization
- [ ] Simple cryptography
  - [ ] Symmetric and asymmetric encryption
- [ ] Classic vulnerabilities
  - [ ] SQL injection, buffer overflow, XSS

### 3. Mobile Application Development

- [ ] Android/iOS environments
- [ ] Concepts: UI, events, local storage
- [ ] Connection with server and database
- [ ] Simple project: tracking or simulation application

### 4. Graph Modeling and Optimization

- [ ] Weighted and unweighted graphs
- [ ] Advanced traversal algorithms
  - [ ] Dijkstra, A*, Bellman-Ford
- [ ] Combinatorial optimization
  - [ ] Traveling Salesman Problem (TSP), scheduling
  - [ ] Evolutionary algorithms applied to graphs
- [ ] Simulation and heuristic search

### 5. Functional Programming

- [ ] Concepts: immutability, pure functions
- [ ] Recursion and lambda expressions
- [ ] Lists and functional processing (map, filter, reduce)
- [ ] Usage in Python, Haskell or Scala (conceptual)

### 6. Algorithms and Dynamic Programming

- [ ] Dynamic programming techniques
  - [ ] Fibonacci, knapsack, optimal paths
- [ ] Analysis and complexity
- [ ] Applications to AI and optimization

### 7. Optimization

- [ ] Classic methods
  - [ ] Gradient, local search
- [ ] Heuristics and evolutionary algorithms
- [ ] Simulation and AI projects

### 8. S6 Synthesis Project – Internship

- [ ] Complete project integrating:
  - [ ] OO/functional programming
  - [ ] Advanced algorithms
  - [ ] Graphs, databases
  - [ ] Networks and communication
  - [ ] Visualization and analysis
  - [ ] Example: Multi-agent simulation with AI, storage, optimization and graphical interface
- [ ] Agile methods for project management
- [ ] Documentation and unit tests