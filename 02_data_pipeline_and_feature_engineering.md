# Data Pipeline and Feature Engineering (Plain Language)

## Raw vs Processed (Why We Move Out of Excel)
- **Raw:** Original files exactly as received; never edited. Stored with date stamp.  
- **Processed:** Clean, tidy tables created by scripts so we can rerun anytime.  
- **Why not Excel edits:** No audit trail, formulas break silently, row limits, and team members create conflicting versions. Scripts make the work repeatable and defendable.

## Clean-Up Steps Clients Should Expect
- **Schema check:** Do columns and date ranges match the agreed template? Flag surprises.  
- **Missing values:** Mark what is truly missing vs zero; avoid guessing.  
- **Deduplication:** Remove exact duplicates; keep a note of how many rows were dropped.  
- **Unit and format fixes:** Standardize units (km, minutes, currency) and date formats.  
- **Outlier review:** Highlight extreme values with a one-line business check (keep or drop).

## Feature Engineering in Non-Technical Terms
- **Time features:** Month/quarter, seasonality markers, pre/post program flags.  
- **Entity features:** Site, branch, product, or partner characteristics (region, size, capabilities).  
- **Behavior features:** Ratios and deltas (on-time rate, detour ratio, idle minutes, mix share).  
- **Lagged signals:** Previous period’s metric to capture momentum without peeking into the future.  
- **Interaction flags:** Simple business rules (e.g., night trips in red zones, high-risk product with a new vendor).

## Data Structures Optimized for Dashboards
- **Tidy fact table:** One row per entity per period (e.g., site-month, vehicle-journey, product-week).  
- **Keys:** Clear IDs for entity, time, and location to join across tables.  
- **Versioned tables:** `raw/` for intakes, `processed/` for cleaned data, `outputs/` for model results.  
- **Ready-made aggregates:** Precompute per-period summaries so charts load fast (no waiting on big pivots).  
- **Metadata file:** Definitions for every column and timestamp of the last refresh.

## What “Good” Looks Like Before Modeling
- Coverage map: % of periods with data per entity.  
- Data dictionary signed off by business owner.  
- Run sheet: which scripts produced which outputs and when.  
- First-cut charts checked by the business lead to confirm numbers feel right.
