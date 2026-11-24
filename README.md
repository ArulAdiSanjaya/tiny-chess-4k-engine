[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/ArulAdiSanjaya/tiny-chess-4k-engine/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/ArulAdiSanjaya/tiny-chess-4k-engine/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# Tiny Chess 4K

A chess engine in at most 4,096 bytes of Python, entered in
[make.fun's tiny-chess-01 bounty](https://make.fun/bounty/tiny-chess-01).
`main.py` is the whole engine; it talks to the bounty env at
`MAKEFUN_ENV_URL` and plays the house gauntlet game after game.

## How it plays

- 0x88 board with incremental material + piece-square score and Zobrist
  hashing maintained in make/unmake.
- Negamax with PVS, iterative deepening to a fixed budget of 120,000
  nodes a move (never a clock, so replays match move for move).
- Transposition table, check extensions, null-move pruning, late-move
  reductions, killer moves and history ordering, MVV-LVA captures.
- Quiescence over captures and promotions, with full evasions when in
  check; repetitions and the fifty-move rule score as draws.
- Tapered evaluation: material, midgame/endgame piece-square tables for
  all six pieces, and the bishop pair.

The committed `main.py` is the readable engine source packed by
`makefun compress` (an LZMA payload with its unpacker); the packer and
the payload together are what the 4,096-byte cap measures.

## License

MIT — see `LICENSE`.

<sub>Entered on [make.fun](https://make.fun/?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
