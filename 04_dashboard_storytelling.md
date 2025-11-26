# Dashboard Storytelling (Executive-First)

## Navigation Template (Streamlit-Friendly)
- **Sidebar:** Executive Summary → Context & Approach → Detailed Analysis tabs → Documentation.  
- **Home/Exec page:** Situation, Complication, Question, Day-1 Hypothesis, and the answer headline.  
- **Drill-down tabs:** One tab per lens (operations, risk, geography, time, peer benchmark).

## Page Pattern
- **Top strip:** 3-4 KPIs with trend arrows and target gaps.  
- **Story block:** One paragraph on what matters this week.  
- **Charts:** Each chart has a one-line “so what” below it (no chart stands alone).  
- **Action box:** What to do next (who owns it, by when).

## Keep It MECE
- Split pages by mutually exclusive lenses: performance level, variance drivers, program impact, risk/outliers, and roadmap.  
- Avoid mixing goals (e.g., driver analysis is separate from intervention impact).

## Bottom-Up Evidence That Feels Top-Down
- Precompute simple tables (deltas, rankings, risk bands) so the story loads fast.  
- Use consistent color coding for wins/risks; avoid rainbow charts.  
- Include a small “method” note on first use of a model (one sentence, no formulas).

## Reusable Section Examples
- **Executive Summary:** “We can recover X by doing Y, proven by Z model with error of A.”  
- **Driver Ranking:** Table with top 5 levers, direction, and expected lift.  
- **Peer Benchmark:** Position vs peers, highlight gap, and recommended target.  
- **Program Impact:** Chart with pre/post or treated vs control, plus verdict and confidence.  
- **Exception List:** Top anomalies with why they were flagged and what to check.

## Delivery Notes
- Always show data currency (last refresh date and version).  
- Keep tooltips/plain labels instead of acronyms.  
- Provide a download link for the processed dataset used in the page.  
- End with a clear next-step list: what to double-click, what to monitor, and what decision is ready now.
