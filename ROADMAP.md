# CS Roadmap — L1 → L3
## Design Method
This roadmap was designed by Claude AI free tier using Sonnet 5 with Max thinking level. I provided it with all the informations on the courses at the FST Université de Lorraine Licence d'Informatique that I could find so it can be as accurate as possible.

I used this prompt :
```
# CURRICULUM ARCHITECT PROMPT
## ROLE

Expert Curriculum Architect & Pedagogue. You design exhaustive, checkable, dependency-aware learning roadmaps that read like a real institution's program handbook, not a generic list of topics.

## CONTEXT

- Target Subject: [INSERT_SUBJECT]
- Current Level: [INSERT_CURRENT_LEVEL]
- Desired Goal: [INSERT_DESIRED_GOAL]
- Macro-structure unit: [INSERT_MACRO_UNIT — e.g. "Year" / "Belt level" / "Book part"]
- Meso-structure unit: [INSERT_MESO_UNIT — e.g. "Semester" / "Module" / "Chapter"]
- User Profile: Auto-didact, highly motivated, susceptible to burnout/overwhelm and is AUDHD. Needs high-relevance filtering, practical application, strict structural progression. Learns via interactive, checkable markdown roadmaps.

## INPUT MATERIALS

- [INSERT_REFERENCE_MATERIAL — official syllabi, course catalogs, prerequisite charts, job postings, exam blueprints, or any authoritative source the roadmap must track]
- If reference material is provided: every phase must explicitly map to it (e.g. "corresponds to UE1.2 Algorithmique" or "matches Chapter 4 of the official syllabus"). Flag any point where you deviate from the reference material and state why (reordering for pedagogical reasons, filling a gap the source leaves implicit, etc.).
- If no reference material is provided: state this explicitly once, then proceed using domain-standard sequencing.
- INIT_CHECK: If Subject, Current Level, or Desired Goal are blank, HALT and request them before generating anything. Reference material is optional — do not halt for it, just flag its absence.

## OUTPUT TARGET STYLE (this is the contract)

The final roadmap, once fully assembled, must have the same anatomy as a real program handbook:

1. Title line: `# [Subject] Exhaustive Roadmap — [Level] → [Goal]`
2. A **marker legend table** (see MARKER_SYSTEM below) shown once, near the top
3. A **design principles** list (3–5 bullets: pacing logic, sequencing logic, burnout mitigation specific to this domain)
4. A short **"Unknown Unknowns"** paragraph — hidden complexity/tooling/logistics self-taught learners typically miss
5. Meso-units (semesters/modules/chapters) grouped under macro-units (years/parts), each meso-unit carrying:
    - A `>` **Theme** blockquote (1–2 sentences: focus + real-world relevance)
    - Numbered major topics (max 6 per meso-unit)
    - `####` sub-categories under each major topic
    - `- [ ]` checkboxes for every atomic micro-skill
    - Inline `>` **"Why here?"** callouts wherever a sequencing choice isn't obvious
    - `⚙️` Hidden Prerequisite / Trap callouts where learners typically fail
    - `🛠️` Practical Application callouts immediately after any pure-theory block
    - A closing `✅ Synthesis Project` that integrates every topic in that meso-unit
6. Once ALL meso-units are generated, two closing appendices:
    - **Appendix A — Dependency Graph**: ASCII arrow chains showing how topics/tracks feed into each other across the whole roadmap (e.g. `Concept A → Concept B → Complex System C`)
    - **Appendix B — What Each Addition Unlocks**: a markdown table mapping every 🆕/🔬-tagged addition to the concrete capability it directly enables downstream

## CONSTRAINTS

- **COG_LANG**: Reason inside a strict markdown `<thought_process>...</thought_process>` block in EN. Final output in the user's active language.
    
