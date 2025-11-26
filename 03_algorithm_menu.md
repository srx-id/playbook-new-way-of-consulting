# Algorithm Menu (Choose Without Jargon)

## Outside-In Benchmark (Deep Learning First)
- **What it is:** Use pre-trained models to scan public text/images and cluster peers, risks, or technology moves.  
- **When to use:** Week 1 to anchor the “where do we stand” slide before internal data is clean.  
- **Output:** Peer benchmark heatmap and a shortlist of practices to test internally.

## Interpretable Baseline (Start Here for Drivers)
- **Models:** Regularized linear or logistic (Ridge/Lasso/ElasticNet).  
- **Use case:** Show direction and approximate effect size (e.g., which FFB source mix lifts OER, which vendor traits cut failures).  
- **Output:** Ranked drivers with signs (↑/↓) and error in business units.

## Non-Linear Accuracy Boost
- **Models:** Gradient Boosting / Random Forest.  
- **Use case:** Capture interactions (seasonality by region, night trips in risky areas).  
- **Guardrails:** Limited feature set, permutation importance, and partial dependence plots so we keep explainability.  
- **Output:** Better predictions, stable top drivers, what-if curves for key levers.

## Anomaly & Risk Detection
- **Models:** Isolation Forest + simple rules.  
- **Use case:** Flag journeys, vendors, or mills that look unlike their peers; blend rules for clarity.  
- **Output:** Risk scores with action bands (monitor, spot-check, investigate).

## Impact of Interventions
- **Methods:** Difference-in-Differences, synthetic control, or double ML.  
- **Use case:** Prove uplift from programs like LMM vs non-program peers.  
- **Output:** Uplift estimate with confidence band and a plain-language verdict (“evidence of improvement” vs “not visible yet”).

## Quick Selection Cheatsheet
- Need a fast story before data is ready → Outside-in benchmark.  
- Need trusted drivers and simple math → Interpretable baseline.  
- Need extra accuracy for forecasts or targeting → Non-linear boost.  
- Need to find bad actors or weird trips → Anomaly + rules.  
- Need to prove program impact → DiD / synthetic control.  
- If daily/high-frequency data arrives → Consider sequence models later; not required for monthly data.
