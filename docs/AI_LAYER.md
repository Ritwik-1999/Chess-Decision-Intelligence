# AI Reasoning Layer

The AI layer is used to make engine analysis understandable.

It is deliberately separated from move calculation.

## Principle

```text
Engine decides.
Features describe.
AI explains.
```

Stockfish determines which moves are strongest.

The reasoning layer receives:

- current FEN
- candidate moves
- principal variations
- engine evaluations
- W/D/L values
- extracted positional features
- tactical signals
- style metrics

The AI layer then converts that information into concise human-readable analysis.

## Responsibilities

### Strategic explanation

Example:

```text
Nd5 improves the least active piece and creates a stable central outpost.
Black has no pawn that can easily challenge the knight, while c7 and f6
become immediate targets.
```

### Candidate comparison

Example:

```text
Bc4 is more forcing and preserves attacking momentum.
Nc3 is safer and more forgiving, but gives Black more time to consolidate.
```

### Plan extraction

When the same idea appears across multiple strong engine lines, the system can surface it as a recurring positional plan.

Examples:

- establish a knight on d5
- open the center before the opponent castles
- pressure f7
- trade the opponent's strongest attacking piece
- prepare a central pawn break

### Training prompts

Examples:

```text
What are the three most reasonable candidate moves here?

Which move preserves the initiative?

Which continuation is safest?

What is Black's main defensive idea?
```

## Guardrails

The AI layer should not:

- invent engine evaluations
- override Stockfish move ranking
- fabricate W/D/L values
- claim tactical motifs that are not supported by board state or engine output

This keeps natural-language reasoning grounded in deterministic chess analysis.
