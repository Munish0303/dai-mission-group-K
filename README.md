# Does the Undercut Pay Off? — DAI Mission, Group K

![CI](https://github.com/<YOUR-GITHUB-USER>/dai-mission-group-k/actions/workflows/run-notebook.yml/badge.svg)

**Data & AI in Economics — TU Dortmund**

| Member | Role |
|---|---|
| Munish Patwa | Causal Inference Lead |
| Simran Arora | Supervised Learning |
| Nimesh Bhavsar | Unsupervised / Generative |

## Research question

> How do pit-stop strategies shape race performance in Formula 1 — and does an early first pit stop
> (before 40% of the race) *causally* improve a driver's net position gain relative to grid, after
> accounting for car quality, starting position, and track conditions?

## Repository structure

```
.github/workflows/   CI: re-executes the notebook on every push to main
data/                f1_strategy_v4.csv (96,336 laps, 2022–2025, OpenF1-enriched)
notebook.ipynb       Full mission notebook (fully executed)
requirements.txt     Python dependencies
```

The notebook follows the official template order:
**§1 Research Question & Data → §2 Causal Inference → §3 Supervised Learning → §4 Unsupervised → §5 Synthesis → References.**

## Headline results

- **Causal:** blanket early pitting does **not** improve finishing position (ATE ≈ −0.32; strengthening
  to −0.53 with DNF exclusion + constructor fixed effects). Effect is robust in direction across
  treatment thresholds; race-clustered SEs reported alongside classical ones.
- **Optimal window:** confounder-adjusted position gain peaks in the **30–50%** race-distance window
  (inverted-U); pitting before ~30% destroys value.
- **Supervised:** net position gain is dominated by grid slot and car quality — strategy features do not
  beat a grid-only baseline (RMSE ≈ 3.3). Pit *decisions* are highly predictable (mechanism AUC ≈ 0.96).
- **Unsupervised:** stints form two interpretable archetypes (early-MEDIUM vs long-HARD), but the
  strategy space is genuinely continuous (silhouette ≈ 0.29).

## How to run

```bash
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute --inplace notebook.ipynb
```

Runtime ≈ 5–10 minutes (DoWhy refutation simulations dominate). The CI workflow runs exactly this on
every push to `main`.

## Data & integrity

- Data: F1 lap-by-lap timing (2022–2025) enriched via the [OpenF1 API](https://openf1.org) (open data).
  The CSV (~30 MB) is committed under `data/`.
- LLM assistance (Claude / GitHub Copilot) was used for structuring, debugging, and drafting narrative;
  all analytical decisions, interpretations, and conclusions are the team's own work (disclosed in the
  notebook header).
