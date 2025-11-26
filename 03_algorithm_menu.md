# Algorithm Menu (Plain Words)

## Outside-In Benchmark
- **What:** Use ready-made AI models to scan public text/images to spot peers and practices.  
- **Why:** Gives a fast “where we stand” view before internal data is perfect.  
- **Output:** Peer map and a shortlist of ideas to test internally.

## Simple, Explainable Drivers
- **What:** Straightforward regression that shows which factors push results up or down.  
- **Why:** Easy to explain; numbers stay in business units (percentage points, minutes, currency).  
- **Output:** Top drivers with direction (↑/↓) and estimated effect size.

## Extra Accuracy When Needed
- **What:** Tree-based models that capture interactions (e.g., seasonality by region).  
- **Why:** Better predictions while we keep explanations via a short driver list and “what-if” curves.  
- **Output:** More accurate forecasts plus stable driver ranking.

## Spotting Outliers and Risky Cases
- **What:** Anomaly detector plus a few clear rules.  
- **Why:** Flags journeys/branches/partners/assets/customers that behave unlike peers, with reasons.  
- **Output:** Risk bands (monitor, spot-check, investigate) and a short “why flagged” note.

## Measuring Program Impact
- **What:** Before/after plus control-vs-pilot comparison methods.  
- **Why:** Answers “did the change help?” without heavy math in the readout.  
- **Output:** Uplift estimate with confidence and a plain verdict (“visible improvement” vs “not yet visible”).

## Quick Selection Guide
- Need a story before internal data is ready → Outside-in benchmark.  
- Need trusted drivers in plain math → Simple, explainable drivers.  
- Need tighter forecasts/targeting → Extra accuracy.  
- Need to catch bad actors/weird trips → Outlier and risk detection.  
- Need to prove a program worked → Impact measurement.  
- Have high-frequency data later → Consider sequence/time-series models; not needed for monthly data.
