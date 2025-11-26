# Using GenAI Tools (Plain Language)

How consultants can use AI assistants (e.g., Claude, ChatGPT/Codex, Gemini) end-to-end without installing anything.

## Where GenAI Helps
- Research and framing: Summarize public articles/reports to shape the “where do we stand” view.  
- Templates: Draft interview guides, data request emails, or executive storylines.  
- Data dictionary cleanup: Turn messy column names into clear business definitions from a sample.  
- Chart captions: Suggest “so what” lines when you supply the key numbers.  
- QA checklists: Generate coverage/duplicate/missing/unit checks based on our standard steps.  
- Light coding help: Produce small Python snippets for pandas cleaning or scikit-learn modeling that engineers can run.

## Guardrails
- No confidential data in public tools; mask names/IDs or use approved private instances.  
- AI output is a draft—store final docs in our repo.  
- Ask for short bullets; state the audience (executive vs analyst).  
- Never paste AI-generated numbers into client work; only use it to format/summarize numbers you already have.  
- Note sources when summarizing external text.

## Step-by-Step Using GenAI (No Installs, Windows-Friendly)
1) Frame the ask: “I need a data request email for performance and activity tables; keep it short.”  
2) Paste sample columns (without sensitive IDs) and ask: “Rewrite these column names as business-friendly definitions; flag unclear ones.”  
3) For raw Excel cleanup guidance: “Given these columns and a few sample rows, list 10 cleanup steps in pandas (or in Excel if pandas isn’t available).”  
4) For modeling ideas: “Suggest a simple scikit-learn approach to rank drivers and a quick anomaly detector; keep code under 40 lines.”  
5) For dashboard storytelling: “Write one-line ‘so what’ captions for these metrics (paste metric, trend, target).”  
6) For QA: “Create a checklist to review a new Excel drop: coverage, duplicates, missing values, unit consistency.”  
7) Share the AI draft with an engineer to run or adapt; keep the final files in the repo.

## Quick Prompts (Copy/Paste)
- “Summarize these bullets into an executive ‘so what’ (under 40 words).”  
- “Rewrite this data request email to be clearer for a business stakeholder; keep these five column names unchanged.”  
- “Given these column names and sample rows, propose business-friendly definitions; list any unclear fields to confirm.”  
- “Draft chart captions: I’ll paste metric, trend, target. Keep each caption to one line and plain language.”  
- “List a pandas cleaning plan for this sample table: handle missing, duplicates, units, IDs. Keep it to 10 steps.”  
- “Suggest a simple regression and an anomaly check in scikit-learn using these columns; code under 40 lines.”  

Use GenAI to speed up drafting, prompts, and small code snippets; keep analysis and numbers grounded in our data and codebase.

## Meta-Prompt First: Have the AI Write Your Task-Specific Prompt
1) Copy this meta-prompt and paste your business statement, data columns, and file name.  
2) The AI will return a tailored “do-the-work” prompt you can run as-is.
```
I have a business statement: <PASTE BUSINESS GOAL/QUESTION>.
I have an Excel file named <PASTE_FILENAME.xlsx> in data/raw.
Key columns: <LIST MAIN COLUMNS AND MEANINGS>.

Please write a single, ready-to-run prompt (using only pandas, openpyxl, scikit-learn, streamlit, plotly, altair, shapely/h3 if geo) that will:
- Profile the Excel (row/col counts, nulls, describe) to data/outputs/profile_summary.csv.
- Clean: rename to clear snake_case, trim strings, parse dates, drop exact duplicates, keep blanks as NaN, save to data/processed/clean.csv.
- Build a tidy performance table: one row per entity-period (entity_id, year, month, metric), saved to data/processed/performance_tidy.csv.
- Add simple features (month, quarter, is_q4, basic ratios/deltas if applicable, one lag) to data/processed/performance_features.csv.
- Fit a driver model (ElasticNet or Ridge) and a RandomForest for accuracy; save importance tables to data/outputs/driver_ranking.csv and data/outputs/driver_importance_rf.csv.
- Run an IsolationForest anomaly check; save flagged rows with scores to data/outputs/anomalies.csv.
- Produce a Streamlit stub (streamlit_app.py) with KPIs, driver tables, anomalies, and Plotly/Altair charts with one-line “so what” captions.
- Include short run instructions for Windows with local venv (no admin).

Return only the final prompt, nothing else.
```
3) Take the generated prompt and run it in the same AI to produce the code and files.

## One-Shot Prompt (Copy/Paste) to Build From Excel → Dashboard
Paste this as one block to Claude/ChatGPT/Gemini, then add your column names and file name where noted.
```
You are my coding copilot. Use the following stack only: pandas, openpyxl (read Excel), scikit-learn (regression, tree models, isolation forest, DBSCAN/KMeans), streamlit, plotly, altair. Optional for geo: shapely/h3 if coordinates exist. Data lives in ./data/raw and outputs go to ./data/processed or ./data/outputs.

Task: Take the Excel file <REPLACE_WITH_FILENAME.xlsx> and produce:
1) A profiling summary (rows, columns, null counts, basic describe) saved to data/outputs/profile_summary.csv.
2) A cleaned CSV in data/processed/clean.csv with: renamed columns to business-friendly snake_case, trimmed strings, parsed datetimes, deduped rows, blanks kept as NaN (no guessing zeros).
3) A tidy performance table data/processed/performance_tidy.csv with one row per entity per period. Columns: entity_id (replace with my ID column), year, month, metric_value (replace with my metric column).
4) A feature table data/processed/performance_features.csv adding simple features: month, quarter, is_q4 flag, basic ratios/deltas if applicable, and a lag of the metric.
5) A lightweight driver model (ElasticNet or Ridge) to rank drivers; save coefficients/feature importances to data/outputs/driver_ranking.csv.
6) A basic accuracy boost model (RandomForestRegressor) and save top importances to data/outputs/driver_importance_rf.csv.
7) An anomaly detector (IsolationForest) on the feature table; save anomalies with scores to data/outputs/anomalies.csv.
8) A Streamlit script stub (streamlit_app.py) that shows: KPIs, driver table, anomalies table, and a few charts (Plotly/Altair) with one-line “so what” captions.

Assumptions:
- My date column is called <REPLACE_WITH_DATE_COL>.
- My entity column is called <REPLACE_WITH_ENTITY_COL>.
- My main metric column is called <REPLACE_WITH_METRIC_COL>.
- Keep code concise and runnable on Windows with a local venv (no admin).
- Write all file paths relative to the repo root.

Deliver:
- Python code blocks for steps 1-7.
- A Streamlit code block for step 8.
- Short instructions to run: profiling/cleaning, feature creation, models, then `streamlit run streamlit_app.py`.
```
