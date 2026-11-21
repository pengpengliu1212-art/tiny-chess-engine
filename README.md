# tiny-chess-engine

[![make.fun](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/pengpengliu1212-art/tiny-chess-engine/rank.svg)](https://make.fun/bounty/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/pengpengliu1212-art/tiny-chess-engine/reward.svg)](https://make.fun/bounty/tiny-chess-01)

An entry for the [make.fun](https://make.fun/bounty/tiny-chess-01)
tiny-chess-01 bounty: the strongest chess engine in 4 KB of Python.

`main.py` is the whole engine (4,064 bytes, Python 3.13 stdlib
only). It is an original engine: 0x88 board, negamax alpha-beta with
iterative deepening, a fixed 80,000-node budget per move, Zobrist
transposition table (cleared each game), MVV-LVA + killer + history
move ordering, quiescence search (no stand-pat while in check),
null-move pruning, LMR, futility pruning, score-aware contempt for
draws (repetition and 50-move score -25 only when the static
evaluation favours the side to move, 0 otherwise), and a tapered
piece-square-table evaluation with a separate endgame pawn table.
The piece-square tables are original values, written for this
engine; the middlegame pawn table scores an unmoved central pawn
(d2/e2) at -5. No clock is used anywhere, so replays play identical
moves. A failed `/move` call is retried with a different legal move
instead of exiting.

Practice Elo on the kit's three practice trials: 1654 / 1545 / 1545
(14.0/18 points, mean 1581) against the house gauntlet, above the
sunfish baseline (1364 / 1451 / 1279 on the same trials).

Head-to-head against sunfish at 50,000 nodes per move (12 games,
trial-0 openings, both colours): 5 wins, 3 draws, 4 losses
(6.5/12). Slowest move in the match was 2,324 ms.
