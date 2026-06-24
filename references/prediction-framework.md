# Prediction Framework

## Evidence Weighting

Use these weights as a guide, then explain deviations.

Keep all forecasts informational. Odds, betting markets, and exchange prices are analysis inputs only; never frame a prediction as guaranteed, betting advice, financial advice, or an instruction to wager.

| Dimension | Weight | What to inspect |
|---|---:|---|
| Team/style matchup | 25% | chance creation, chance prevention, press resistance, transition defense, set pieces |
| Player availability/state | 25% | starters, injuries, suspensions, illness, role fitness, ratings |
| Current data | 20% | xG, big chances, shots on target, saves, chance locations, momentum |
| Market baseline | 15% | Polymarket, Stake, books, liquidity, line movement |
| Group/context/environment | 15% | standings, draw value, path incentives, host boost, heat, travel, governance and continuity signals |

Raise player availability above 25% when a team depends on one or two key roles: a build-up organizer, main ball progressor, primary chance creator, defensive organizer, goalkeeper, set-piece specialist, or main finisher. Use named players only as verified, tournament-specific examples; do not treat them as permanent rules. Availability means role fitness, expected minutes, and replacement quality, not just whether the player appears in the squad.

## Source Tiers

| Tier | Sources | Use |
|---|---|---|
| A | official lineups, FIFA match centre, federation injury updates | facts and availability |
| B1 | Sofascore, FotMob, Flashscore, FIFA match centre stats, user-supplied screenshots from these sources | immediate performance, lineups, player ratings, saves, big chances, shot xG when visible |
| B2 | WhoScored, Sofascore event maps, shot maps, heatmaps, Opta-style event data | event-level and tactical diagnosis when directly readable |
| B3 | FBref, StatsBomb free data, Understat | delayed review, historical validation, model calibration, and deep context rather than live matchday reads |
| C | Polymarket public pages, Stake public odds pages, major books | market baseline and consensus |
| D | Guardian/BBC/ESPN/local beat reports | narrative, context, quotes, style and matchup hints |
| E | social clips/forums | hypothesis only; verify elsewhere |

Mark uncertain facts clearly: confirmed, reported, inferred, or user-supplied.

Access discipline matters as much as source quality. If a site returns 403, requires heavy JavaScript, blocks automated access, or only appears through a user screenshot, say exactly that. Do not promote a source into "used" unless the relevant match page, API output, or screenshot was actually read.

## Market Reading

- Prefer public web pages for market baselines: Polymarket event/market pages, Stake public odds pages, and major books. Use screenshots only when live page access is unavailable.
- For World Cup fixtures, start from dedicated aggregation pages before generic search:
  - Polymarket World Cup games: `https://polymarket.com/zh/sports/world-cup/games`
  - Stake soccer / visible World Cup listings: `https://stake.com/zh/sports/soccer`
  If locale-specific paths fail, try the same product area in another locale before declaring the market layer unavailable.
- Do not treat a failed generic search, a team-name-only Polymarket Gamma API search, or an unrelated API result as proof that odds do not exist. The public sport/game aggregation page can expose fixtures that API search misses.
- For Polymarket public pages, read visible market text first: moneyline, draw, spreads, totals, BTTS, first-team-to-score, displayed volume, and any visible probability/cent price. Clean duplicated or concatenated page text before using it.
- For Stake public pages, separate normal 1X2 decimal odds from signup offers, free bets, odds boosts, and acquisition promos. Promotional prices are not a market baseline.
- Do not claim Polymarket orderbook depth, bid/ask spread, midpoint, or token-level detail unless an API/orderbook source was actually read. Public page text is enough for baseline probability, not precise execution quality.
- Convert odds/prices into rough probabilities, but avoid false precision when using screenshots or noisy page text.
- Compare 1X2 with handicap and totals.
- Favorite with weak handicap support often means small win, not blowout.
- Heavy favorite plus deep handicap support plus group net-goal incentive supports multi-goal predictions.
- Low total with strong favorite supports 1-0 or 2-0 rather than 3-1.
- Polymarket low liquidity, low volume, stale visible prices, or very wide spread should be weak reference only.

## Data Reading

Prefer tournament data over friendlies, but still inspect the recent five friendlies/pre-tournament matches when available. Use them for role continuity, minutes, opponent quality, and player state; use current tournament data for the stronger read on actual chance quality.

Immediate performance sources:

- Use FotMob, Sofascore, Flashscore, FIFA match centre, or user screenshots for live scores, lineups, substitutions, shots, shots on target, big chances, saves, ratings, and visible xG.
- Use Sofascore shot xG, player ratings, heatmaps, and event views when available; they are especially useful for distinguishing real pressure from low-value shot volume.
- Use WhoScored or Opta-style event data for tactical questions such as ball progression, repeated turnovers, zone occupation, and whether a midfield disconnect is structural.

Delayed review sources:

- Use FBref for next-day or later validation of aggregate and advanced stats. Do not treat it as a real-time source.
- Use StatsBomb free data for historical learning, event-data practice, and model calibration; do not assume current World Cup coverage.
- Use Understat as an xG reference mainly for covered club competitions; verify coverage before using it for national-team matches.

For the previous match, ask:

