# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Educational AI project (Ukrainian language) implementing a perceptron from scratch. The goal is to build a binary classifier that identifies a person (Семеріков) based on facial features.

## Current State

No code exists yet. The `data/` directory contains:
- **`2026_03_17.ods`** — Training dataset with 4 samples, 5 binary features (Окуляри, Борода та вуса, Довге волосся, Чорно-біле, Темний колір волосся), plus bias. Features encoded as -1/+1, target y: +1 for Семеріков, -1 for others.
- **`2026-03-17-Note-12-29_annotated.pdf`** — Handwritten lecture notes defining the perceptron model.

## Model Specification (from notes)

- **Inputs:** x1–x5 (features) + x6=1 (bias term)
- **Weighted sum:** S = w1·x1 + w2·x2 + w3·x3 + w4·x4 + w5·x5 + w6
- **Activation:** sign function — y = +1 if S > 0, y = -1 if S ≤ 0
- **Architecture:** Single-layer perceptron (no hidden layers)

## Language and Conventions

- All user-facing text, comments, and documentation should be in Ukrainian unless otherwise requested.
- The project is educational — prioritize clarity and step-by-step explanations over optimization.
