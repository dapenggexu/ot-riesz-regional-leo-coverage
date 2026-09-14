# Regional LEO coverage results

The three **2026-06-19 tables are superseded** by the revalidated files below. They remain unchanged only for historical traceability and must not be used as the current physical-performance results.

| Superseded file | Current file |
|---|---|
| `main_3seed_best_by_N_median_20260619.csv` | `main_3seed_best_by_N_median_20260914_revalidated.csv` |
| `focused_5seed_candidate_summary_20260619.csv` | `focused_5seed_candidate_summary_20260914_revalidated.csv` |
| `ablation_summary_20260619.csv` | `ablation_summary_20260914_revalidated.csv` |

## Evaluation version

Revalidation date: 2026-09-14. Frozen scientific-source and region-data bundle SHA-256: `b57bcb2458d6a4aa7f22fc1d7dbd58022f05761f00f71567a8a58127b72ae2ee`.

The updated evaluation uses the corrected ECI-to-ECEF rotation `R3(-omega_E*t)` and the area-weighted empirical inverse-CDF P95. The superseded tables used weighted-CDF interpolation; this quantile change does not affect MaxGap. Both OT candidate scoring and final coverage evaluation use the corrected propagation. OT–Riesz and OT-only were reselected from their original seeded pools of 60 candidates. Riesz-only pool selections were verified against the historical angles, then reevaluated. Fixed historical Walker-like angles were preserved and reevaluated.

The inputs comprise 162 main runs, 28 additional seed runs and 30 ablation/reference rows. Nine exact duplicate scientific configurations were executed once and explicitly mapped back, giving 211 unique configurations. The model remains two-body, 550 km altitude, 53 degree inclination, a 24-hour finite window and 60-second sampling over the Kazakhstan ADM0 polygon. Objective/evaluation grids have 579/2410 points. Objective scoring uses time stride 2 (721 samples); final evaluation uses 1441 samples. Candidate generation and objective weights are unchanged. Memoization only reuses an identical fixed objective grid; an uncached comparison verified identical candidate scores and outputs.

## Fields and aggregation

- Times are in minutes. `P95_*` summarizes the **area-weighted 95th percentile of grid-point maximum finite-window gaps**, not the pooled distribution of all gaps. Each unvisited point has a 1440-minute maximum gap. `Max_*` summarizes the largest point-level gap.
- `_median`, `_min` and `_max` aggregate runs independently. They need not describe the same layout. `seed_count` is the number of runs in that row; fixed Walker-like references have one run.
- The main table first aggregates seeds 0/1/2 within each N/FOV/slew setting, then retains the setting with the lowest P95 median for each N.
- The focused table preserves all 14 historical settings, combining seeds 0/1/2 with additional seeds 3/4. The ablation table groups by N and method, with three seeds per random-search method.
- `uncovered_median` is the unweighted fraction of grid points never visited. `mean_coverage_fraction_median` is area weighted.
- `OT_cost_median` is the reported transport cost. `Riesz_median` is normalized angular energy. `Total_obj_median` is the reported weighted objective: OT-only uses zero Riesz weight; Riesz-only reports the full objective after Riesz-only selection. It is not a common selection score across methods.

The historical Walker-like references are N24 = 5/5/5/5/4 (missing the 288 degree RAAN, 288 degree phase slot), N30 = 5×6, and N36 = 6×6. The N24 reference is distinct from a divisible standard Walker 24/K/F family. These tables do not establish universal superiority of either method or constellation family.