- **MARKER_SYSTEM** (mandatory, shown as a legend table before the first meso-unit):
    
    |Marker|Meaning|
    |---|---|
    |(none)|Standard/expected placement for this subject|
    |`↕️`|Moved from its "obvious" position to a pedagogically better one — state why in a `>` callout the first time it's used|
    |`🆕`|Added because the reference material or domain reality demands it and a naive roadmap would omit it|
    |`🔬`|Added in a deeper refinement pass — usually theory/math prerequisites the learner won't notice they need until much later|
    
    Every topic in the roadmap must carry the correct marker or none. Do not invent new markers mid-roadmap without adding them to the legend.
    
- **DOMAIN_ADAPTATION**: If academic/digital (CS, Math, languages), focus on logic, syntax, formal notation, abstract mechanisms, theory. If physical/craft (leatherworking, DIY, sport), focus on biomechanics, tool progression, safety, sensory feedback, material behavior. Adjust the vocabulary of callouts accordingly (e.g. `🛠️` = physical prototype, not just code).
    
- **BURNOUT_PACING**: Max 6 major topics per meso-unit. Every pure-theory or safety block is IMMEDIATELY followed by a `🛠️` concrete application — this is a hard formatting rule, not a suggestion.
    
- **ABSOLUTE_PROGRESSION**: Strict fundamentals → complexity. Build theoretical, mathematical, or material/safety prerequisites explicitly before they're needed. If a later meso-unit needs a concept, that concept must already have appeared with a `>` note pointing forward (mirrors how the reference roadmap says "Gradient descent (S7) requires you to differentiate functions — this is not optional background").
    
- **RELEVANCE_FILTER**: Zero filler. Every topic must serve the stated goal. Every meso-unit gets a `>` Theme justifying its existence.
    
- **MICRO_TOPIC_EXPANSION**: Never stop at surface categories. Break every major topic into atomic, specific micro-skills (named algorithms, exact syntax rules, named techniques) — not vague headers like "learn functions."
    
- **HIDDEN_PREREQUISITES**: Actively surface unknown unknowns via `⚙️` callouts — the setup logistics, edge cases, or foundational tooling self-taught learners usually skip.
    
- **CHUNKING_RULE** (critical): Never generate the whole roadmap at once. Generate exactly ONE meso-unit (or a tightly related pair if the domain groups them, e.g. two short semesters), then HALT and wait for explicit authorization. Generate Appendix A and B only after the user confirms all meso-units are done.
    
- **FORMAT_OUTPUT**: Strict markdown hierarchy as specified in OUTPUT TARGET STYLE. Use `- [ ]` for every micro-topic without exception — the user tracks progress by checking these off.
    

## TASK

### PHASE 1 — CURRICULUM ARCHITECTURE (once, at start)

Output: title, marker legend table, design principles, "Unknown Unknowns" paragraph, and a **preview** of the dependency graph's core tracks (3–6 arrow chains, not the full appendix yet).

### PHASE 2 — GENERATION LOOP (one meso-unit per turn)

For each meso-unit, output using this rigid skeleton:

Code boxe
## [Macro-unit] — [Meso-unit N] — [Name]
> **Theme:** [1–2 sentences]

### [N]. [Major Topic] *(max 6 per meso-unit)*
**[Sub-category]**
- [ ] [marker if any] [micro-skill]
- [ ] ⚙️ *Hidden Prerequisite / Trap:* [failure mode or missing link]
- [ ] 🛠️ *Practical Application:* [concrete exercise/mini-project]

✅ [Meso-unit] Synthesis Project
- [ ] **[Project name]:** [description unifying every concept in this meso-unit]


### PHASE 3 — PROGRESSION GATE

HALT after each meso-unit. Output exactly: "🛑 **[Meso-unit] complete.** Reply 'continue' to generate [next meso-unit]: [one-line preview]. Reply 'expand [Topic]' for more depth before moving on."

### PHASE 4 — CLOSING APPENDICES (only after the user confirms the roadmap is fully generated)

Output:

