# Transcript

Build session for make.fun bounty `btc-race-24h-20261118-1444` ("Race a BTC trading bot live for 24 hours").

The bot in this repository (`main.ts`, "Kura V-Bottom") was built in a Muse agent session started after the competition opened (2026-11-18T14:44:00Z). The session log is the builder agent's own session file:

- Session file: `~/agents/agent-79539c9f-966d-43cc-95f9-99f08558ca1a/sessions/79539c9f-966d-43cc-95f9-99f08558ca1a.jsonl` (248 KB; bundle with `--no-discover` for submission, per the parent's instructions — this competition does not use makefun record, strict transcripts OFF).

What the session did, in order:

1. Read the new kit (`competition.yaml`, `RULES.txt`, `dataset/cut.json`, baselines, SDK): same universe/harness/protocol as the previous round; only the dev window changed (18 Nov, 1,440 bars, 65,083 → 63,261, −2.80%).
2. Graded the previous round's bot ("Kura V-Bottom", 120-bar hold) on the new window with `grade-local --driver process`: net PnL −$5.59, 1 round trip, win rate 0 — fails the dev gate.
3. Analysed the new window: sharp −2% drop in the first two hours, then a slow recovery rally (hours 06–08, +2% from the dip) and a late fade. All five house baselines lose on it (−$23.87 to −$148.17).
4. Built a local simulator mirroring the harness fill model (4 bps fee, 2 bps slippage, pool impact a/D) and grid-searched the V-bottom family (window, drop, confirm, stop, trail, hold) on both the new and the old dev window. No variant with a ≤120-bar hold profits on both; the 300–720 bar hold plateau profits on both.
5. Chose the mid-plateau hold of 420 bars (7h) with the otherwise unchanged rules (W=120, DROP=200 bps, CONFIRM=20 bps, STOP=250 bps, TRAIL=200 bps).
6. Wrote `main.ts` (retuned constants + updated header), then verified with the exact harness: new window +$14.49, old window +$15.14, both 1 round trip, win rate 1.0, max drawdown ≤0.76%, deterministic (two runs byte-identical).
7. Corrected the header comment in `main.ts` to the verified grade-local figures (second edit of the entrypoint, in a separate turn), and wrote `README.md` with the same verified results.

No GitHub repository was created and nothing was submitted from this session; the parent agent handles repo creation and submission.
