# MDST Football Project

How much of a player's fantasy football production comes from opportunity (targets, carries, pass attempts) — and can last season's opportunity predict next season's points?

This project models PPR fantasy points per game for NFL QBs, RBs, WRs and TEs using 2024–2025 season data, tests how well those models actually forecast the following year, and projects 2026 top 10s at each position.

Built as a project with the Michigan Data Science Team (MDST) at the University of Michigan.

## Key findings

- **Usage explains a season well.** Linear regression on per-game usage explains most of the variation in same-season fantasy output: R² of 0.93 for RBs, 0.83 for WRs and 0.53 for QBs on held-out data.
- **But it forecasts next season only moderately.** Fit on 2024 and projecting 2025, the model picked **18 of 40** actual top-10 players across the four positions, versus 20 of 40 for a naive "same as last year" baseline. It had lower per-game error than the baseline at QB, WR and TE.
- **Predictability varies a lot by position.** Year-to-year correlation in PPR points per game is 0.65 for RBs and 0.64 for WRs, but only 0.40 for QBs and 0.30 for TEs.
- **QB volume misleads.** Attempts-based QB projections overrate high-volume and rushing QBs and miss efficient pocket passers, pointing to efficiency stats as the next feature to add.
- **Role changes drive breakouts and fall-offs.** K-means groups of 2024 vs. 2025 scoring show that at every position, breakout players gained opportunities per game and fall-off players lost them, and fall-offs skewed older at QB, WR and TE.
- **Most forecast misses are unmodeled events:** injuries, team changes, role breakouts and rookies with no prior season.

## Notebooks

| Notebook | What it does |
|---|---|
| [`Modeling/linear_regression.ipynb`](Modeling/linear_regression.ipynb) | Fits overall and position-specific regressions of PPR/game on usage features; flags "buy-low" WRs who underperformed their target volume. |
| [`Modeling/top10_projections.ipynb`](Modeling/top10_projections.ipynb) | Backtests the regressions (2024 → 2025 top 10s) against a naive baseline, then projects 2026 top 10s from combined 2024–2025 usage. |
| [`Modeling/k_means.ipynb`](Modeling/k_means.ipynb) | Year-to-year analysis (next-season R², persistence, aging curves), plus k-means clustering of players into High-High, High-Low, Low-High and Low-Low groups by 2024 vs. 2025 PPR/game to see what separates breakouts from fall-offs. |
| [`Modeling/def_modeling.ipynb`](Modeling/def_modeling.ipynb) | Team-level model: whether plays faced by a team's defense predict that team's total player fantasy points. |
| [`Modeling/Plots_Visuals.ipynb`](Modeling/Plots_Visuals.ipynb) | Exploratory correlation heatmaps across all fantasy stats. |
| [`DataSets/CombineData.ipynb`](DataSets/CombineData.ipynb) | Merges the raw 2024 and 2025 passing, rushing, receiving and defense tables into the combined datasets. |

## Methods

- **Data prep:** merged per-season passing, rushing and receiving stats into one player-season table (2024–2025); deduplicated traded players; filled missing counting stats with 0 while leaving rate stats missing.
- **Feature engineering:** per-game usage rates (targets, rush attempts, pass attempts, touchdowns), with minimum-play thresholds by position (QB 200, RB 100, WR 40, TE 30) to filter out low-volume noise.
- **Modeling:** scikit-learn linear regression with position-specific feature sets, evaluated on held-out data and with an out-of-sample year-ahead backtest against a naive baseline.
- **Evaluation:** R², mean absolute error, Spearman rank correlation and top-10 hit rate.

## Data

Player and team stats come from [Pro Football Reference](https://www.pro-football-reference.com/) (Sports Reference). `DataSets/` holds the combined player stats (`FantasyData.csv`), season PPR totals (`2024FantasyPPR.csv`, `2025FantasyPPR.csv`) and team defense stats (`DefenseData.csv`) for the 2024 and 2025 NFL seasons.

## Running it

```bash
python -m venv .venv
source .venv/bin/activate
pip install pandas numpy scipy matplotlib seaborn scikit-learn jupyterlab
jupyter lab
```

Run notebooks from the repository root so the `DataSets/` paths resolve.

## Next steps

- Add efficiency features (yards per attempt, yards per target, TD rate), especially for QBs.
- Use more seasons of history, weighting recent seasons more heavily.
- Add age and injury history, and replace touchdowns with red-zone opportunities.
- Score the 2026 projections once the season's data is available.

**Tools:** Python, pandas, NumPy, scikit-learn, SciPy, Matplotlib, seaborn, Jupyter
