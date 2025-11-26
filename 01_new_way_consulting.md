# New Way of Consulting (Top-Down + ML Bottom-Up)

## Philosophy
- Start with the CEO question, not the dataset: define Situation → Complication → Question → Day-1 Hypothesis.
- Prove or kill the hypothesis with data: move from outside-in signals to inside-out models.
- Keep MECE: separate market benchmark, internal performance, and program impact so the client sees no overlaps or gaps.

## Client Flow (Week-by-Week Ready)
1) **Frame the question (Day 0)**  
   - Agree on business outcome and north-star metric (e.g., OER %, theft risk score, on-time rate).  
   - Draft the storyline: executive summary page plus three supporting pages.
2) **Outside-in benchmark (Week 1)**  
   - Pull external signals fast: pre-trained deep learning embeddings on public text/images to map peers, risk terms, or technology mentions.  
   - Deliver a benchmark table: where the client sits vs industry, and a heatmap of gaps.
3) **Data intake & hygiene (Week 1-2)**  
   - Lock a single raw data drop; assign owners for definitions.  
   - Build a reproducible processed dataset (no manual Excel edits).  
   - Validate coverage: time window, entities, and key metrics.
4) **Baseline, interpretable models (Week 2)**  
   - Use regularized linear models to show direction and effect size; keep features limited and business-readable.  
   - Report errors in business units (e.g., OER points, minutes, currency).
5) **Non-linear lift & driver ranking (Week 3)**  
   - Add gradient boosting/forests for accuracy; run permutation importance and partial dependence to explain drivers.  
   - Stabilize findings with time-aware splits (train past, test future).
6) **Program impact (Week 3-4)**  
   - If there is an intervention (e.g., LMM), run Difference-in-Differences or synthetic control.  
   - Show uplift with confidence bands and peer controls.
7) **Package & deploy (Week 4)**  
   - Publish the Streamlit dashboard with executive summary first, then drill-down tabs.  
   - Ship processed datasets + code notebook so results are repeatable.

## Working Norms with Clients
- One owner per metric definition; no silent redefinitions midstream.
- Every chart has a bottom-line “so what” in one sentence.
- Decisions are logged against the data view used (raw/processed version and timestamp).

## Deliverables to Expect
- Executive readout draft by end of Week 1 (top-down narrative).
- Clean processed dataset and profiling report (Week 2).
- Driver ranking and scenario calculator (Week 3).
- Impact assessment plus dashboard (Week 4).
