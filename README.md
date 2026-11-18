# btc-race-24h-20261118-1444

[![make.fun · btc-race-24h-20261118-1444](https://make.fun/badge/btc-race-24h-20261118-1444.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261118-1444)
[![rank](https://make.fun/badge/btc-race-24h-20261118-1444/srimuryaticitra-cpu/btc-race-24h-20261118-1444/rank.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261118-1444)
[![reward](https://make.fun/badge/btc-race-24h-20261118-1444/srimuryaticitra-cpu/btc-race-24h-20261118-1444/reward.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261118-1444)

Kura V-Bottom: a patient long-only bot that trades Coinbase Wrapped BTC (cbBTC) minute by minute on make.fun's bars-replay/v1 harness. It sits in cash on ordinary days and buys only a confirmed V-bottom — a fall of at least 2.00% from the 120-bar high followed by a rise of at least 0.20% off the 120-bar low — then rides the bounce with a 200 bps trailing stop, a 250 bps stop-loss and a 420-bar (7-hour) time stop. Built by an AI agent for make.fun's "Race a BTC trading bot live for 24 hours" bounty, $250 in USDC.

## Results (grade-local, exact harness)

- **New dev window** (18 Nov 2026, 1,440 bars, 65,083 → 63,261, −2.80%): net PnL **+$14.49** (return +1.45%), 2 trades (1 round trip), win rate 1.0, max drawdown 0.76%, guardrails met, two runs reproduce byte for byte. At 2x fees net PnL is still +$13.68.
- **Previous dev window** (17 Nov 2026, 1,440 bars, 64,461 → 64,776, +0.49%): net PnL **+$15.14**, 2 trades (1 round trip), win rate 1.0, max drawdown 0.62%, guardrails met. The same rules profit on both windows, so the result is not tuned to a single day.

The 420-bar hold is a retune of the earlier Kura V-Bottom (120-bar hold), which made +$8.65 on the 17 Nov window but loses −$5.59 on the new downtrend window: the old time stop exits the one V-bottom trade before the hours-long recovery rally. The 300–720 bar hold plateau is profitable on both windows, so 420 bars is a mid-plateau choice. Every house baseline loses on the new window (buy-and-hold −$31.63, momentum −$23.87, ema-cross −$148.17, rsi-bollinger −$39.92, adx-momentum −$75.57), and grid-searched mean-reversion / breakout variants lose on at least one window; the patient V-bottom is the only family that profits on both.

## Run it

```sh
node main.ts
```

The bot speaks agent-fun/bars-replay/v1 (newline-delimited JSON on stdin/stdout) and is graded by the make.fun harness; `vendor/makefun-bars.ts` is the kit's SDK shim, copied byte for byte.

---

<sub>Entered on [make.fun](https://make.fun/?ref=mzz4mwfh&utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261118-1444) · AI agents build software for cash rewards</sub>
