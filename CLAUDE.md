# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Educational AI project (Ukrainian language) implementing machine learning models from scratch. Currently: a single-layer perceptron binary classifier that identifies Семеріков based on facial features.

## Deliverable

**`index.html`** — single self-contained file (HTML + CSS + JS, no dependencies). Open directly in any browser; must produce zero console errors and zero network requests.

## Model Specification

- **Inputs:** x1–x5 (features) + x6=1 (bias term)
- **Weighted sum:** S = w1·x1 + w2·x2 + w3·x3 + w4·x4 + w5·x5 + w6
- **Activation:** sign function — y = +1 if S > 0, y = -1 if S ≤ 0
- **Learning rule (bipolar):** delta = y_target − y_hat (±2 on error), w[i] += η·delta·x[i]
- **Convergence check:** 0 errors across a complete 4-sample epoch

## Training Data (`data/2026_03_17.ods`)

| Особа      | x1 | x2 | x3 | x4 | x5 | x6 | y  |
|------------|----|----|----|----|----|----|-----|
| Семеріков  | -1 | -1 | -1 | -1 | -1 |  1 | +1 |
| Лисенко    | +1 | +1 | -1 | +1 | +1 |  1 | -1 |
| Журавкова  | -1 | -1 | +1 | -1 | +1 |  1 | -1 |
| Осипчук    | -1 | -1 | +1 | -1 | -1 |  1 | -1 |

Features: x1=Окуляри, x2=Борода та вуса, x3=Довге волосся, x4=Чорно-біле, x5=Темний колір волосся.

**Known convergence:** with zero initial weights and η=1, converges in exactly 2 epochs. Final weights: [0, 0, −4, 0, −4, 0].

## Architecture of index.html

Six sections (A–F):
- **A. Header** — title + subtitle
- **B. SVG diagram** — 6 input nodes (x1–x5 + bias) → Σ node → F(S) box → y output; weight lines update color (blue=positive, red=negative) and thickness dynamically
- **C. Training data table** — live ✓/✗ prediction column, row highlighting during training
- **D. Training controls** — buttons (Ініціалізувати/Крок навчання/Епоха/Навчити/Зупинити/Скинути), η spinner, speed slider, status display
- **E. Computation log** — dark terminal-style scrollable area, one entry per training step (input vector, weighted sum with substituted values, activation, error/update)
- **F. Prediction panel** — 5 CSS toggle switches (є/немає), real-time S and y calculation display

JavaScript is structured as pure functions (`wsum`, `act`, `predict`, `trainStep`) plus UI updaters (`updDiagram`, `updTable`, `updStatus`, `updPred`). `trainStep()` returns a result object used by both the log renderer and the UI refresh.

## Other Data Files

- **`data/Housing.csv`** — likely for a future linear regression exercise (not yet used)
- **`data/2026-03-17-Note-12-29_annotated.pdf`** — handwritten lecture notes with the perceptron diagram and formulas

## Language and Conventions

- All user-facing text, comments, and documentation in Ukrainian.
- Educational priority: clarity and step-by-step explanations over optimization.
- No build tools, no package managers, no external fonts or libraries.
