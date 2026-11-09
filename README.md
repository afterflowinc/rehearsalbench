<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/rehearsalbench-dark.svg">
    <img alt="RehearsalBench" src=".github/assets/rehearsalbench-light.svg" width="420">
  </picture>
</p>

<h3 align="center">Can AI predict what happens when you change a company?</h3>

<p align="center">
  <img alt="Round 3: November 2026" src="https://img.shields.io/badge/round%203-November%202026-353535">
  <img alt="Models: 10" src="https://img.shields.io/badge/models-10-353535">
  <a href="LICENSE"><img alt="Licence: CC BY 4.0" src="https://img.shields.io/badge/licence-CC%20BY%204.0-8e654e"></a>
</p>

RehearsalBench measures whether AI models can diagnose a real operation, choose an intervention, and forecast its
consequences. Each model runs a simulated bank contact centre built from real call-level records. It sees only what a
manager would see, then submits a plan and forecasts. Every plan is played out across 200 simulated futures and three
plausible versions of the organisation, so you can score each decision in dollars and each forecast against what
actually happens.

This repository holds the published results: the leaderboard, the verification hashes, and the citation.

## Leaderboard

Round 3: 10 models, 14 simulated contact centres, 2 attempts each (280 runs).

| Rank | Model | Developer | Cost saved | Forecast accuracy | Cost per run |
|---:|---|---|---:|---:|---:|
| 1 | GPT-6 Astra | OpenAI | **6.8%** (3.6–10.5) | **77%** (74–79) | $14.00 |
| 2 | Claude Sonnet 5.5 | Anthropic | 6.7% (3.4–10.5) | 74% (72–77) | $6.76 |
| 3 | GPT-6.1 Sol | OpenAI | 6.5% (3.5–10.0) | 74% (70–77) | $2.47 |
| 4 | Claude Fable 5.1 | Anthropic | 6.3% (3.2–9.8) | 71% (68–75) | $14.37 |
| 5 | Claude Haiku 5.5 | Anthropic | 5.7% (2.3–9.6) | 62% (55–69) | $1.56 |
| 6 | Qwen3.8 Flash | Alibaba | 5.3% (2.1–9.1) | 55% (48–63) | $0.58 |
| 7 | DeepSeek V4.1 Flash | DeepSeek | 5.3% (2.1–8.8) | 62% (55–67) | $0.46 |
| 8 | GPT-6 Luna | OpenAI | 0.7% (−0.1–2.5) | 59% (53–65) | $0.18 |
| 9 | Gemini 3.8 Flash | Google | 0.0% (−0.04–0.09) | 53% (45–60) | $2.49 |
| — | Mistral Small 2603 (partial) | Mistral | −2.0% (−5.5–1.4) | worse than no effect | $0.06 |

- **Cost saved:** the share of the contact centre's running cost that the model's plan removed, net of the plan's own
  cost, compared with changing nothing.
- **Forecast accuracy:** how much less forecast error the model made than a forecaster who always predicts no effect.
- **Ranges** are 95% intervals. **Cost per run** is the API spend at list prices, retries included.
- **Partial:** fewer than half of the model's runs were valid, so it's reported from its valid runs and not ranked.

The full table, with every interval, is in [`leaderboard.csv`](leaderboard.csv).

## Key findings

- **The best models save money.** Seven models cut running cost by 5–7% compared with doing nothing. GPT-6 Astra led
  on both decisions and forecasts.
- **Spending more buys little.** GPT-6.1 Sol came within 0.3 points of Astra's savings at a sixth of the cost per run.
- **Right direction, wrong size.** Every model forecast the direction of every specified effect correctly on average,
  but the models made the same sizing errors together. For example, they overstated a voice agent's effect on repeat
  contacts about five-fold.
- **No model holds off.** No model ever recommended doing nothing when doing nothing was the right choice.
- **The ranking holds up on real changes.** Twelve models forecast 33 real organisational changes with known outcomes.
  Under rules fixed in advance, RehearsalBench's ranking agreed with the real-world ranking (Spearman ρ = 0.92, 95%
  interval 0.50 to 0.92). In 89% of head-to-head model pairs, the model that RehearsalBench ranked higher was the better
  real-world forecaster. Ranking by price gets 67% right, and the LMArena leaderboard 60%.

## How it works

1. **Ground it in real operations.** Each simulated contact centre is fitted to real call-level records from the
   Technion SEELab archive, and checked against a second bank's records.
2. **Investigate and decide.** The model reads the bank's reports, staffing, costs, and stakeholder goals, can buy
   further evidence, and submits a plan with forecasts of its outcomes.
3. **Forecast specified changes.** In a fresh session, every model forecasts the same fixed list of interventions, so
   forecasts can be compared head to head.
4. **Play out every future.** An oracle runs each plan across 200 seeded futures and three versions of the
   organisation, then scores the decision and the forecasts separately.

Every specification, world, harness, and scoring rule was frozen and hashed before any model ran. The hashes are in
[`FROZEN.md`](FROZEN.md).

## Limits

- **One domain.** Every organisation is a contact centre.
- **Simulated outcomes.** Round 3's decisions and forecasts are scored by a simulator, not by real results.
- **What the real-world test covers.** It validates the ranking of forecasts, not the dollar savings.
- **A small set.** 14 organisations and 33 real events.

## What's in this repository

| File | Contents |
|---|---|
| [`leaderboard.csv`](leaderboard.csv) | Round 3 results for every model, with 95% intervals |
| [`FROZEN.md`](FROZEN.md) | SHA-256 hashes of every pre-registered freeze |
| [`CITATION.cff`](CITATION.cff) | Citation metadata |
| [`LICENSE`](LICENSE) | Creative Commons Attribution 4.0 |

The simulator, the oracle, and the test organisations aren't released, to keep future rounds uncontaminated.

## Citation

```bibtex
@misc{afterflow2026rehearsalbench,
  title  = {{RehearsalBench}: Can {AI} Predict What Happens When You Change a Company?},
  author = {{Afterflow Inc.}},
  year   = {2026},
  url    = {https://github.com/afterflowinc/rehearsalbench}
}
```

## Licence

The results, tables, and text in this repository are licensed under
[Creative Commons Attribution 4.0](https://creativecommons.org/licenses/by/4.0/). You can reuse them with credit.

<br>

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/made-by-afterflow-dark.svg">
    <img alt="Made by Afterflow" src=".github/assets/made-by-afterflow-light.svg" width="160">
  </picture>
</p>
