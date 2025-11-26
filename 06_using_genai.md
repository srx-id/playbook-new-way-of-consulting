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
