# XHUMANITY

XHUMANITY is a standards-first initiative focused on one measurable mission:

- **Reduce global carbon emissions by 10 million kg CO2e (10,000 metric tons CO2e) in 3 years**.

This repository provides the revvel-standards ship-to-market baseline for that mission.

## Revvel-Standards S2M Rules

- Every WR/PR must ship in one iteration with a complete, testable website/UI surface.
- If the product core is ACL, API, or MCP, include a companion UI/website flow (engine-style test surface) so the tool can be exercised end to end.

## Front-to-Back Research Engine Requirement

Every S2M WR/PR must ship a fully wired research engine from intake to deployment output in the same iteration:

1. Intake research signals (energy module candidates + source evidence)
2. Evaluate/score modules (abatement, readiness, regional fit)
3. Publish outcomes in a testable website/UI dashboard and machine-readable export
4. Execute pilot/deployment decisions using the same scored outputs

Implementation details are defined in `GO_TO_MARKET.md` and `DEPLOYMENT_GUIDE.md`.

## 3-Year Objective

- Baseline period: 2026 start
- Target window: 3 years
- Cumulative reduction target: **10 million kg CO2e (10,000 metric tons CO2e)**
- Primary levers:
  1. Grid decarbonization acceleration
  2. Building efficiency retrofits
  3. Industrial electrification and fuel switching
  4. Methane leak detection and abatement
  5. Reforestation and verified carbon removals

## Delivery Artifacts (revvel-standards)

- `CHANGELOG.md`
- `DEPLOYMENT_GUIDE.md`
- `GO_TO_MARKET.md`
- `BRAND_GUIDELINES.md`
- `SECURITY.md`

## Website-in-Test (Required)

Every S2M WR/PR must publish a live website/UI test surface and record it in this README:

- `Website in Test (Vercel)`: `<vercel-preview-or-production-url>`
- `Intervention API/Test Export`: `<endpoint or path to intervention_modules.json>`
- `Build/Deploy Automation`: `<workflow or deployment job reference>`

If these fields are missing, the WR/PR is not revvel-standards complete.

## Quick Start

1. Review the strategy in `GO_TO_MARKET.md`.
2. Use `DEPLOYMENT_GUIDE.md` to launch pilots.
3. Track updates in `CHANGELOG.md`.
