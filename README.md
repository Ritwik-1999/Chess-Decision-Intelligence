# Chess Decision Intelligence

An interactive chess analysis platform focused on understanding **what to play, why it works, and what kind of position it leads to**.

The project analyzes a given chess position, calculates strong continuations for both sides, and presents them as an explorable decision tree. Beyond engine evaluation, each line is evaluated for practical characteristics such as tactical complexity, attacking potential, safety, defensive value, risk, and overall playability.

The goal is to make engine analysis more useful for **opening preparation and midgame improvement**, where understanding plans and candidate moves matters more than simply knowing the engine's first choice.

## What I'm Building

* Multi-line position analysis using Stockfish
* Candidate move generation with configurable search depth
* Interactive continuation trees for both sides
* Win / draw / loss probabilities for analyzed positions
* Line classification including:

  * Attacking
  * Defensive
  * Tactical
  * Positional
  * Safe / Solid
  * Forcing
  * High-risk / Complex
* Position-level analysis for:

  * King safety
  * Material balance
  * Development
  * Pawn structure
  * Weak squares
  * Piece activity
  * Open files and positional pressure
* Comparison between objectively strongest moves and more practical alternatives
* PGN and FEN based position input
* Opening-focused analysis for studying recurring middlegame structures

## Planned Analysis Flow

```text
PGN / FEN
    ↓
Position Parser
    ↓
Stockfish Analysis
    ↓
Top Candidate Moves
    ↓
Continuation Tree
    ↓
W/D/L + Evaluation
    ↓
Positional Feature Analysis
    ↓
Line Classification
    ↓
Interactive Training View
```

## Tech Stack

**Backend**

* Python
* FastAPI
* python-chess
* Stockfish / UCI

**Frontend**

* React / Next.js
* Interactive chessboard UI

**Data**

* SQLite initially
* PostgreSQL as analysis and training data grows

## Why Build This?

Traditional engine analysis is extremely good at answering:

> What is the best move?

This project is aimed at answering a broader set of questions:

> What are my realistic candidate moves?

> What does each move lead to?

> Which line is safer or more tactical?

> What is each side trying to achieve?

> How difficult is the resulting position to play?

That distinction is especially useful when studying openings and trying to improve positional awareness in the middlegame.

## Status

Currently under active development.

Initial work is focused on the analysis engine, MultiPV continuation generation, position evaluation, and the data model for representing variation trees.