- Was the score supported by xG and big chances?
- Did a goalkeeper produce an outlier performance?
- Were red cards, early goals, penalties, or game-plan collapses decisive?
- Did the team create box entries and high-quality shots, or only low-value volume?
- Which players had high ratings for repeatable actions: saves, key passes, duels, progressive carries, defensive actions?

Pattern examples:

- A 0-0 with high shot volume and many goalkeeper saves can show real pressure, but finishing variance or a goalkeeper outlier may break market expectation.
- A possession-dominant 0-1 loss does not prove poor team quality by itself; inspect whether possession became high-quality chances.
- A reputation-heavy favorite can underperform when the actual team sheet removes key chance creation, progression, defensive control, or finishing roles.
- A favorite with consecutive low-efficiency attacking games should not be treated as due for automatic rebound. Upgrade only if the lineup, roles, or previous-match chance quality show a real route to repair.
- An underdog that creates repeatable scoring routes across matches should be upgraded from "can frustrate" to "has a stable goal path." Track set pieces, direct play, crosses to a target forward, transition carries, long shots, and second balls.

## Calibration Discipline

- Carry forward explicit lessons from recent post-match reviews before making a new forecast.
- After a run of draws, raise draw awareness but do not apply blanket draw protection.
- After noticing overconservatism, do not swing back to paper-strength favorites without rechecking key role fitness, starters, and recent chance quality.
- After a favored team has failed to score from open play or produced repeated low-quality volume, cap its margin and raise draw risk until there is concrete evidence of chance-creation repair.
- After a smaller team shows real scoring routes in consecutive tournament matches, give that route independent weight even if market price, reputation, or possession profile still favors the opponent.
- Strong teams with healthy elite creators/finishers should not be flattened into default draws by climate or opening-round caution alone.
- Structural or role gaps should usually cap margin first, then raise draw risk; they should not automatically flip the match to an upset.
- Public criticism from core players about rushed federation rebuilds, leaks, squad discontinuity, or instability is a high-weight cohesion signal, not ordinary post-match venting. Downgrade team cohesion, tactical continuity, defensive coordination, and late-game resilience. Keep unverified corruption, payment, or internal-politics claims separate until sourced.
- If final lineups are unavailable, label the forecast provisional and name the specific lineup triggers that would move the score or winner lean.

## Style Matchup Diagnostics

Do not force every team into a preferred formation, build-up shape, or possession model. Evaluate whether the team's actual approach creates and prevents high-quality chances.

### Positive indicators

- The team creates repeatable high-quality chances, not just territory or shot volume.
- Ball progression remains functional under pressure.
- Defensive spacing limits the opponent's best chance creation route.
- Set pieces, transitions, wide play, central combinations, or direct play fit the available players.
- Game state changes do not immediately remove the team's main route to goal.

### Warning indicators

- Possession or pressure produces few clear chances.
- Key creators occupy the same zones and reduce each other's influence.
- Injuries or role changes remove the team's main progression, creation, or finishing route.
- Recent coaching change, abrupt youth rebuild, public leaks, or player-confirmed lack of shared playing time undermines coordinated pressing, defensive spacing, set-piece assignments, and late-game resilience.
- Aggressive attacking choices leave repeated high-value counterattacks.
- The team needs to chase but lacks tools to create better chances.

## Group Incentives

- Team on 3 points may accept draw if it nearly secures qualification.
- Team on 1 point against weak opponent may chase net goal difference.
- Team on 0 points in match two usually cannot accept a draw, but may still lack tools to chase.
- Path incentives matter only if teams can realistically control placement; do not overweight speculative bracket choices early.

## Confidence Labels

| Confidence | Use when |
|---|---|
| High | market, data, personnel, and motivation align; low missing-data risk |
| Medium | favorite clear but one key uncertainty exists |
| Low | signals conflict, key lineups unknown, or team styles create high variance |

Separate confidence in result from confidence in exact score. Exact score is usually lower confidence.

## Standard Answer Template

```markdown
| Match | Sources used | Market | Data/personnel correction | Prediction | Confidence |
|---|---|---|---|---|---|
| A vs B | Market, news, matchup | A small favorite | B has strong low block; A missing creator | A 1-0 | Medium |

**A vs B**
Sources used: Polymarket public page or Stake public odds page; team news report; style-matchup notes. Data layer unavailable.
Calibration: Prior review showed overcorrecting to draws is risky, but this remains provisional because final lineups are unavailable.
Prediction: A 1-0; backup 1-1.
Why: [market], [data], [availability], [style matchup].
Failure mode: A cannot turn possession into box chances, or B scores first from transition/set piece.
Missing data: Sofascore unavailable / lineup not confirmed / weather not checked.
Disclaimer: Informational football analysis only; not betting or financial advice.
```

## Post-Match Review Template

```markdown
| Match | Prediction | Result | Verdict |
|---|---:|---:|---|

What was right:
- ...

What was wrong:
- ...

Model update:
- Increase/decrease weight for ...
- Note whether this was a paper-strength error, over-draw-protection error, lineup/fitness miss, market miss, or finishing-variance miss.
```

Review against process and chance quality, not only score. If a prediction loses to an extreme goalkeeper performance or red card, record it differently from a wrong style-matchup read.
