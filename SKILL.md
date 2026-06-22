---
name: worldcup-predictor
description: Use when analyzing or predicting World Cup or international football matches, especially when the user asks for match forecasts, score predictions, betting-market comparison, group qualification scenarios, style matchup, player availability, post-match review, or iterative model corrections.
---

# World Cup Predictor

## Core Principle

Predict matches by combining market baseline, verified data, team news, style matchup, and group incentives. Do not let one signal dominate: odds can overprice favorites, scorelines can hide chance quality, and possession can hide low chance quality.

## Disclaimer

Use this skill for informational football analysis only. Predictions are uncertain and can be wrong; do not present them as guaranteed outcomes, betting advice, financial advice, or an instruction to wager. When betting markets, odds, or platforms such as Polymarket or Stake are discussed, state that they are evidence inputs for analysis rather than recommendations to bet.

## Required Source Discipline

Before forecasting, state which source layers were actually used:

| Layer | Examples | Rule |
|---|---|---|
| Market | Polymarket public market pages, Stake public odds pages, major books, screenshots only as fallback | Use as baseline, not verdict |
| Data | Sofascore, FotMob, Flashscore, WhoScored, FBref, match centre stats | Prefer for xG, big chances, saves, ratings, momentum |
| News | FIFA, federations, Guardian, BBC, ESPN, local beat reports | Use for injuries, suspensions, lineup clues, travel/weather |
| Context | Group table, path, schedule, venue, weather | Use for motivation and risk appetite |
| Style matchup | pressing, buildup routes, chance creation patterns, transition risk, set pieces | Use to explain how chances are created or denied |

If a layer is missing, say so and reduce confidence. Never claim Sofascore, FotMob, Flashscore, WhoScored, FBref, Stake, Polymarket, or lineup data was used unless it was directly read from a public page/API or supplied by the user. Treat FBref as a delayed review and validation source, not a real-time matchday source, unless current-match data is verified.

## Forecast Workflow

1. **Check calibration state**: if prior post-match reviews or user-cited earlier sessions exist, carry forward the explicit model corrections before forecasting. Do not let a recent draw cluster cause blanket draw protection, and do not overcorrect back to paper favorites while ignoring injuries, starters, or role gaps.
2. **Identify match state**: date/time, group, standings, qualification incentives, and whether a draw helps either side.
3. **Set market baseline**: prefer visible prices from Polymarket public market pages, Stake public odds pages, or major books; use screenshots only as fallback. Convert visible prices/odds into rough favorite, draw, and total-goals expectations. Note liquidity, volume, wide spreads, stale pages, or missing markets. Use Polymarket API only when public page text cannot expose the needed market or when orderbook/bid-ask detail is specifically required.
4. **Verify recent performance**: prefer last tournament match data over friendlies, but also inspect recent five friendlies/pre-tournament matches when available. For immediate matchday reads, prefer verified Sofascore/FotMob/Flashscore data or user-supplied screenshots; use WhoScored/Sofascore event or shot-level data when available; use FBref, StatsBomb free data, and Understat mainly for delayed review, model calibration, or historical context. Check opponent quality, xG/chance quality, shots on target, big chances, saves, player ratings, minutes, and whether the scoreline was misleading.
5. **Check player availability**: injuries, suspensions, illness, rotation, expected starters, whether key players are truly fit enough to execute their role for 60-70 minutes, and whether replacements preserve or change the team's main route to goal.
6. **Analyze style matchup**: test how each team creates chances, prevents chances, handles pressure, progresses the ball, defends transitions, and uses set pieces without forcing a preferred shape or formation.
7. **Account for environment**: heat/humidity, travel, home/host boost, kickoff time, venue surface, and referee/discipline risk if known. Treat climate as a modifier, not the master variable.
8. **Produce prediction**: give winner/draw lean, exact score, backup score, confidence, and the single most important failure mode. If odds or betting markets were used, include a brief disclaimer that the analysis is not betting or financial advice.
9. **Post-match review**: compare prediction with score, xG/chances, ratings, key events, and update the model. Do not overgeneralize from one matchday.

## Style Matchup Checks

Analyze team style without privileging a specific formation, build-up shape, or possession structure.

- Strong favorite is safer when it repeatedly creates high-quality chances and limits the opponent's most dangerous route to goal.
- Be skeptical when possession, shot count, or territorial pressure does not translate into clear chances.
- Distinguish **pressure** from **chance quality**. A team can have 70% possession, 20+ shots, and still mostly create low-value attempts.
- Extra man is not automatic advantage. Ask whether the team can turn numbers into clear chances, second-ball recovery, and defensive control.
- Big first-match wins can be false signals when the opponent collapsed, received red cards, or conceded unusually easy chances.

## Output Format

Use a compact table first:

| Match | Sources used | Market baseline | Data/news correction | Prediction | Confidence |
|---|---|---|---|---|---|

Then add short match notes:

- **Sources used**: market, data, news, context, and style-matchup layers actually used.
- **Calibration**: prior post-match lessons applied, and whether this is provisional or final based on lineup availability.
- **Prediction**: score and backup score.
- **Why**: 2-4 strongest reasons.
- **Failure mode**: the most likely way the prediction breaks.
- **Missing data**: important unavailable source layers.
- **Disclaimer**: if odds or betting markets were used, state that the analysis is informational only and not betting or financial advice.

## Common Mistakes

- Do not equate favorite price with goal margin.
- Do not equate first-match score with true form; inspect chance quality and opponent collapse.
- Do not treat FBref, StatsBomb free data, or Understat as real-time sources for current World Cup matches unless current-match coverage was directly verified.
- Do not overrate friendlies over current tournament data.
- Do not assume a returning star is fully functional; ask whether they can sprint, press, dribble, or play 60+ minutes.
- Do not assume a coaching change creates instant defensive cohesion.
- Do not assume a favorite will fix repeated chance-creation problems just because it has famous attackers or needs a result; require evidence from lineup, role, or chance-quality changes.
- Do not keep treating an underdog as only a defensive spoiler after it has shown repeatable scoring routes such as set pieces, direct play, transitions, or a target-forward outlet.
- Do not say a team lacks quality just because it lost; check whether it created real chances.
- Do not treat climate, opening-round caution, or a cluster of draws as a master variable.
- Do not swing from "too conservative" straight back to paper-strength favorites when key creators, finishers, defenders, or starters are missing or limited.

For detailed weighting, confidence rules, and review templates, read `references/prediction-framework.md`.
