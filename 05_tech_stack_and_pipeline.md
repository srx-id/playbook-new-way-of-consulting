# Tech Stack and Data-to-Dashboard Walkthrough

Plain-language catalog of the tools already in our projects and how they fit together, plus a literal step-by-step from raw Excel to a client-ready dashboard.

## Tech Stack (What Each Tool Is For)
- **Data intake & cleaning:** `pandas`, `numpy`, `openpyxl` (read Excel), `python-dotenv` (load settings).  
- **Feature engineering & models:** `scikit-learn` (regression/classification, trees/boosting, clustering, anomaly detection), `srx-lib-core` (logging/config), `srx-lib-ml` (shared ML helpers in the transport project).  
- **Visualization & delivery:** `streamlit` (app shell), `plotly` and `altair` (interactive charts).  
- **Geospatial extras (transport app):** `shapely` (zones/polygons), `h3` (hex grids).  
- **Dev hygiene:** `ruff` (format/lint), `pytest` (quick checks), `ipython` (scratch exploration).

## Algorithm Catalog by Common Question
- **“Which factors move the metric?”**  
  - Use regularized regression (linear/logistic) in `scikit-learn` for a clear driver list with direction and size.  
  - Examples: ElasticNet, Ridge/Lasso.  
- **“Can we predict it more accurately?”**  
  - Use tree ensembles in `scikit-learn` (RandomForest, GradientBoosting/HistGradientBoosting) and keep a short top-driver list.  
- **“Are there patterns or groups?”**  
  - Clustering with `DBSCAN` (find natural clusters/outliers) or `KMeans` (quick grouping).  
- **“What looks unusual or risky?”**  
  - Anomaly detection with `IsolationForest` plus a few simple rules for clarity.  
- **“Did the change help?”**  
  - Pre/post with control vs pilot using plain regression/time splits in `pandas` + `scikit-learn`; show uplift and confidence, not formulas.  
- **Tip:** Pick the simplest method that answers the business question; only add complexity for accuracy or coverage.

## Excel-to-Dashboard: Step-by-Step (What Actually Happens)
1) **Receive the raw drop:** Save the Excel file as-is in `data/raw/` with a date stamp.  
2) **Profile quickly:** Open with `pandas` to see columns, date range, row counts, obvious gaps/dupes; note, don’t blame.  
3) **Standardize IDs and units:** Align IDs to one list; make units explicit (currency, minutes, km, pieces).  
4) **Tidy the tables:** One row per entity per period for performance; one row per activity/event with IDs, timestamps, location/status.  
5) **Handle missing and duplicates:** Keep blanks as unknown; drop exact duplicates and log how many.  
6) **Add simple features:** Time markers (month/quarter), flags (pilot vs control), ratios/deltas (success rates, distances per trip), basic lags.  
7) **Split for sanity checks:** Use earlier periods as “train” and later periods as “holdout” to confirm stability.  
8) **Fit lightweight models:** Start with explainable regression for drivers; add tree models if accuracy is needed; run anomaly detection if hunting outliers.  
9) **Save clean outputs:** Write processed tables and model outputs to `data/processed/` or `data/outputs/` for reuse.  
10) **Build the dashboard:** Streamlit pages with Plotly/Altair charts, each with a one-line “so what”; add data currency/version in the header.  
11) **Share and iterate:** Walk through the exec page first, then drill-down tabs; capture feedback and adjust filters/labels, not the raw data.

Use this as the catalog and recipe—consultants can point to the tool/step without needing to code.
