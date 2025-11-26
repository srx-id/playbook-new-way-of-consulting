# New Way of Consulting (Top-Down + ML Bottom-Up)

Plain-language guide to secure the right data upfront so the analysis is fast, defensible, and dashboard-ready. No week-by-week promises—just what to ask for and what “good enough” looks like.

## Ask for These Core Tables
- **Performance by period:** One row per entity per period (site/branch/plant/vendor/vehicle, by day or month). Include the north-star metric and supporting metrics (e.g., output volume, success/failure counts, cost, revenue).
- **Operational events:** Time-stamped events that create the performance (e.g., deliveries, journeys, work orders). Must have IDs, start/end time, location if relevant, and status/outcome.
- **Context/master data:** Static attributes for entities (region, size, capacity, equipment, contract type, partner tier). Keep code lists consistent with the performance table.
- **Intervention markers:** Flags for pilots/rollouts/changes (on/off dates) so we can estimate impact.
- **Reference targets:** Business targets or thresholds per metric to anchor “so what”.

## Minimum Viable Specs (Borrowed from Past Work)
- **Operations performance (analogous to production/yield work):**
  - Periodic table with metric (e.g., yield %, throughput, quality rate), volume, and cost.
  - Attributes: site/plant ID, region, capacity band, process flags.
  - Intervention flag: pilot vs control, before/after change date.
- **Transport/security (analogous to journey risk work):**
  - Event table: journey ID, vehicle ID, start/end timestamp, coordinates or zones, distance, duration, idle time, speed stats, status codes.
  - Optional enrich: stop locations, route geometry or snapped polyline, anomaly notes.
  - Attributes: vehicle type, partner, route class, risk zones (green/red) if available.
- **Procurement/partner performance (analogous to vendor scorecards):**
  - Order/transaction table: order ID, partner ID, timestamps, SLA status (on-time/late/fail), cost/price, location, product/service type.
  - Partner master: segment/tier, region, contract terms, capacity, specialties.
  - Outcomes: success/failure counts, delays, cancellations, rework flags.

## Data Quality Guardrails (Client-Friendly)
- **Coverage:** Share what periods and entities are present/missing; no blame, just a map.
- **Consistency:** One ID system per entity; provide a mapping table if systems differ.
- **Timestamps:** Clear timezone; start/end pairs for durations.
- **Units:** State units for distance/time/currency/volume; avoid mixed units in one column.
- **Duplicates:** Allow us to drop exact duplicates; flag how many were removed.
- **Missing values:** Distinguish “not applicable” vs “unknown”; keep blanks, don’t force zeros.

## How to Ask (Without Blaming Data)
- Position the request as enabling faster insight: “With these five columns we can deliver the exec story and the driver ranking.”
- Offer the template: a tidy CSV/Parquet example with IDs, timestamps, outcome/status, and key attributes.
- Commit to return a profiling note first (what’s in/out) before any modeling.
