[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/taozhupipi/makefun-tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/taozhupipi/makefun-tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# tiny-chess-01

A 4 KB chess engine in Python (stdlib only) for the [make.fun tiny-chess-01 bounty](https://make.fun/bounty/tiny-chess-01).

## Engine

- 0x88 board, negamax with alpha-beta and PVS
- Transposition table, quiescence search (captures/promotions, check evasions)
- Move ordering: TT move first, MVV-LVA captures, promotions
- Tapered piece-square evaluation (PeSTO tables), fixed node budget per move
- Deterministic: fixed node count, no clock, no randomness

`main.py` is a compressed self-extracting payload (lzma + base85) that
unpacks to the full engine at import time; the payload and its unpacker
together stay within the 4,096-byte limit.

## Practice results

Practice trial 0 against the six practice gauntlet engines: **Elo 1545**
(4 wins, 1 draw, 1 loss).

- Wins by checkmate vs depth-2, depth-3, depth-4 and nodes-100k
- Draw vs nodes-250k by threefold repetition
- Loss vs nodes-500k by checkmate

That is about 180 Elo above the sunfish house baseline (~1365) and well
above the 1,154 qualification bar. Move generation is verified by perft:
start position 20/400/8902/197281, Kiwipete 48/2039/97862.

## License

MIT — see [LICENSE](LICENSE).