- **Appendix A — Dependency Graph**: full ASCII arrow chains across every meso-unit
- **Appendix B — What Each Addition Unlocks**: table of every 🆕/🔬 topic → what it directly enables downstream
```

## How to read this roadmap

| Marker | Meaning                                                          |
| ------ | ---------------------------------------------------------------- |
| (none) | From original roadmap, same position                             |
| `↕️`   | From original roadmap, **moved** to a better position            |
| `🆕`   | **New topic** — added in first optimization pass                 |
| `🔬`   | **New topic** — added in second optimization pass (this version) |

**Design principles:**
- Every pure-theory block is immediately followed by a coding application
- Data structures: linear → tree → hash → graph (strict progression)
- No semester has more than 6 major topics
- Math tracks (linear algebra, calculus, discrete math) are built up before they're needed by AI/optimization
- Automata + computability placed **before** Compilation
- Java introduced alongside Python OOP — so you're not learning syntax mid-course

---

---

## L1 — Strong Foundations

---

## Semester 1 — First Contact
> **Theme:** Get code running. Understand the machine. Build the reflex of committing everything.

### 🆕 1. Environment Setup (Week 1 — do this first, once)
- [x] 🆕 Linux basics: `cd`, `ls`, `mkdir`, `mv`, `cp`, `man`, pipes (`|`), redirection (`>`)
- [x] 🆕 Git fundamentals: `init`, `add`, `commit`, `push`, `pull`, branches, `.gitignore`
- [x] 🆕 Python environment: interpreter, script files, `print()`, running from terminal

> **Why first?** Every project from S1 onward lives in a Git repo on a Linux terminal.
> Learn this once, never touch it again as a concept.

---

### 2. Imperative Programming — Python Core

#### Fundamental Concepts
- [x] Program: input → process → output
- [x] Debugging: bugs and classic errors (`NameError`, `TypeError`, `IndexError`)
- [x] Sequential execution

#### Python Syntax and Types
- [x] Numbers: `int`, `float`
- [x] Booleans: `True` / `False`
- [x] Strings: slicing, `len()`, `.upper()`, `.replace()`
- [x] Variables, assignment, scope (local vs global)

#### Operations
- [x] Arithmetic: `+`, `-`, `*`, `/`, `%`, `**`
- [x] Comparisons
- [x] Logical: `and`, `or`, `not`

#### Control Structures
- [x] Conditions: `if`, `elif`, `else`
- [x] Loops: `for`, `while`

#### Functions
- [x] Define a function, parameters, `return`
- [x] Scope inside functions

#### Collections
- [x] Lists: creation, access, modification
- [ ] Tuples: immutability
- [ ] Dictionaries: key-value pairs
- [ ] Sets: unordered, no duplicates

#### Simple Algorithms
- [ ] Sum, max, min — implemented from scratch
- [ ] Linear search
- [ ] Bubble sort, insertion sort

#### Modules and Libraries
- [ ] `math`, `random`, `os`

---

### 3. Mathematics for Computer Science (Applied in Python)
> Every formula becomes a function you implement.

- [ ] Integers, rationals, decimals, fractions, powers, square roots
- [ ] Basic logic: AND, OR, NOT — implement truth tables in Python
- [ ] Matrices and vectors (2D): addition, scalar multiplication — coded manually
- [ ] Basic statistics: mean, median, variance, standard deviation — from scratch
- [ ] Elementary probability: dice, drawing — simulated with `random`

---

### 4. Introduction to the Web
- [ ] HTML: basic structure (`<html>`, `<head>`, `<body>`, headings, `<p>`, `<a>`, `<img>`)
- [ ] CSS: selectors, box model, colors, fonts
- [ ] Notion of client / server

---

### ✅ S1 Synthesis Project
- [ ] Mini calculator or grade manager in Python
- [ ] **Stored in a Git repository with meaningful commits**

---
---

## Semester 2 — Data Structures, Recursion and Discrete Math
> **Theme:** Understand how data is organized and how to reason formally about it.

### 1. Recursion and Advanced Programming
- [ ] What recursion is: base case, recursive case
- [ ] Factorial, Fibonacci
- [ ] Error handling: `try` / `except`
- [ ] File reading and writing (`open`, `read`, `write`, `with`)

---

### 2. Data Structures — Proper Progression
> Each structure introduces exactly one new idea on top of the previous.

#### Linear Structures
- [ ] Arrays / lists: index, slicing, manipulations (depth)
- [ ] Stacks: LIFO — implement with a Python list
- [ ] Queues: FIFO — implement with `collections.deque`

#### 🆕 Tree Structures
- [ ] 🆕 Binary trees: nodes, leaves, root, depth, height
- [ ] 🆕 Tree traversal: preorder, inorder, postorder
- [ ] 🆕 Heaps: min-heap, max-heap, `heapify` — implement + use `heapq`

#### Hash and Set Structures
- [ ] Dictionaries (hash map): hash function, collision
- [ ] Sets: union ∪, intersection ∩, difference ∖

---

### 3. Sorting and Complexity
- [ ] Advanced sorting: merge sort, quicksort
- [ ] Complexity analysis: O(1), O(n), O(log n), O(n²)
- [ ] Space/time trade-off

---

### 4. Fundamentals of Discrete Mathematics
- [ ] Sets, relations, formal functions
  - [ ] Subsets, union, intersection, complement
  - [ ] Relations: reflexive, symmetric, transitive
  - [ ] Functions: injective, surjective, bijective
- [ ] Graphs: formal definition (nodes/edges) — intro only
- [ ] Combinatorics: permutations, combinations
- [ ] Reasoning by induction: simple proofs
- [ ] 🆕 Regular expressions: formal definition + Python `re` module
- [ ] Modular arithmetic: introduction
- [ ] Number theory basics: divisibility, GCD, LCM

---

### 5. Introduction to Databases
- [ ] Concepts: table, row, column
- [ ] Primary key / foreign key
- [ ] Basic SQL: `SELECT`, `INSERT`, `UPDATE`, `DELETE`
- [ ] Simple project: create and query a table

---

### ✅ S2 Synthesis Project
- [ ] Contact manager with file storage + CRUD operations
- [ ] 🆕 Git workflow: feature branches, pull request simulation, README

---
---

## Semester 3 — C, Memory, Architecture, Linear Algebra and OOP
> **Theme:** Understand what happens beneath Python. Think at the machine level. Get ready for AI math.

### 1. Introduction to C and Memory Management
- [ ] Basic C syntax: variables, types, operators
- [ ] Pointers: `*` and `&`
- [ ] Dynamic allocation: `malloc` / `free`
- [ ] Arrays and structures (`struct`)
- [ ] Stack vs heap
- [ ] Segmentation fault: what causes it and how to debug
- [ ] 🔬 Debugging tools: `gdb` (set breakpoints, inspect memory), `valgrind` (detect leaks)

---

### 2. Computer Architecture
- [ ] Binary representation: two's complement, IEEE 754
- [ ] CPU: registers, ALU, pipeline
- [ ] Memory: cache, RAM, virtual memory
- [ ] Simple assembler: `MOV`, `ADD`, `SUB`

---

### 3. 🔬 Linear Algebra (Properly)
> The 2D matrix intro in S1 was a preview. This is the real thing.
> Required for AI, graphics, and numerical methods in S4+.

- [ ] 🔬 Vectors in Rⁿ: coordinates, norm, dot product, angle between vectors
- [ ] 🔬 Matrix operations: addition, multiplication, transpose
- [ ] 🔬 Linear transformations: what a matrix *does* geometrically
- [ ] 🔬 Determinant: definition, 2×2 and 3×3 cases, geometric meaning (area/volume scaling)
- [ ] 🔬 Rank, kernel (null space), image — what they tell you about a system
- [ ] 🔬 Systems of linear equations: Gaussian elimination, existence/uniqueness of solutions
- [ ] 🔬 Eigenvalues and eigenvectors: definition, computation, geometric interpretation
- [ ] 🔬 Apply in Python: implement matrix ops from scratch, then verify with `numpy`

---

### 4. Object-Oriented Programming (OOP) — Python and Java

#### Core OOP Concepts (in Python first)
- [ ] Classes and objects
- [ ] Attributes and methods
- [ ] Encapsulation
- [ ] Inheritance and polymorphism
- [ ] Modules and packages, simple program design

#### 🔬 Java Introduction (same concepts, different syntax)
> Most French CS courses use Java. Learning it here means you follow lectures on day 1.

- [ ] 🔬 Java syntax: types, `static`, `void`, `public`/`private`
- [ ] 🔬 Classes and objects in Java: constructors, `this`
- [ ] 🔬 Inheritance and interfaces in Java
- [ ] 🔬 Compile and run: `javac` / `java`
- [ ] 🔬 Comparison exercise: rewrite your Python OOP project in Java

#### Practical Exercises
- [ ] Animal class with Dog and Cat subclasses (Python → Java)
- [ ] Managing collections of objects

---

### 5. Advanced Discrete Mathematics
- [ ] Equivalence relations and partitions, partial orders and chains
- [ ] Formal graphs: directed/undirected, degree, path, cycle, adjacency matrices
- [ ] Modular arithmetic: congruences, modulo n
- [ ] Number theory: prime numbers, GCD algorithms
- [ ] Double induction

---

### 6. Formal Logic
- [ ] Propositional logic: syntax, semantics, truth tables, CNF, DNF
- [ ] First-order logic: variables, quantifiers ∀, ∃, predicates and functions
- [ ] Formal proofs: natural derivation, resolution

---

### ✅ S3 Synthesis Project
- [ ] Graph manager using OOP (Python + Java version)
- [ ] Adjacency list and matrix representations
- [ ] DFS / BFS traversal, path and cycle analysis
- [ ] 🆕 Documented with a UML class diagram

---
---

## L2 — Deepening and Transition

---

## Semester 4 — Algorithms, Calculus, Automata and AI
> **Theme:** Master algorithms and the math that drives AI. Understand what computation itself means.

### 1. Algorithms and Complexity — In Depth
- [ ] Quicksort and merge sort: formal analysis
- [ ] Binary search in complex structures
- [ ] In-depth recursion: Tower of Hanoi, recursion on lists/trees/graphs
- [ ] Algorithmic optimization: memory/time trade-offs (revisited formally)

---

### 2. Graph Algorithms
- [ ] Traversal: DFS, BFS (formal + implemented)
- [ ] Trees and forests
- [ ] Shortest path: Dijkstra — concept + implementation
- [ ] Applications: networks, maps, social graphs

---

### 3. 🔬 Differential Calculus (for Computing)
> Gradient descent (S7) requires you to differentiate functions.
> This is not optional background — it is a direct prerequisite.

- [ ] 🔬 What a derivative is: rate of change, geometric intuition (slope of the tangent)
- [ ] 🔬 Derivative rules: power rule, product rule, chain rule
- [ ] 🔬 Partial derivatives: functions of several variables — ∂f/∂x, ∂f/∂y
- [ ] 🔬 Gradient: definition (∇f), direction of steepest ascent
- [ ] 🔬 Taylor expansion (first-order): linear approximation of a function
- [ ] 🔬 Apply in Python: implement numerical differentiation, plot gradients with `matplotlib`

---

### 4. 🆕 Automata Theory, Formal Languages and Computability
> Expanded to include computability — the theoretical foundation of CS.

#### Automata and Languages
- [ ] 🆕 Deterministic Finite Automata (DFA): states, transitions, acceptance
- [ ] 🆕 Non-deterministic Finite Automata (NFA): definition, equivalence with DFA
- [ ] 🆕 Regular languages: definition, closure properties
- [ ] 🆕 Context-Free Grammars (CFG): productions, derivations, parse trees
- [ ] 🆕 Pushdown Automata (intro)
- [ ] 🆕 Chomsky hierarchy: Type 0, 1, 2, 3
- [ ] 🆕 Connection to regular expressions and to lexing

#### 🔬 Computability Theory
- [ ] 🔬 Turing machines: tape, states, transitions — formal model of computation
- [ ] 🔬 Church-Turing thesis: what "computable" means
- [ ] 🔬 The halting problem: proof that it is undecidable
- [ ] 🔬 Decidability vs semi-decidability
- [ ] 🔬 Rice's theorem (statement and intuition)

---

### 5. 🔬 Numerical Methods (Intro)
> Floating point is not exact. Every AI/optimization result depends on this.

- [ ] 🔬 Floating point errors: catastrophic cancellation, loss of significance
- [ ] 🔬 Newton's method: root-finding as an iterative algorithm
- [ ] 🔬 Numerical integration: trapezoidal and Simpson's rule
- [ ] 🔬 Numerical stability: what makes an algorithm robust
- [ ] 🔬 Apply in Python: implement each method, compare results vs exact analytic solution

---

### 6. Applied Probability and Statistics
- [ ] Conditional probabilities, Bayes' theorem
- [ ] Simple random variables, law of large numbers
- [ ] Simulation in Python

---

### 7. Graphical User Interfaces (GUI)
- [ ] Tkinter or PyQt basics: window, widgets, events
- [ ] Mini-calculator, graph visualization

---

### 8. Introduction to Artificial Intelligence
- [ ] What is a model? Dataset, features, labels
- [ ] Linear regression
- [ ] Supervised classification
- [ ] Clustering: K-means
- [ ] Evolutionary algorithms: population, mutation, selection, fitness

---

### ✅ S4 Synthesis Project
- [ ] Option A: Multi-agent simulation — agents interact, state tracked in DB, results visualized
- [ ] Option B: Graph + database project with statistical analysis

---
---

## Semester 5 — Systems, Networks, APIs and Databases
> **Theme:** Understand how computers talk to each other and how data is stored at scale.

### 1. Systems: Processes, Threads and Memory
- [ ] 🆕 Linux/shell scripting (intermediate): scripts, variables, loops, `cron`, `grep`, `awk`
- [ ] Processes and threads: creation and termination
- [ ] Synchronization: mutex, semaphores
- [ ] Classic problems: producer-consumer
- [ ] Deadlock: detection and prevention
- [ ] Memory management: static/dynamic allocation, segmentation, fragmentation
- [ ] Inter-process communication (IPC)
- [ ] 🔬 Docker basics: what a container is, `Dockerfile`, `docker build`, `docker run`, `docker-compose`

> **Why Docker here?** You now know enough about processes, isolation, and networking to understand what Docker actually does.

---

### 2. Networks — All Layers
> Lower and upper layers taught together for coherence.

#### Lower Layers
- [ ] IP, MAC address
- [ ] Protocols: TCP, UDP, HTTP
- [ ] Socket programming in Python
- [ ] Client/server communication, ping

#### Upper Layers
- [ ] OSI vs TCP/IP model: application, presentation, session
- [ ] Protocols: HTTP/HTTPS, FTP, SMTP, DNS
- [ ] Multiple clients, simultaneous communication
- [ ] Routing and subnets: network mask, CIDR

#### Basic Network Security
- [ ] SSL/TLS, simple encryption, authentication

#### 🔬 REST APIs
- [ ] 🔬 HTTP methods: GET, POST, PUT, DELETE — semantics and usage
- [ ] 🔬 Status codes: 200, 201, 400, 401, 404, 500
- [ ] 🔬 JSON: structure, serialization, parsing in Python
- [ ] 🔬 Designing a REST API: resources, endpoints, naming conventions
- [ ] 🔬 Consuming a REST API: `requests` library in Python
- [ ] 🔬 Simple project: build a REST API with Flask + consume it from a client

---

### 3. Advanced Databases
- [ ] Relational design: normalization 1NF → 2NF → 3NF, integrity constraints
- [ ] Advanced SQL: complex JOINs, subqueries, aggregations, transactions, indexes
- [ ] NoSQL: MongoDB — documents, collections, indexing, performance

---

### 4. Statistics for Computer Science
- [ ] Discrete and continuous random variables
- [ ] Conditional probabilities and Bayes (deepened)
- [ ] Model evaluation: precision, recall, F1-score

---

### ✅ S5 Synthesis Project
- [ ] Multi-agent system with database + GUI + REST API
- [ ] OR: Mini network server with concurrent processing + statistical visualization

---
---

## L3 — Specialization and Professional Development

---

## Semester 6 — Advanced Design, Logic and Security
> **Theme:** Write production-quality code. Design defensively. Prove correctness.

### 1. Advanced OOP Design

#### Design Patterns
- [ ] Singleton, Factory, Observer
- [ ] Exception handling in OO projects
- [ ] Modularity and packaging
- [ ] Unit tests: `unittest` in Python, JUnit in Java

#### 🔬 SOLID Principles
> The foundation of maintainable OOP. Design patterns are applications of SOLID.

- [ ] 🔬 Single Responsibility Principle (SRP): a class does one thing
- [ ] 🔬 Open/Closed Principle (OCP): open for extension, closed for modification
- [ ] 🔬 Liskov Substitution Principle (LSP): subclasses must be substitutable
- [ ] 🔬 Interface Segregation Principle (ISP): no forced dependencies on unused interfaces
- [ ] 🔬 Dependency Inversion Principle (DIP): depend on abstractions, not concretions
- [ ] 🔬 Exercise: refactor a bad OOP codebase using SOLID as a guide

#### Software Engineering Methodology
- [ ] 🆕 UML: class diagrams, sequence diagrams
- [ ] 🆕 Agile: sprints, user stories, kanban, retrospectives
- [ ] 🔬 TDD (Test-Driven Development): red → green → refactor cycle

---

### 2. Advanced Logic
- [ ] Complete first-order logic: quantifiers, substitution, resolution, derivation
- [ ] Combinational logic: circuits, program verification

---

### 3. Functional Programming
- [ ] Immutability, pure functions
- [ ] Recursion and lambda expressions
- [ ] `map`, `filter`, `reduce`
- [ ] Python / Haskell / Scala conceptual

---

### 4. Introduction to Computer Security
- [ ] CIA triad: confidentiality, integrity, availability
- [ ] Authentication and authorization
- [ ] Symmetric and asymmetric encryption
- [ ] Classic vulnerabilities: SQL injection, buffer overflow, XSS

---

### ✅ S6 Synthesis Project
- [ ] Project: OOP design patterns + SOLID + unit tests + network + database + security awareness
- [ ] Documented with UML, managed with Agile, tracked in Git

---
---

## Semester 7 — Complexity Theory, Algorithms, Compilation and Functional Theory
> **Theme:** The hardest theoretical content. Understand what is impossible, what is slow, and how to build a language.

### 1. 🔬 Complexity Classes
> Big O (S2-S4) measured *how fast* an algorithm runs.
> This block classifies *what problems can be solved efficiently at all*.

- [ ] 🔬 Class P: problems solvable in polynomial time
- [ ] 🔬 Class NP: problems verifiable in polynomial time
- [ ] 🔬 NP-complete: hardest problems in NP (definition)
- [ ] 🔬 NP-hard: at least as hard as NP-complete
- [ ] 🔬 Polynomial reduction: showing problem A is at least as hard as problem B
- [ ] 🔬 Classic NP-complete problems: SAT, vertex cover, clique, TSP
- [ ] 🔬 P vs NP: the open question and why it matters

---

### 2. Dynamic Programming
- [ ] Fibonacci (memoization vs tabulation), knapsack, optimal paths
- [ ] Complexity analysis of DP solutions
- [ ] Applications to AI and optimization

---

### 3. Graph Modeling and Optimization
- [ ] Weighted and unweighted graphs
- [ ] Dijkstra (formal proof), A*, Bellman-Ford
- [ ] Combinatorial optimization: TSP, scheduling
- [ ] Evolutionary algorithms applied to graphs
- [ ] Simulation and heuristic search

---

### 4. Optimization
- [ ] Gradient descent: connects directly to calculus block in S4
- [ ] Local search
- [ ] Heuristics and evolutionary algorithms

---

### 5. Compilation
> Automata + computability (S4) are direct prerequisites for this block.

- [ ] Lexing: tokenizing source code — link to DFA/NFA
- [ ] Parsing: syntax analysis — link to CFG
- [ ] Abstract Syntax Trees (AST)
- [ ] Semantic analysis
- [ ] Code optimization
- [ ] Machine code / bytecode generation
- [ ] Compilation error handling
- [ ] Introduction to modern compilers

---

### 6. Functional Programming — Theory
- [ ] Immutability, pure functions (revision)
- [ ] `map`, `filter`, `reduce` in depth
- [ ] 🔬 Lambda calculus: syntax (λx.e), β-reduction, Church encoding of booleans and numbers
- [ ] 🔬 Relation to Turing machines: Church-Turing thesis from the functional side
- [ ] Conceptual: Haskell or Scala types and laziness

---

### 7. Mobile Application Development
- [ ] Android/iOS environments
- [ ] UI, events, local storage
- [ ] Server + database connection
- [ ] Simple tracking or simulation application

---

### ✅ S7 Synthesis Project
- [ ] Graph optimization tool OR small interpreter/compiler
- [ ] Full pipeline: parse → analyze → execute → visualize

---
---

## Semester 8 — Final Project and Professional Readiness
> **Theme:** Integrate everything. Build something real. Defend it.

### 1. Final Synthesis Project
- [ ] Complete project integrating:
  - [ ] OO and/or functional programming
  - [ ] Advanced algorithms and dynamic programming
  - [ ] Graphs, databases, REST API
  - [ ] Networks and communication
  - [ ] Visualization and analysis
  - [ ] Simulation and AI
  - [ ] Security awareness, Docker deployment
- [ ] 🆕 Full documentation: README, API docs, UML architecture diagram
- [ ] 🆕 Test suite: unit tests + integration tests + CI
- [ ] Agile project management: sprint retrospective, burn-down chart
- [ ] Presented and defended as a capstone

---

## Appendix A — Topic Dependency Graph

```
Git → everything
Linux → everything
Python Core → Collections → Recursion → Data Structures → Algorithms
Data Structures: linear → trees → heaps → hash → graphs
Discrete Math → Formal Logic → Automata → Computability → Compilation
  └─ Chomsky Hierarchy → CFG → Parsing → AST
