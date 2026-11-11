---
license: cc-by-4.0
language:
  - en
pretty_name: "US Commercial Insurance GLP-1 Prior-Authorization, Step-Therapy & Cash Bypass Benchmark (2026)"
size_categories:
  - n<1K
task_categories:
  - tabular-regression
  - tabular-classification
tags:
  - healthcare
  - pharmacoeconomics
  - telehealth
  - glp-1
  - health-policy
configs:
  - config_name: default
    data_files:
      - split: train
        path: payer_formulary_audit.csv
  - config_name: national_commercial_pbms
    data_files:
      - split: train
        path: subsets/national_commercial_pbms.csv
  - config_name: employer_self_insured_exclusions
    data_files:
      - split: train
        path: subsets/employer_self_insured_exclusions.csv
  - config_name: federal_medicare_aca_channels
    data_files:
      - split: train
        path: subsets/federal_medicare_aca_channels.csv
  - config_name: direct_503a_cash_bypass_benchmarks
    data_files:
      - split: train
        path: subsets/direct_503a_cash_bypass_benchmarks.csv
---

# US Commercial Insurance GLP-1 Prior-Authorization, Step-Therapy & Cash Bypass Benchmark (2026)

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24139325.svg)](https://doi.org/10.5281/zenodo.24139325)

**Published by:** Losing Weight RX Pharmacoeconomics & Consumer Audit Desk (Losing Weight RX LLC)  
**Canonical Interactive Dataset Hub:** [https://losingweightrx.com/datasets/us-commercial-insurance-glp1-pa-denial-formulary-2026/](https://losingweightrx.com/datasets/us-commercial-insurance-glp1-pa-denial-formulary-2026/)  
**Paired Statistical Audit Report:** [https://losingweightrx.com/blog/2026-commercial-insurance-glp1-prior-authorization-denial-audit](https://losingweightrx.com/blog/2026-commercial-insurance-glp1-prior-authorization-denial-audit)  
**Methodology & Editorial Governance:** [https://losingweightrx.com/editorial-standards](https://losingweightrx.com/editorial-standards)  
**Academic Identifier (DOI):** `10.5281/zenodo.24139325`  
**License:** Creative Commons Attribution 4.0 International (`CC-BY-4.0`)  
**Last Verified:** `2026-11-11`

---

## Executive Summary

Structured health-policy and payer-formulary audit across 108 US commercial PBM, self-insured employer, ACA Marketplace, Medicare Part D, and direct cash-pay benchmarks evaluating GLP-1 prior-authorization BMI gates, step-therapy durations, lifestyle-app locks, and Q1 deductible out-of-pocket exposure.

All numeric fields are strictly typed (`Float64` / `Int64` / `Boolean`) with zero currency-string symbols or untyped null placeholders, enabling zero-friction ingestion into Apache Parquet, DuckDB, Polars, Pandas, and `datasets.load_dataset("losing-weight-rx/us-commercial-insurance-glp1-pa-denial-formulary-2026")`.

## Multi-Configuration Splits Included

| Config Name | File Path | Description |
| :--- | :--- | :--- |
| `default` | `payer_formulary_audit.csv` | Complete audited dataset (`all` records) |
| `national_commercial_pbms` | `subsets/national_commercial_pbms.csv` | Filtered analytical split (`42` records) |
| `employer_self_insured_exclusions` | `subsets/employer_self_insured_exclusions.csv` | Filtered analytical split (`24` records) |
| `federal_medicare_aca_channels` | `subsets/federal_medicare_aca_channels.csv` | Filtered analytical split (`30` records) |
| `direct_503a_cash_bypass_benchmarks` | `subsets/direct_503a_cash_bypass_benchmarks.csv` | Filtered analytical split (`12` records) |

## Column Schema (`20` Strictly Typed Fields)

- `formulary_record_id`
- `payer_or_benchmark_entity`
- `plan_channel_category`
- `pbm_administrator`
- `covered_indication_scope`
- `molecule_evaluated`
- `prior_authorization_mandated_boolean`
- `min_bmi_threshold_no_comorbidity`
- `comorbidity_bmi_threshold`
- `step_therapy_months_required`
- `mandatory_coaching_app_lock_boolean`
- `employer_rider_opt_in_required_boolean`
- `typical_annual_deductible_exposure_usd`
- `monthly_copay_or_cash_rate_usd`
- `estimated_q1_out_of_pocket_usd`
- `estimated_12month_patient_spend_usd`
- `pa_reauthorization_interval_months`
- `median_approval_turnaround_days`
- `access_friction_index_100`
- `canonical_source_url`

## Scoring Framework: LWR Consumer Price-Lock & Dose-Parity Index (v1.0)

Records are evaluated deterministically across four verifiable consumer-protection axes:
1. **Dose-Escalation Parity:** Whether high maintenance doses (`2.4 mg` semaglutide / `15.0 mg` tirzepatide) maintain the same monthly rate as starter titration vials (`0.25 mg` / `2.5 mg`).
2. **Fee Unbundling Disclosure:** Whether recurring platform membership fees (`$75-$199/mo`), lab markups, or initial consult charges are separated from medication pricing.
3. **Contractual Exit Freedom:** Month-to-month cancel-anytime billing vs. mandatory 3-, 6-, or 12-month non-refundable upfront locks.
4. **Pharmacoeconomic Yield:** Effective out-of-pocket USD per milligram of active ingredient or bioavailable dose delivered.

## Citation (BibTeX)

```bibtex
@dataset{lwr_us_commercial_insurance_glp1_pa_denial_formulary_2026,
  author       = {Losing Weight RX Pharmacoeconomics & Consumer Audit Desk},
  title        = {US Commercial Insurance GLP-1 Prior-Authorization, Step-Therapy & Cash Bypass Benchmark (2026)},
  year         = {2026},
  publisher    = {Zenodo},
  doi          = {10.5281/zenodo.24139325},
  url          = {https://losingweightrx.com/datasets/us-commercial-insurance-glp1-pa-denial-formulary-2026/}
}
```
