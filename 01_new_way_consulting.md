# New Way of Consulting (Top-Down + Bottom-Up)

Plain guide for non-technical consultants: what data to ask for, what “good enough” looks like, and how to ask without blaming data.

## What to Ask For
- **Performance by period:** Simple table (spreadsheet is fine) with one row per site/branch/partner per day or month. Include the headline result and supporting numbers (volume, success/fail counts, cost, revenue).
- **Activities that create the result:** Rows for each delivery/journey/order/work order with IDs, start/end time, location (if relevant), and outcome/status.
- **Reference info:** A short list of attributes for each site/partner/vehicle (region, size, capacity band, contract type). Use the same IDs as above.
- **Change markers:** On/off dates for pilots, rollouts, or policy changes so we can see before/after impact.
- **Targets:** The business targets or thresholds you already use, so “so what” is clear.

## “Good Enough” Examples (Taken from past projects)
- **Operations performance:**  
  - Table by period with result (e.g., yield/quality/service level), volume, and cost.  
  - Attributes for each site: region, size, capacity band, a few process flags.  
  - Simple flag for sites in a pilot versus control, with start date.
- **Transport/security:**  
  - Trip table: journey ID, vehicle ID, start/end time, distance, duration, idle minutes, basic speed stats, status code.  
  - Optional: stop locations or zones; a note if a trip is clearly unusual.  
  - Vehicle attributes: type, partner, route class; zone labels if you already have them.
- **Procurement/partner performance:**  
  - Order table: order ID, partner ID, timestamps, on-time/late/fail, cost/price, location, product/service type.  
  - Partner list: tier/segment, region, contract terms, capacity, specialties.  
  - Outcomes: counts of delays, cancellations, rework.

## Friendly Data Checks (No Blame)
- **Coverage:** Which periods and entities are present or missing; just share the map.  
- **IDs:** One ID per entity; if there are two systems, give a short mapping table.  
- **Time:** Include timezone; start and end for anything with a duration.  
- **Units:** Say the unit (currency, minutes, km, pieces) and keep it consistent per column.  
- **Duplicates:** OK to remove exact duplicates; note how many.  
- **Missing:** Leave blank if unknown; avoid guessing zero.

## How to Ask
- “With these few columns we can build the executive story and the supporting dashboard quickly.”  
- Share a simple example table with the columns above instead of technical terms.  
- Promise a short “what’s in/out” note before any modeling or coding.  
