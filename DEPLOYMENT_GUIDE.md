# Deployment Guide

This guide defines how to deploy XHUMANITY in a single ship-to-market iteration toward a 3-year target of 10 million kg CO2e reduction (10,000 metric tons CO2e), followed by continuous monitoring and reporting.

## Single Iteration Deployment

- Create a country/region emissions baseline (electricity, buildings, industry, methane).
- Run the **Intervention Discovery Engine** in the same one-iteration release and publish results in the project website/UI test surface as:
  - A dashboard page summarizing module priority scores (derived from abatement + readiness) and rollout state, and
  - A machine-readable export (`intervention_modules.json`) for tool testing.
- Minimum required module search coverage per WR/PR:
  - Heat pumps and building electrification
  - Solar and other distributed clean-power modules
  - Water-based generation pathways (hydro/marine where viable)
  - Green software and AI/data-center efficiency pathways
  - Creative co-benefit modules (AWG, rooftop gardens/biosolar) when regionally feasible
- For each candidate module, store: evidence links, readiness constraints, expected 3-year abatement contribution, and pilot measurement design.
- Minimum JSON schema for `intervention_modules.json`:
  - `module_id` (required string, lowercase alphanumeric segments with optional underscore separators, regex `^[a-z0-9]+(_[a-z0-9]+)*$`, 1-64 chars; examples: `solar`, `heat_pump_residential`)
  - `module_name` (required string, 1-120 chars)
  - `evidence_links` (required array of 1+ URLs, each matching `^https://`)
  - `readiness_constraints` (required array of 1+ strings, each 1-240 chars)
  - `expected_abatement_kg_co2e` (required number, projected abatement value, `>= 0`)
  - `abatement_period_years` (required integer, currently `3` for this standard)
  - `pilot_measurement_plan` (required string, 1-1000 chars)
  - `status` (required enum value: `candidate`, `pilot`, or `deployed`)
  - `priority_score_0_1` (optional number, normalized 0-1 ranking score used by dashboard ordering)
  - `deployment_date` (optional string, ISO 8601 date format `YYYY-MM-DD`)
  - `region_applicability` (optional array of region/country codes)
- Define local reduction quota aligned to the global 10 million kg CO2e target using:
  - Share of baseline emissions (50% weight)
  - Abatement potential by sector (30% weight)
  - Delivery readiness (20% weight)
- Abatement Potential Score: normalized 0-1 score from technical potential model (`regional feasible tCO2e reduction / max regional feasible tCO2e reduction`), where the denominator is the highest feasible reduction value observed across all regions in the same planning cycle.
- Delivery Readiness Score: normalized 0-1 score from implementation readiness index (permitting maturity, partner readiness, financing availability, and grid interconnection readiness).
- Technical potential model definition:
  - `regional feasible tCO2e reduction = sum(sector baseline emissions × feasible reduction % within 3-year window)` across electricity, buildings, industry, and methane.
  - Feasible reduction percentages are sourced from the current planning cycle's sector abatement assumptions register and must be versioned in deployment records.
  - Register location: `DEPLOYMENT_GUIDE.md` deployment records appendix maintained by program operations for each planning cycle.
- Implementation readiness index definition (equal weighting):
  - `Readiness Score = 0.25(Permitting) + 0.25(Partner) + 0.25(Financing) + 0.25(Grid)`, with each factor scored 0-1 against a published rubric.
- Calculation formula: `Quota Share = 0.5(Baseline Share) + 0.3(Abatement Potential Score) + 0.2(Delivery Readiness Score)`.
- Store and compute `Quota Share` as a decimal value (0-1) to 6 decimal places; convert to percentage only for reporting output.
- Example: if a region scores 0.10 baseline share, 0.12 abatement potential, and 0.08 readiness, quota share = `0.5(0.10)+0.3(0.12)+0.2(0.08)=0.102` (**0.102, or 10.2%**) of global pathway allocation.
- Apply a 0.9 conservatism factor uniformly across intervention types to account for historical model overestimation and verification lag (default uncertainty buffer until replaced by annual third-party calibration), and keep a public registry of project IDs to prevent double counting.
- Select launch partners (utilities, municipalities, industrial operators).
- Confirm the one-iteration release includes a testable website/UI; for ACL/API/MCP-first implementations, confirm companion interface flows are live for tool testing.

- Publish quarterly scorecards: planned vs achieved reductions.
- Use conservative accounting (no double counting, no unverifiable offsets).
- Escalate underperformance with corrective plans within 30 days.

## Deployment Records Appendix

- Maintain the sector abatement assumptions register in deployment records for each planning cycle version.
