# Project Portfolio

This page provides a detailed guide to my projects: why they were developed, what they implement, and where to inspect the supporting evidence.

The portfolio has four categories:

1. **Academic Projects** : coursework developed during my Master's and Bachelor's degrees.
2. **Paper Implementations & Formalizations** : studies that translate published ideas into code, formal definitions, proofs, or engineering constraints.
3. **Independent Explorations** : tools and experiments driven by questions I wanted to investigate.
4. **Learning Resources & Study Notes** : explanations, exercises, reference material, and executable learning paths.

Each repository has one primary category here. Projects can share themes across categories: an academic project can also involve formal methods, and a learning repository can contain substantial tested code.

[Profile](./README.md) · [Full academic coursework](./education.md)

## Suggested Reading Paths

| Interest | Suggested route |
|---|---|
| Programming languages and semantics | Sophie → Abstracting Abstract Machines → A Weak Silly Substitution Calculus |
| Quantum computing and verification | Formal Quantum Validation → Quantum-Ed |
| C and systems engineering | NASA Power of Ten Demo → cnumkit → C++ Netprobe |
| Algorithms and experimental evaluation | SimHash Logs → Abstracting Abstract Machines → Keywords in Languages |
| Simulation and applied modeling | Post-Crisis Collective Decision Simulator → Vehicle Dynamics KPI Toolbox → Environmental Telemetry Risk Pipeline |

The descriptions below summarize the repositories rather than certify their current build status. Each repository's README, tests, and documentation provide the detailed scope, setup commands, and verification evidence.

## Academic Projects

These projects originate from university coursework. The course context explains the initial task; the repository documents the resulting implementation and any subsequent development. Descriptions of group projects refer to the team's artifact.

### Master's Degree — University of Bologna

**Academic year 2026–2026** · Both projects received **30/30 with honours (30 e lode)**.

#### Sophie

