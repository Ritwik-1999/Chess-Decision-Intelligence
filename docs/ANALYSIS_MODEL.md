# Analysis Model

Each analyzed node should contain more than a centipawn score.

The goal is to represent both **objective engine strength** and **practical character**.

## Node Structure

Conceptual example:

```json
{
  "fen": "...",
  "move": "Bc4",
  "evaluation_cp": 48,
  "wdl": {
    "win": 41,
    "draw": 44,
    "loss": 15
  },
  "style": [
    "attacking",
    "tactical",
    "initiative"
  ],
  "metrics": {
    "attack": 8.2,
    "tactical_richness": 7.4,
    "safety": 5.1,
    "complexity": 8.0,
    "forgiveness": 4.2
  }
}
```

## Engine Evaluation

Stockfish remains authoritative for:

- best move
- candidate move ordering
- principal variation
- centipawn evaluation
- mate scores
- W/D/L estimation

## Tactical Richness

Potential inputs:

- checks
- captures
- sacrifices
- forcing moves
- attacked queens
- forks
- pins
- discovered attacks
- hanging pieces
- evaluation swings

## Attack Score

Potential inputs:

- pressure around the enemy king
- pieces entering attacking zones
- open lines toward the king
- pawn advances near the king
- checks and forcing threats
- loss of defensive pieces

## Safety Score

Potential inputs:

- own king exposure
- tactical instability
- number of reasonable continuations
- evaluation volatility
- hanging pieces
- structural weaknesses

## Complexity

A position can be treated as more complex when:

- evaluation varies sharply between candidate moves
- tactical motifs are dense
- many forcing lines exist
- the position is materially or structurally unbalanced
- accurate move ordering matters significantly

## Forgiveness

Forgiveness estimates how badly a player is punished for failing to find the strongest continuation.

Example:

```text
Position A
Move 1: +0.40
Move 2: +0.35
Move 3: +0.31
Move 4: +0.25
```

This position is relatively forgiving.

```text
Position B
Move 1: +1.20
Move 2: -0.70
Move 3: -1.40
Move 4: -2.10
```

This position is highly unforgiving.

## Resulting-Position Classification

Move classification and resulting-position classification are intentionally separate.

Example:

```text
Move:
Developing, tempo-gaining

Resulting position:
Sharp, kingside attacking, high complexity
```

This distinction prevents a quiet-looking move from being incorrectly labeled as producing a quiet game.
