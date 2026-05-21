# Deployment Guide

This guide defines how to deploy XHUMANITY programs toward the 2035 emissions target.

## 1) Program Setup (Weeks 1-4)

- Create a country/region emissions baseline (electricity, buildings, industry, methane).
- Define local reduction quota aligned to the global 1.5 trillion kg CO2e target using:
  - Share of baseline emissions (50% weight)
  - Abatement potential by sector (30% weight)
  - Delivery readiness (20% weight)
- Abatement Potential Score: normalized 0-1 score from technical potential model (`regional feasible tCO2e reduction / max regional feasible tCO2e reduction`), where the denominator is the highest feasible reduction value observed across all regions in the same planning cycle.
- Delivery Readiness Score: normalized 0-1 score from implementation readiness index (permitting maturity, partner readiness, financing availability, and grid interconnection readiness).
- Technical potential model definition:
  - `regional feasible tCO2e reduction = sum(sector baseline emissions × feasible reduction % within 2035 window)` across electricity, buildings, industry, and methane.
- Implementation readiness index definition (equal weighting):
  - `Readiness Score = 0.25(Permitting) + 0.25(Partner) + 0.25(Financing) + 0.25(Grid)`, with each factor scored 0-1 against a published rubric.
- Calculation formula: `Quota Share = 0.5(Baseline Share) + 0.3(Abatement Potential Score) + 0.2(Delivery Readiness Score)`.
- Store and compute `Quota Share` as a decimal value (0-1); convert to percentage only for reporting output.
- Example: if a region scores 0.10 baseline share, 0.12 abatement potential, and 0.08 readiness, quota share = `0.5(0.10)+0.3(0.12)+0.2(0.08)=0.102` (**0.102, or 10.2%**) of global pathway allocation.
- Apply a 0.9 conservatism factor uniformly across intervention types to account for historical model overestimation and verification lag, and keep a public registry of project IDs to prevent double counting.
- Select pilot partners (utilities, municipalities, industrial operators).

## 2) Pilot Deployment (Months 2-6)

- Launch three pilot lanes:
  - Energy efficiency retrofits
  - Methane abatement
  - Renewable procurement + electrification
- Stand up monthly emissions accounting (tCO2e avoided).
- Require third-party MRV (measurement, reporting, verification) for claims.

## 3) Scale Deployment (Months 7-24)

- Expand successful pilots by cost-per-ton and feasibility score.
- Prioritize projects with:
  - <$100/tCO2e abatement cost
  - <18 month implementation cycle
  - Auditable reduction data

## 4) Governance

- Publish quarterly scorecards: planned vs achieved reductions.
- Use conservative accounting (no double counting, no unverifiable offsets).
- Escalate underperformance with corrective plans within 30 days.
