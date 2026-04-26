Certo, eccolo in un unico blocco copiabile. Crea un file nella root chiamato `projects.md` e incolla tutto questo:

````md
# Projects

This page provides a more detailed map of my GitHub projects. The main `README.md` keeps only a short selection, while this file works as an extended portfolio page for reviewers, recruiters, and academic evaluators.

The projects are grouped by the kind of skill or signal they are meant to show: programming languages, formal methods, scientific computing, systems engineering, algorithms, and structured technical study.

---

## Portfolio Overview

| Area | Main repositories | What they demonstrate |
|---|---|---|
| Programming languages & DSLs | [Sophie](https://github.com/cicixgliamici/sophie) | DSL design, parsing, typed ASTs, evaluator architecture, Scala engineering |
| Formal methods & logic | [A Weak Silly Substitution Calculus](https://github.com/cicixgliamici/a-weak-Silly-substitution-Calculus) | Lean 4, substitution calculi, rewriting, formal reasoning |
| Safety-oriented C | [NASA Power of Ten Demo](https://github.com/cicixgliamici/nasa-power-of-ten-demo) | disciplined C, traceability from paper to code, tests, CI |
| Quantum computing education | [Quantum-Ed](https://github.com/cicixgliamici/quantum_ed) | quantum foundations, NumPy-first scientific computing, notebooks, tests |
| Log analytics / algorithms | [simhash-logs](https://github.com/cicixgliamici/simhash-logs) | Go, SimHash, near-duplicate detection, observability/security use cases |
| System design | [System Design](https://github.com/cicixgliamici/System_design) | distributed systems reasoning, architecture trade-offs, interview preparation |
| Algorithms practice | [LeetCode](https://github.com/cicixgliamici/leetcode), Project Euler | problem solving, multi-language practice, complexity analysis |
| Academic engineering projects | [Algorithms & Data Structures](https://github.com/cicixgliamici/Algoritmi-StruttureDati_2024), [Software Engineering](https://github.com/cicixgliamici/Ingegneria_Software2024), [Digital Logic Design](https://github.com/cicixgliamici/RetiLogiche_2024) | C, Java, VHDL, software architecture, hardware-oriented design |

---

## Suggested Reading Paths

### For programming languages and formal reasoning

1. [Sophie](https://github.com/cicixgliamici/sophie)
2. [A Weak Silly Substitution Calculus](https://github.com/cicixgliamici/a-weak-Silly-substitution-Calculus)
3. [Programming Languages Reference & Practice](https://github.com/cicixgliamici/ProgrammingLanguages)

This path highlights my interest in programming-language foundations, interpreters, formal structure, syntax, substitution, and mechanized reasoning.

### For rigorous software engineering

1. [NASA Power of Ten Demo](https://github.com/cicixgliamici/nasa-power-of-ten-demo)
2. [simhash-logs](https://github.com/cicixgliamici/simhash-logs)
3. [Sophie](https://github.com/cicixgliamici/sophie)

This path emphasizes small but reviewable artifacts, testing discipline, traceability, and engineering decisions.

### For academic and scientific computing interests

1. [Quantum-Ed](https://github.com/cicixgliamici/quantum_ed)
2. [A Weak Silly Substitution Calculus](https://github.com/cicixgliamici/a-weak-Silly-substitution-Calculus)
3. Future logic and quantum/formal-verification repositories

This path is the closest to my long-term interests in logic, theoretical computer science, quantum computing, and formal methods.

### For interview-oriented preparation

1. [LeetCode](https://github.com/cicixgliamici/leetcode)
2. [System Design](https://github.com/cicixgliamici/System_design)
3. [Programming Languages Reference & Practice](https://github.com/cicixgliamici/ProgrammingLanguages)

This path shows structured preparation for software engineering interviews and technical discussions.

---

# Core Technical Projects

## Sophie

**Repository:** [cicixgliamici/sophie](https://github.com/cicixgliamici/sophie)  
**Status:** public, active  
**Type:** programming-language / DSL / software architecture project  
**Main stack:** Scala 3, sbt, ANTLR4, ScalaTest, uPickle

Sophie is a JVM-based domain-specific language for expressing simple trading strategies and portfolio allocations. The repository is designed around a complete language-engineering pipeline:

```text
source program -> parser -> typed AST -> evaluator -> execution plan -> lowered instructions -> execution/persistence
```

### What the project does

Sophie lets the user write compact strategy-like programs such as buy/sell rules, conditional execution, portfolio target allocations, price lookups, arithmetic expressions, and indicators such as moving averages, EMA, standard deviation, and RSI.

The project is not meant to be a production trading platform. Its value is in showing how a small language can be designed, parsed, represented, evaluated, and connected to execution-oriented abstractions.

### What it demonstrates

- DSL design and syntax engineering
- ANTLR-based parser construction
- typed AST modeling with Scala case classes and sealed traits
- interpreter/evaluator architecture
- separation between pure core logic and side-effecting execution
- CLI/TUI reuse of the same core pipeline
- testing of language behavior and execution components

### Best reviewer entry points

- `src/main/antlr4/sophie.g4` — grammar definition
- `src/main/scala/ast` — AST and AST builder
- `src/main/scala/engine` — evaluator, execution plan, lowering, persistence
- `src/main/scala/frontend` — parser facade and interactive frontend
- `src/test/scala` — unit and integration tests
- `docs/` — language and architecture notes

### Why it matters in my portfolio

This is currently one of my strongest software artifacts because it connects theory-oriented interests — syntax, semantics, ASTs, evaluation — with practical software architecture.

---

## NASA Power of Ten Demo

**Repository:** [cicixgliamici/nasa-power-of-ten-demo](https://github.com/cicixgliamici/nasa-power-of-ten-demo)  
**Status:** public, review-ready compact artifact  
**Type:** safety-oriented C / technical paper implementation  
**Main stack:** C, Make, unit tests, GitHub Actions

This repository is a small C project inspired by the NASA/JPL *Power of Ten* rules for safety-critical software. The main artifact is a fixed-size ring buffer written to demonstrate disciplined implementation rather than feature breadth.

### What the project does

The project translates the ideas of the paper into a concrete, inspectable C artifact. It focuses on bounded memory, simple control flow, explicit error handling, assertions, warning-clean compilation, tests, and documentation that maps rules to implementation choices.

### What it demonstrates

- disciplined C programming
- bounded data structures
- explicit error handling
- traceability from engineering guidelines to code
- unit testing of edge cases
- CI and repository hygiene
- technical reflection on the limits of safety-oriented rules

### Best reviewer entry points

- `include/ring_buffer.h` — public API
- `src/ring_buffer.c` — core implementation
- `tests/test_ring_buffer.c` — behavior and edge-case tests
- `docs/rule-mapping.md` — paper-to-code traceability
- `docs/evidence-matrix.md` — compact evaluation view
- `.github/workflows/ci.yml` — automated quality checks

### Why it matters in my portfolio

It shows that I can take a technical paper or engineering guideline, extract actionable constraints, implement a small artifact, and document the reasoning behind design choices.

---

## Quantum-Ed

**Repository:** [cicixgliamici/quantum_ed](https://github.com/cicixgliamici/quantum_ed)  
**Status:** public, active educational repository  
**Type:** quantum computing education / scientific computing  
**Main stack:** Python, NumPy, Jupyter, pytest

Quantum-Ed is an educational repository for quantum computing, quantum information, and hardware-aware foundations. It combines theory notes, runnable notebooks, reusable Python utilities, demos, and tests.

### What the project does

The repository builds a learning path from basic linear algebra to qubits, state vectors, measurement, Bell states, circuits, density matrices, noise channels, and introductory hardware considerations.

The emphasis is on understanding the mathematics first, then using code to make the ideas inspectable and testable.

### What it demonstrates

- mathematical exposition
- scientific computing with NumPy
- educational repository design
- tests for mathematical properties
- notebooks as executable explanations
- quantum-computing foundations
- bridge between theory notes and runnable code

### Best reviewer entry points

- `docs/` — structured theory chapters
- `notebooks/` — executable learning material
- `src/quantum_ed/` — reusable Python modules
- `tests/` — validation of states, gates, measurement, entanglement, and noise behavior
- `environment.yml` / `pyproject.toml` — reproducible setup

### Why it matters in my portfolio

This repository supports my long-term academic direction toward quantum computing, formal reasoning, and rigorous technical education. It is also designed to become a base for future quantum/formal-verification projects.

---

## A Weak Silly Substitution Calculus

**Repository:** [cicixgliamici/a-weak-Silly-substitution-Calculus](https://github.com/cicixgliamici/a-weak-Silly-substitution-Calculus)  
**Status:** public, theory-oriented and evolving  
**Type:** formal methods / Lean 4 / programming-language theory  
**Main stack:** Lean 4, Lake

This repository studies a small substitution-based calculus and develops a Lean 4 formalization around its syntax, contexts, reductions, strategies, normal forms, and selected theorems.

### What the project does

The project treats substitution as an explicit part of the formal object rather than only as a meta-operation. It defines terms, weak contexts, substitution contexts, root steps, contextual closure, strict strategies, normal-form structures, and mechanically checked examples/theorems.

### What it demonstrates

- Lean 4 project structure
- formal syntax definitions
- explicit substitution and reduction systems
- operational semantics intuition
- theorem-proving workflow
- connection between logic, rewriting, and programming-language foundations

### Best reviewer entry points

- `SSC/Syntax.lean` — terms, values, free variables
- `SSC/Contexts.lean` — weak and substitution contexts
- `SSC/Reduction.lean` — root reduction and contextual step relation
- `SSC/Strategy.lean` — strict strategy contexts and steps
- `SSC/NormalForms.lean` — normal-form-related definitions
- `SSC/Theorems/` — mechanically checked proof material
- `SSC/Tests/` — compile-time verified examples

### Why it matters in my portfolio

This is the clearest repository signal for my interest in logic, formal systems, mechanized reasoning, lambda-calculus-style foundations, and future graduate study in logic/theoretical computer science.

---

## simhash-logs

**Repository:** [cicixgliamici/simhash-logs](https://github.com/cicixgliamici/simhash-logs)  
**Status:** public, Step 1 completed / Step 2 in progress  
**Type:** paper-inspired algorithm implementation / log analytics / cybersecurity-adjacent tooling  
**Main stack:** Go, CLI, tests

This repository implements a practical version of SimHash for near-duplicate detection in system logs. It is inspired by similarity estimation techniques and adapts them to observability and security-oriented log processing.

### What the project does

The project normalizes noisy log fields, tokenizes messages, computes 64-bit SimHash fingerprints, compares fingerprints via Hamming distance, and detects near-duplicate log lines. The current implementation includes a brute-force baseline and in-memory LSH-like candidate generation.

### What it demonstrates

- Go project structure
- text normalization and tokenization
- SimHash fingerprinting
- Hamming-distance-based matching
- baseline vs indexed search trade-offs
- CLI design
- observability and cybersecurity use-case thinking

### Best reviewer entry points

- `cmd/` — CLI entrypoint
- `internal/normalize/` — noisy-field normalization
- `internal/tokenize/` — tokenization utilities
- `internal/simhash/` — SimHash and Hamming distance
- `internal/search/` — brute-force and indexed matching logic
- `examples/` — sample log inputs
- `docs/` — design notes and experiment material

### Why it matters in my portfolio

It shows that I can take an algorithmic idea from literature and turn it into an applied engineering prototype with realistic data-processing motivations.

---

# Educational and Preparation Repositories

## System Design

**Repository:** [cicixgliamici/System_design](https://github.com/cicixgliamici/System_design)  
**Status:** public, growing educational repository  
**Type:** distributed systems / architecture reasoning / interview preparation

This repository organizes system-design fundamentals, distributed-systems concepts, architectural patterns, case studies, exercises, and glossary material.

### What it demonstrates

- structured reasoning about distributed systems
- reliability, scalability, and performance trade-offs
- architecture communication
- interview preparation discipline
- reusable templates for design discussions

### Planned value

The long-term goal is to make it a structured handbook of system-design reasoning rather than a random collection of interview prompts.

---

## LeetCode Solutions

**Repository:** [cicixgliamici/leetcode](https://github.com/cicixgliamici/leetcode)  
**Status:** public, being normalized  
**Type:** algorithms practice / multi-language problem solving

This repository collects LeetCode solutions, currently organized by difficulty and supported by maintenance scripts for metadata, statistics, and generated problem indexes.

### What it demonstrates

- algorithmic problem solving
- complexity analysis
- multi-language implementation practice
- repository normalization and metadata discipline
- interview-oriented preparation

### Current direction

The repository is being moved toward a consistent structure where each problem has metadata, a README, approach explanation, complexity notes, and one or more language-specific implementations.

---

## Programming Languages Reference & Practice

**Repository:** [cicixgliamici/ProgrammingLanguages](https://github.com/cicixgliamici/ProgrammingLanguages)  
**Status:** public, growing study repository  
**Type:** programming-language reference / practice archive

This repository collects notes, exercises, small examples, and language-specific material across C, Java, Scala, Python, Lean 4, and Spring Boot.

### What it demonstrates

- broad programming-language practice
- comparison of idioms across languages
- language-specific study discipline
- connection between practical programming and language foundations
- preparation for interviews and technical breadth

### Role in the portfolio

It is best understood as a structured learning archive rather than as a single finished software artifact.

---

## Project Euler

**Repository:** currently private / in progress  
**Status:** early stage  
**Type:** mathematical problem solving / algorithms / numerical reasoning

The Project Euler repository is intended to become a mathematics-oriented problem-solving archive. Its role is different from LeetCode: the emphasis is less on interview-style patterns and more on number theory, combinatorics, mathematical insight, and efficient implementation.

### Intended value

- show mathematical maturity through code
- practice efficient algorithms for mathematical problems
- complement the formal/theoretical direction of the portfolio
- provide a bridge between programming, mathematics, and computational reasoning

### Public-release condition

This repository should become public once it has a clean structure, consistent documentation, and enough solved problems to look intentional rather than empty.

---

# Academic Engineering Projects

These repositories come from university coursework and are useful as evidence of foundational engineering experience. They are not all equally polished as modern portfolio artifacts, but they show important technical background.

## Algorithms and Data Structures 2024

**Repository:** [cicixgliamici/Algoritmi-StruttureDati_2024](https://github.com/cicixgliamici/Algoritmi-StruttureDati_2024)  
**Status:** public academic project  
**Type:** C / data structures / algorithmic system

This project implements a bakery-management simulation in C using data structures such as hash tables, min-heaps, max-heaps, queues, and linked lists.

### What it demonstrates

- C programming
- manual memory management
- hash tables, heaps, queues, and linked lists
- modular decomposition across source files
- performance-oriented data-structure selection
- algorithmic reasoning under constraints

---

## Software Engineering 2024

**Repository:** [cicixgliamici/Ingegneria_Software2024](https://github.com/cicixgliamici/Ingegneria_Software2024)  
**Status:** public academic group project  
**Type:** Java / software engineering / client-server game

This project implements the board game *Codex Naturalis* as a university software-engineering project, including complete rules, textual UI, graphical UI, TCP socket connection, and chat functionality.

### What it demonstrates

- Java software engineering
- larger group project organization
- client-server communication
- UML and design documentation
- testing and delivery artifacts
- GUI/TUI implementation

---

## Digital Logic Design 2024

**Repository:** [cicixgliamici/RetiLogiche_2024](https://github.com/cicixgliamici/RetiLogiche_2024)  
**Status:** public academic project  
**Type:** VHDL / FSM / hardware-oriented design

This project implements a RAM sequence-processing finite-state machine in VHDL. The design reads and processes memory sequences, handles zero values, computes credibility values, and writes processed results back to RAM.

### What it demonstrates

- VHDL design
- finite-state machines
- RAM interaction
- synchronous hardware reasoning
- testbench-based verification
- hardware/software boundary awareness

---

# Supporting Study Repositories

Some repositories are primarily private or study-oriented archives rather than public portfolio artifacts.

| Repository | Visibility / role | Notes |
|---|---|---|
| `university` | private academic archive | useful for personal organization, not intended as a public portfolio artifact |
| `courses` | private learning archive | useful for certifications and independent study material |
| `project_euler` | private / in progress | should become public after enough structure and solved problems are added |

These repositories are part of my broader learning system, while the public repositories above are the ones intended for external review.