**Repository:** [cicixgliamici/sophie](https://github.com/cicixgliamici/sophie)  
**Course:** Computational Models and Programming Languages (*Linguaggi e Modelli Computazionali*)  
**Stack:** Scala 3, sbt, ANTLR4, ScalaTest, uPickle

**Purpose.** Explore how a small domain-specific language can connect readable trading rules to a structured execution pipeline.

**Implemented artifact.** Sophie parses source programs into a typed AST, evaluates conditions against market data, produces an execution plan, lowers it into instructions, and applies those instructions to portfolio state. CLI and TUI frontends reuse the underlying pipeline.

The language supports conditional buy/sell statements, quantities and monetary amounts, price lookups, arithmetic, Boolean expressions, and selected indicators. Decision explanations retain evaluated values and distinguish false conditions from branches skipped through short-circuiting.

**Design and evidence.** A shared pure accounting engine supports preview and execution. Ordered batches validate cash, holdings, quantities, prices, and currency compatibility before acceptance. File execution adds locking and recovery mechanisms. Tests cover language behavior and execution components.

**Scope.** This is a language-engineering and simulation project. Automatic portfolio rebalancing, FX conversion, and advanced order types are outside the implemented scope. Instruction identifiers do not provide replay protection.

**Review route.** Start with the README example, inspect `src/main/antlr4/sophie.g4`, then follow `src/main/scala/ast/` and `src/main/scala/engine/`. Read `docs/decision_explanations.md`, `docs/storage_and_persistence.md`, and the corresponding tests. Run `sbt test` after following the setup instructions.

#### Formal Quantum Validation

**Repository:** [cicixgliamici/formal-quantum-validation](https://github.com/cicixgliamici/formal-quantum-validation)  
**Course:** Introduction to Quantum Computing  
**Stack:** Python, Qiskit, Lean 4, mathlib, Coq/SQIR

**Purpose.** Investigate how executable quantum-circuit checks can be connected to exact mathematical statements and kernel-checked proofs.

**Implemented artifact.** The project uses a restricted circuit language containing `I`, `X`, `Z`, `H`, `CNOT`, and `SWAP`. Executable checks and formal backends cover Bell preparation, GHZ(3), and two fixed Deutsch–Jozsa examples. Lean additionally proves the nonempty GHZ(n) family and unitarity and normalization preservation for supported circuits.

A separate certificate path supports exact cancellation of adjacent equal self-inverse gates. A relative-phase demonstration shows why matching basis-measurement probabilities alone is insufficient to establish the intended state.

**Design and evidence.** Versioned IR and contracts connect the executable and formal layers. Tests include semantic regressions, generated-source drift checks, and deliberately incorrect targets that must be rejected.

**Scope.** Kernel acceptance applies to the emitted formal statement. It does not establish correctness of Qiskit, the Python extractor, or the entire translation pipeline. Automatic proof generation remains practical for small fixed circuits; broader parametric results require reusable lemmas and induction.

**Review route.** Read `docs/ARCHITECTURE.md` and `docs/TRUST_BOUNDARY.md`, inspect an IR/contract pair, then follow its generated Lean and Coq modules. Use `docs/PHASE_DEMO.md` for the phase example and `docs/DEVELOPMENT.md` for the separate toolchain-dependent suites.

### Bachelor's Degree — Politecnico di Milano

#### Codex Naturalis

**Repository:** [cicixgliamici/Ingegneria_Software2024](https://github.com/cicixgliamici/Ingegneria_Software2024)  
**Course:** Software Engineering (*Ingegneria del Software*)  
**Context:** Academic year 2023–2024; four-person team, AM19  
**Technology:** Java, TCP sockets, graphical and textual interfaces

**Purpose and artifact.** Implement the board game *Codex Naturalis* as a client-server application. The team artifact includes the game rules, GUI, TUI, network communication, and chat.

**Evidence to inspect.** Source and tests are accompanied by UML diagrams, generated JavaDoc, a game JAR, and peer-review deliverables. Together, these provide material for examining both software behavior and the team's design process.

**Review route.** Begin with the repository README and delivery material, then compare the UML with `src/main/` and inspect `src/test/`. The features listed here describe the group result rather than an attribution of every component to one author.

#### RAM Sequence Processing FSM

**Repository:** [cicixgliamici/RetiLogiche_2024](https://github.com/cicixgliamici/RetiLogiche_2024)  
**Course:** Digital Logic Design (*Reti Logiche*)  
**Context:** Two-person project with Enrico James Busato  
**Technology:** VHDL, finite-state machines, Vivado

**Purpose and artifact.** Design a hardware controller that reads a sequence from RAM, replaces zero values according to the specification, updates associated credibility values, and writes results back to memory.

**Engineering focus.** Explicit state transitions, clocked memory interaction, reset behavior, and boundary cases connect the algorithm to synchronous hardware constraints.

**Review route.** Read the processing specification, trace the FSM implementation, and inspect the supplied testbenches and synthesis material. Functional simulation and synthesis/timing evidence answer different questions and should be examined separately.

#### Bakery Management System

**Repository:** [cicixgliamici/Algoritmi-StruttureDati_2024](https://github.com/cicixgliamici/Algoritmi-StruttureDati_2024)  
**Course:** Algorithms and Foundations of Computer Science (*Algoritmi e Principi dell'Informatica*)  
**Context:** Academic year 2023–2024  
**Technology:** C, hash tables, heaps, queues, linked lists

**Purpose and artifact.** Simulate ingredient inventory, recipes, pending orders, and truck shipments under ordering and expiration constraints.

**Engineering focus.** Data structures are selected around operations: ingredient lookup, expiration handling, pending-order processing, and shipment prioritization. The project connects algorithmic choices to manual memory management and implementation constraints.

**Review route.** Read the repository's source map, inspect the data structures and order-processing modules, then compare behavior with the supplied input/output cases. Historical versions provide development context; start with the documented main implementation.

## Paper Implementations & Formalizations

These projects begin with published technical work. The source ideas belong to the cited authors; my work concerns their implementation, formalization, adaptation, and evaluation within each repository's stated scope.

### Abstracting Abstract Machines

**Repository:** [cicixgliamici/abstracting-abstract-machines](https://github.com/cicixgliamici/abstracting-abstract-machines)  
**Foundation:** *Abstracting Abstract Machines* — David Van Horn and Matthew Might  
**Stack:** OCaml, Dune, opam; Python experiment tooling

**Purpose.** Study how a concrete evaluator becomes a conservative higher-order program analysis through store allocation and finite addresses.

**Implemented artifact.** The project follows the progression from pure CEK execution to a fresh store-allocated machine and finite-address abstract analysis. It also explores state/control extensions and deterministic garbage collection.

**Implementation-study contributions.** An independent pure substitution evaluator, generated tests, explicit correctness arguments, worked traces, and reproducible experiments supplement the paper-based construction. Artifact checksums identify the supplied source/documentation/result payload.

**Evidence.** Tests examine machine correspondence, local abstract simulation, reachability, GC, and independent evaluation. Experiments compare allocation policies and GC configurations, distinguishing graph size, store footprint, precision proxies, timing, and completion under resource limits.

**Scope.** Correctness arguments are informal rather than machine-checked proofs of the executable. Fuel exhaustion does not establish divergence, and an abstract final state does not establish concrete termination. Larger address pools do not guarantee that an experiment finishes within its budget.

**Review route.** Read `WALKTHROUGH.md`, `PAPER_TO_CODE.md`, `CORRECTNESS.md`, and `VALIDATION.md`; inspect `lib/store_machine.mli` and its implementation. Follow `EXPERIMENTS.md` for results and `ARTIFACT.md` for payload verification.

### A Weak Silly Substitution Calculus

**Repository:** [cicixgliamici/a-weak-Silly-substitution-Calculus](https://github.com/cicixgliamici/a-weak-Silly-substitution-Calculus)  
**Foundation:** *Mirroring Call-by-Need, or Values Acting Silly* — Beniamino Accattoli and Adrienne Lancelot  
**Stack:** Lean 4, Lake

**Purpose.** Mechanize a fragment of the paper's weak Silly Substitution Calculus and make the relationship between syntax, operational rules, and proofs explicit.

**Implemented artifact.** The library includes named terms, explicit substitutions, free-variable infrastructure, freshness and capture-avoiding substitution, contexts, labelled root rules, and weak closures. It formalizes the Call-by-Silly strategy and proves its inclusion in generic weak reduction.

**Formalization contribution.** The development includes a bidirectional weak-normal-form characterization, checked examples, regression tests, and a document mapping implemented definitions and results to the paper.

**Scope.** This is a growing formalization of an existing calculus. It does not claim the full paper development; multi-step infrastructure, postponement results, and confluence infrastructure remain subsequent milestones.

**Review route.** Start with `docs/paper-implementation.md`, then inspect `SSC/Syntax.lean`, `SSC/Reduction.lean`, `SSC/Strategy.lean`, and `SSC/Theorems/`. Run `lake build` to check the library, examples, and tests.

### SimHash Logs

**Repository:** [cicixgliamici/simhash-logs](https://github.com/cicixgliamici/simhash-logs)  
**Foundations:** Charikar's *Similarity Estimation Techniques from Rounding Algorithms*; Manku, Jain, and Das Sarma's *Detecting Near-Duplicates for Web Crawling*  
**Stack:** Go, CLI, unit and integration tests

**Purpose.** Adapt similarity fingerprints and candidate-generation methods to noisy system logs.

**Implemented artifact.** The pipeline normalizes variable fields, tokenizes messages, computes 64-bit SimHash fingerprints, and verifies near-duplicate matches using Hamming distance. Search options include a brute-force baseline, an LSH-style band index, a historical heuristic permutation index, and a Manku-style pigeonhole prefix index.

**Adaptation and evidence.** Log normalization and configurable weighting connect the literature to a practical use case. The evaluation command compares candidate indexes against brute-force ground truth and exports parameter sweeps for analysis.

**Scope.** The baseline pipeline and candidate-generation prototype are implemented. Persistent storage, streaming ingestion, larger external benchmarks, and production observability integrations remain outside the current scope. The historical heuristic and paper-faithful index are distinguished explicitly.

**Review route.** Follow `internal/normalize/`, `internal/tokenize/`, `internal/simhash/`, and `internal/search/`. Run `go test ./...` and reproduce an evaluation from the README.

### RFR-HJM-FMM

**Repository:** [cicixgliamici/rfr-hjm-fmm](https://github.com/cicixgliamici/rfr-hjm-fmm)  
**Foundation:** *Alternative Risk-Free Rates and the New Indexation Framework: An Analysis of Compounded Overnight Rates with Applications to FRNs and Swaps*  
**Stack:** Python, numerical models, pytest

**Purpose.** Explore the mathematical and computational structure of compounded overnight risk-free-rate instruments.

**Implemented artifact.** The project provides deterministic OIS discounting, extended forward rates, FRN and payer-swap pricing, par swap rates, DV01, and convexity. Generalized FMM and Markovian HJM scaffolds form a basis for subsequent stochastic work.

**Scope.** Deterministic pricing and tested scaffolds do not constitute the completed coupled stochastic model. Pathwise pricing, the monthly simulation experiment, paper risk-table reproduction, and calibration remain future work.

**Review route.** Begin with the README's status boundary, inspect `src/rfr_hjm_fmm/`, and run the examples and validation suite before examining the model scaffolds.

### NASA Power of Ten Demo

**Repository:** [cicixgliamici/nasa-power-of-ten-demo](https://github.com/cicixgliamici/nasa-power-of-ten-demo)  
**Foundation:** NASA/JPL's *The Power of Ten: Rules for Developing Safety-Critical Code*  
**Stack:** C, Make, tests, ACSL contracts, optional Frama-C tooling

**Purpose.** Turn engineering guidelines into explicit implementation constraints and inspectable evidence.

**Implemented artifact.** A fixed-size ring buffer provides bounded memory, simple control flow, explicit status handling, invariants, and meaningful empty/full/wrap-around cases.

**Engineering contribution.** Rule-to-code mapping, compliant/non-compliant examples, tests, contracts, and a lightweight safety case explain how the guidelines influence design decisions.

**Scope.** This is an engineering study, not a certified safety-critical library. Formal and static-analysis paths depend on the documented tools; their evidence must be distinguished from the ordinary build and unit tests.

**Review route.** Inspect `include/ring_buffer.h`, `src/ring_buffer.c`, and `tests/test_ring_buffer.c`, then read the verification matrix and contract documentation. Use `make review` for the standard reviewer path.

## Independent Explorations

These projects investigate a question or build a tool outside the coursework and paper-implementation categories above. Their scope ranges from focused libraries to simulation prototypes and comparative studies.

### cnumkit

**Repository:** [cicixgliamici/cnumkit](https://github.com/cicixgliamici/cnumkit)  
**Area and stack:** Numerical computing; C11, CMake

A small scientific-computing library exploring predictable APIs, explicit ownership, borrowed vector/matrix views, runtime error handling, and numerical reasoning. Modules cover scalar kernels, dense linear algebra, optimization helpers, and simple one-dimensional ML utilities.

**Evidence and scope.** Examples and mathematical scenario tests connect individual operations to complete calculations. Build configurations cover strict warnings, static/shared libraries, contracts, and sanitizers. The scalar implementation is educational; it does not aim to replace BLAS or LAPACK. RISC-V is a documented direction, and RVV acceleration is future work.

**Review route.** Read `docs/USER_GUIDE.md`, `docs/BORROWED_KERNELS.md`, and `docs/NUMERICAL_NOTES.md`; inspect public headers and scenario tests. Follow the README's CMake/CTest commands.

### Post-Crisis Collective Decision Simulator

**Repository:** [cicixgliamici/fallout-decision-making](https://github.com/cicixgliamici/fallout-decision-making)  
**Area and stack:** Collective decision-making; Python simulation

A Fallout-inspired isolated-colony model asks when delegation improves material outcomes under scarcity, and how it affects preference satisfaction and concentration of voting power.

**Implemented artifact.** Community members estimate needs, rank policies, vote or delegate, and experience resource and health consequences. The simulator compares first-choice plurality, approval, expert delegation, and bounded-chain liquid democracy under explicit scenario assumptions.

**Evidence and scope.** Documented study assumptions, reproducible scenarios, reports, and event logs make the model inspectable. Outcomes describe the simulated rules and assumptions; they are not predictions about real communities. Strategic voting, coalitions, and equilibria are future extensions.

**Review route.** Start with `docs/walkthrough.md`, `docs/research_basis.md`, `docs/study_protocol.md`, and `docs/current_results.md`; use `docs/code_guide.md` to follow the implementation.

### C++ Netprobe

**Repository:** [cicixgliamici/cpp-netprobe](https://github.com/cicixgliamici/cpp-netprobe)  
**Area and stack:** Packet analysis; C++20, libpcap, CMake, Doctest

A layered packet analyzer reads capture files or live traffic and produces structured protocol reports. Individual parsers consume byte spans and return typed results or an explicit failure for malformed/truncated input.

**Engineering focus.** Protocol layering, byte order, header lengths, zero-copy views, and parser failure behavior connect networking concepts to systems programming. Supported paths include Ethernet, IPv4/IPv6, ARP, and selected transport/control protocols, with BPF filtering.

**Scope and review route.** Evaluate the documented protocol coverage rather than assuming complete network-stack behavior. Inspect `include/netprobe/`, `src/`, and `tests/`, then build with CMake and run CTest using the README instructions.

### Vehicle Dynamics KPI Toolbox

**Repository:** [cicixgliamici/vehicle-dynamics-kpi-toolbox](https://github.com/cicixgliamici/vehicle-dynamics-kpi-toolbox)  
**Area and stack:** Vehicle dynamics and signal processing; MATLAB

A pipeline for loading measurements, preprocessing signals, detecting maneuvers, extracting handling/ride KPIs, and exporting results. It includes spectral analysis, bicycle-model comparisons, and a linear Kalman filter for sideslip estimation.

**Evidence and scope.** Synthetic maneuvers and tests connect numerical outputs to stated physical models. The linear assumptions and synthetic validation define the interpretation of the results. Nonlinear tyre models, an EKF extension, and standardized frequency-weighted ride scoring remain roadmap items.

**Review route.** Read `docs/ARCHITECTURE.md` and `docs/MATH_REFERENCE.md`, run the single-maneuver example, and inspect `tests/ToolboxTest.m` and the robustness-validation script.

### Environmental Telemetry Risk Pipeline

**Repository:** [cicixgliamici/env-telemetry-risk-pipeline](https://github.com/cicixgliamici/env-telemetry-risk-pipeline)  
**Area and stack:** Applied ML and data validation; Python, pytest, Docker

A small pipeline validates environmental telemetry, profiles data quality, creates features, compares baseline classifiers, performs batch prediction, and detects anomalies with Isolation Forest.

**Evidence and scope.** Generated metrics, model metadata, reports, and deterministic synthetic-data generation support reproducible review. The bundled dataset is small: model metrics provide pipeline smoke evidence rather than validated field performance.

**Review route.** Read the dataset card, model card, and modeling notes under `docs/`; run validation and tests before reproducing training, prediction, or anomaly detection.

### Keywords in Languages

**Repository:** [cicixgliamici/keywords-in-languages](https://github.com/cicixgliamici/keywords-in-languages)  
**Area and stack:** Comparative language study; CSV corpus, Python validation and notebooks

A source-backed corpus investigates how reserved and contextual tokens distribute semantic responsibilities across C, C++, Rust, Go, and Scala.

**Study contribution.** The dataset distinguishes lexical status, aliases, versions, and semantic annotations. Validation and generated findings make the static comparison reproducible.

**Scope.** Keyword counts are not interchangeable measures of language complexity. Independent annotation reliability remains planned; historical coverage is provisional and real-program usage analysis has not started.

**Review route.** Inspect `data/keywords.csv`, `data/sources.csv`, `docs/TAXONOMY.md`, and `docs/FINDINGS_PHASE1.md`, then run the documented validation and notebook checks.

## Learning Resources & Study Notes

These repositories organize study rather than deliver one application. Their value lies in the clarity of explanations, progression of exercises, and connection between written claims and executable examples.

### Quantum-Ed

**Repository:** [cicixgliamici/quantum_ed](https://github.com/cicixgliamici/quantum_ed)  
**Focus:** Quantum computing, information, and verifiable simulation

Mathematical notes, eight notebooks, a NumPy toolkit, and experiments connect states, gates, measurement, entanglement, mixed states, noise, and quantum communication.

**Material to inspect.** The Bell-pair noise study compares independent NumPy and PennyLane implementations against analytical predictions, with generated data and figures. It illustrates why unchanged measurement probabilities or recovered purity do not by themselves imply preserved entanglement.

**Review route.** Begin with `docs/reviewer-guide.md`, the Bell-noise study, and `experiments/README.md`, then inspect the underlying toolkit and tests. Idealized simulations should be read within their stated mathematical and hardware assumptions.

### Programming Languages

**Repository:** [cicixgliamici/ProgrammingLanguages](https://github.com/cicixgliamici/ProgrammingLanguages)  
**Focus:** Languages, paradigms, frameworks, and proof assistants

Structured tracks cover C, Java, Python, Scala, Lean, Coq, and selected application ecosystems. Track READMEs distinguish executable lessons from planned material and describe prerequisites and learning objectives.

**Review route.** Choose one track, follow its lesson order, inspect examples and exercises, and run its documented checks. Repository-wide verification distinguishes missing toolchains from failing checks; strict verification requires all supported toolchains.

### System Design

**Repository:** [cicixgliamici/System_design](https://github.com/cicixgliamici/System_design)  
**Focus:** Distributed systems and architecture reasoning

Theory guides, architectural case studies, exercises, runnable Go/Python/TypeScript modules, and benchmarks connect concepts such as caching, retries, messaging, replication, and concurrency to inspectable examples.

**Review route.** Pair a theory chapter with its implementation and tests, then inspect the benchmark methodology. Case studies are design exercises, while local modules and measurements provide evidence for their own documented behavior and environment.

### Meta Projects

**Repository:** [cicixgliamici/meta-projects](https://github.com/cicixgliamici/meta-projects)  
**Focus:** Git, software delivery, CI/CD, containers, and infrastructure

Notes and practical labs explain development and delivery workflows. Material includes a Python API, CI examples, Docker, Kubernetes/Helm, Terraform examples, and testing exercises.

**Review route.** Follow a concept from `docs/` into its corresponding lab or configuration. Treat deployment configurations as learning artifacts whose suitability depends on the documented environment.

### LeetCode Solutions

**Repository:** [cicixgliamici/leetcode](https://github.com/cicixgliamici/leetcode)  
**Focus:** Algorithm practice and complexity analysis

A multi-language solution archive organized by difficulty, with supporting practice tracks and reference notes. Maintenance tooling validates structure and derives indexes/statistics from metadata.

**Scope and review route.** Normalization is ongoing: some problems still need metadata or explanations. Select a documented problem and inspect the approach, complexity analysis, and implementation together; consult the repository tooling for archive consistency.

---

## Academic Context

The [full academic coursework](./education.md) complements this portfolio with the subjects studied during both degrees. The project categories explain the origin of each artifact; the coursework provides the broader mathematical, theoretical, and engineering context.

My current direction connects **programming languages, logic, formal methods, and quantum computing**, including preparation for a thesis on quantum computing and logic.