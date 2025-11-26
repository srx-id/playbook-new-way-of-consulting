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

## Excel-to-Dashboard with Simple Python (Copy/Paste, Windows-Friendly)
- **If Python is not installed:** Ask tech team for a pre-made `.venv` folder with `pandas` and `openpyxl`, or install once with `pip install pandas openpyxl`. No admin rights needed if you use a local venv.  
- **Where to run:** PowerShell or Command Prompt in the project folder (same level as `data/`).

### 1) Quick profile of the raw Excel
```bash
python - <<'PY'
import pandas as pd
df = pd.read_excel("data/raw/your_file.xlsx")
print("Rows:", len(df))
print("Columns:", list(df.columns))
print("\nFirst 3 rows:\n", df.head(3))
print("\nNulls per column:\n", df.isna().sum().head())
df.describe(include="all").to_csv("data/outputs/profile_summary.csv", index=False)
PY
```

### 2) Clean and standardize (IDs, dates, duplicates)
```bash
python - <<'PY'
import pandas as pd

INPUT = "data/raw/your_file.xlsx"
OUTPUT = "data/processed/clean.csv"

col_map = {
    # "Old Column Name": "new_name",
    # Fill in a few key renames to keep names short and clear
}

df = pd.read_excel(INPUT)
df = df.rename(columns=col_map)

# Example: standardize an ID and a date column if present
if "id" in df.columns:
    df["id"] = df["id"].astype(str).str.strip()
if "date" in df.columns:
    df["date"] = pd.to_datetime(df["date"], errors="coerce")

df = df.drop_duplicates()
df.to_csv(OUTPUT, index=False)
print(f"Saved cleaned table to {OUTPUT} with {len(df)} rows.")
PY
```

### 3) Create a tidy performance table (one row per entity-period)
```bash
python - <<'PY'
import pandas as pd

df = pd.read_csv("data/processed/clean.csv")
# Replace these column names with your own
date_col = "date"
entity_col = "site_id"
value_col = "metric_value"

# Extract period (month) example
df[date_col] = pd.to_datetime(df[date_col], errors="coerce")
df["year"] = df[date_col].dt.year
df["month"] = df[date_col].dt.month

tidy = df[[entity_col, "year", "month", value_col]].copy()
tidy.to_csv("data/processed/performance_tidy.csv", index=False)
print("Saved tidy performance table to data/processed/performance_tidy.csv")
PY
```

### 4) Basic feature adds (time flags, simple ratios)
```bash
python - <<'PY'
import pandas as pd

df = pd.read_csv("data/processed/performance_tidy.csv")
df["is_q4"] = df["month"].isin([10, 11, 12]).astype(int)
df.to_csv("data/processed/performance_features.csv", index=False)
print("Added simple features to data/processed/performance_features.csv")
PY
```

### 5) Hand off for modeling and dashboard
- Share the `data/processed/*.csv` files with the engineering/analytics team.  
- They plug into Streamlit + Plotly/Altair pages already in the repos.  
- You focus on story: confirm column names, targets, and the “so what” for each chart.
