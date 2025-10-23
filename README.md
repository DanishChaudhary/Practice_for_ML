# Practice_for_ML

[![Status](https://img.shields.io/badge/status-active-brightgreen)]() 
[![License](https://img.shields.io/badge/license-MIT-blue.svg)]() 
[![Repo](https://img.shields.io/badge/repo-DanishChaudhary/Practice_for_ML-000000?logo=github)]()

> A disciplined log of practice problems, experiments and concept notes for Machine Learning and supporting algorithms.  
> The repo is organized so every problem, experiment and concept is reproducible, testable and easy to review.

## Why this repo exists (short)
You're not saving one-off scripts. You’re building a searchable, versioned record of how you learned — problems attempted, solutions shipped, and concept notes that scale into projects. This repo is the single source of truth for that process.

What this really means is:
- Each problem has: statement, input/output examples, clean solution(s), and a small test suite.
- Each concept has: concise notes, references, runnable examples and a minimal experiment.
- Everything is structured so reviewers (you in 6 months included) can jump straight to a working example.

---

## Table of contents
- [Repo structure](#repo-structure)  
- [Conventions](#conventions)  
- [How to add a problem / concept / experiment](#how-to-add)  
- [How to run & test locally](#run)  
- [CI / quality gates](#ci)  
- [Contribution guidelines (short)](#contribute)  
- [License & contact](#license)

---

## Repo structure

├─ README.md
├─ CONTRIBUTING.md
├─ requirements.txt # python deps for experiments & tests
├─ problems/ # solved practice problems (by topic)
│ ├─ algorithms/
│ │ ├─ 001-two-sum/
│ │ │ ├─ README.md # problem statement, complexity, approach
│ │ │ ├─ solution.py
│ │ │ ├─ test_solution.py
│ │ │ └─ data/ # optional example inputs
│ ├─ dynamic-programming/
│ └─ ...
├─ concepts/ # notes & runnable examples
│ ├─ linear-regression/
│ │ ├─ notes.md
│ │ ├─ demo.ipynb
│ │ └─ requirements.txt
│ └─ ...
├─ experiments/ # quick experiments, small notebooks
├─ notebooks/ # general notebooks
└─ .github/
├─ workflows/ci.yml
├─ ISSUE_TEMPLATE.md
└─ PULL_REQUEST_TEMPLATE.md


---

## Conventions (read this)
Short, strict rules so the repo stays usable:

- **Naming**: `problems/<topic>/<zero-padded-id>-short-title/`  
  Example: `problems/algorithms/001-two-sum/`
- **Each problem folder must contain**:
  - `README.md` (statement, constraints, complexity)
  - `solution.*` (one or more clean solutions)
  - `test_solution.*` (unit tests that validate correctness)
- **Language**: Use the language that makes the solution clear (Python preferred for ML/concepts). If you use Java or C, add a `README.md` describing how to build.
- **Code style**:
  - Python: type hints, `black` formatting, `pytest` for tests.
  - Java: single public class per file, clear method-level comments.
- **Commits**: Use clear messages — prefer `type(scope): short description`. Example: `feat(dp): add memoized knapsack solution`.
- **Branches**: `main` (stable), `dev` (integration), `feature/<short>` for work.
- **Tests**: Every solution must be backed by at least one deterministic unit test.

---

## How to add a problem / concept / experiment
Here's the exact workflow I expect:

1. Create folder: `problems/<topic>/<id>-<short-title>/`
2. Add `README.md` with:
   - Problem statement (copied + link)
   - Constraints and edge cases
   - Complexity (time, space)
   - Approach summary (1–3 lines)
3. Add `solution.py` (or `solution.java`) — clear, commented, type-hinted.
4. Add `test_solution.py` (pytest) — include edge cases and typical cases.
5. Run tests locally and then push a branch `feature/<id>-<short>` and open PR to `dev`.

If it's a concept:
- Put under `concepts/<concept-name>/`
- Add `notes.md` summarizing intuition + formulas + pitfalls.
- Add runnable examples (script or notebook).

---

## README template for a problem (paste into each problem `README.md`)
```md
# 001 — Two Sum

**Source:** LeetCode 1 (link)  
**Difficulty:** Easy  
**Constraints:** n <= 10^5, values can be negative  
**Goal:** Return indices of two numbers that add up to target.

## Approach
- Hash map: one-pass, store complement -> index.
- Time: O(n), Space: O(n)

## Edge cases
- Duplicate values, negative numbers, no-solution case.

## Files
- `solution.py` — final solution
- `test_solution.py` — pytest tests

How to run & test locally

Here's what works on any machine:

# clone
git clone https://github.com/DanishChaudhary/Practice_for_ML.git
cd Practice_for_ML

# python env (recommended)
python -m venv .venv
source .venv/bin/activate      # Linux/Mac
.venv\Scripts\activate         # Windows

pip install -r requirements.txt

# run all tests
pytest -q

# run a single problem's test
pytest problems/algorithms/001-two-sum/test_solution.py -q