Modular Arithmetic → Number Theory → Cryptography
2D Matrices (S1) → Linear Algebra (S3) → Eigenvalues → AI/ML Math
Derivatives (S4) → Gradient → Gradient Descent → Optimization (S7)
Numerical Methods (S4) → Stability → AI robustness
Probability → Statistics → Bayes → ML Evaluation
C + Architecture → gdb/valgrind → Systems → Docker → Deployment
OOP (Python) → OOP (Java) → SOLID → Design Patterns → Unit Tests → TDD
Graph Theory → Graph Algorithms → Dijkstra → A* → Optimization
Complexity Analysis (Big O) → Complexity Classes (P/NP) → NP-complete
Lambda Calculus → Functional Programming → Haskell conceptual
REST APIs → Flask → Full-stack project
```

---

## Appendix B — What Each Addition Unlocks

| Added Topic | Directly enables |
|---|---|
| Linear Algebra (S3) | AI/ML math, eigendecomposition in stats, graphics |
| Differential Calculus (S4) | Gradient descent, backpropagation intuition, optimization |
| Computability Theory (S4) | Understanding limits of CS, Compilation theory, P/NP |
| Complexity Classes (S7) | Knowing when to give up on exact solutions, use heuristics |
| Java (S3) | Following university OOP/algorithms courses on day 1 |
| SOLID (S6) | Maintainable OOP, better design pattern usage |
| Lambda Calculus (S7) | Formal FP theory, type systems, compiler semantics |
| REST APIs (S5) | Every modern web/backend project |
| Docker (S5) | Clean project deployment, university lab submissions |
| gdb/valgrind (S3) | Debugging C without guessing, catching memory leaks |
| Numerical Methods (S4) | AI robustness, understanding why floats lie |
| TDD (S6) | Writing code that is correct by construction |

---

*Last updated: May 2026 — optimized for AUDHD learner, University of Lorraine CS entry*








