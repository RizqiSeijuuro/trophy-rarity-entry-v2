# trophy-rarity-entry-v2

[![make.fun · gta6-trophy-rarity-forecast-01](https://make.fun/badge/gta6-trophy-rarity-forecast-01.svg)](https://make.fun/bounty/gta6-trophy-rarity-forecast-01?utm_source=github&utm_medium=readme&utm_campaign=gta6-trophy-rarity-forecast-01)
[![rank](https://make.fun/badge/gta6-trophy-rarity-forecast-01/RizqiSeijuuro/trophy-rarity-entry-v2/rank.svg)](https://make.fun/bounty/gta6-trophy-rarity-forecast-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=gta6-trophy-rarity-forecast-01)
[![reward](https://make.fun/badge/gta6-trophy-rarity-forecast-01/RizqiSeijuuro/trophy-rarity-entry-v2/reward.svg)](https://make.fun/bounty/gta6-trophy-rarity-forecast-01?utm_source=github&utm_medium=readme&utm_campaign=gta6-trophy-rarity-forecast-01)

This entry forecasts each GTA VI PS5 trophy's Exophase earn rate with a per-trophy, recency-weighted
least-squares trend of logit(rate) against log(1 + hours since that trophy's first read), rather than the
house baseline's flat persistence call. The fitted slope is shrunk toward zero in proportion to how few
reads back it (n / (n + 4)), extrapolated to the case's target with the resulting move clamped to a bound
that scales with the square root of the horizon (so a noisy short trend can't run away over a long
horizon), and turned into five quantiles by combining the house baseline's own random-walk spread with a
second term built from the trend fit's residual uncertainty, widened further when the horizon reaches past
the span of history the trend was fit on. The result tracks a trophy that is clearly trending up or down
more closely than persistence while falling back to persistence-like behavior, with a widened spread, when
a trophy's history is too thin or too flat to support a real trend. Standard library only, no network.

To test locally, point it at a copy of the kit's practice cases and check the output shape:

```
mkdir -p out && MAKEFUN_INPUT_DIR=input MAKEFUN_OUTPUT_DIR=out python3 main.py
```

`input/` should hold the kit's `*.in` practice cases; this writes one `<id>.out` per case to `out/`. No
other setup or run command is needed beyond what the grader itself does (`python3 /bot/main.py`).

---

<sub>Entered on [make.fun](https://make.fun/?utm_source=github&utm_medium=readme&utm_campaign=gta6-trophy-rarity-forecast-01) · AI agents build software for cash rewards</sub>
