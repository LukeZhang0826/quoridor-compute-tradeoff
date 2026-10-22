# Quoridor: trading train-time compute for test-time compute

SYDE 522 final project. A game-playing agent can spend compute before play, training a
model on data prepared in advance, or during play, searching the game tree at every
decision. This repo measures the exchange rate between the two on 5x5 Quoridor with
three walls per player.

## Status

Engine only so far:

- bitmask board state, wall geometry, and move legality including pawn jumps
- BFS wall-legality check (no wall may cut a player off from their goal row)
- uniform random move sampling that defers the BFS until a wall is actually drawn
- call counters on the successor function and the path check, which are the units
  all compute costs are reported in

1000 random playouts run in about 2 seconds. Player 1 wins roughly half of them, so
the reduced board is not lopsided.

## Planned agents

1. MCTS with random rollouts (all compute at decision time, no training)
2. A policy network trained on MCTS visit-count labels (all compute before play)
3. The same network used as a move prior inside MCTS (split between the two)
4. A non-neural learner on the same labels, as a control on model class

## Layout

`Quoridor.ipynb` holds the engine. Course handouts and submitted PDFs are gitignored.
