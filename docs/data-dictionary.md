# Data dictionary

All three files are practice data for a made-up company, Northbank Freight Services (140 employees). No real company, person or incident is in them. The incident file was generated for this project. The risk file comes from my Project 2 risk register.

## security_incidents.csv (one row per incident)
| Column | Meaning |
|---|---|
| incident_id | Unique ID, for example INC-0001 |
| detected_at | Date and time the incident was detected |
| detected_date | Date part of detected_at, used to link to the calendar table |
| first_response_at | Date and time someone first responded. Blank if nobody has responded yet |
| resolved_at | Date and time the incident was resolved. Blank if still open |
| incident_type | Kind of incident, for example Phishing Email or Lost or Stolen Device |
| severity | Critical, High, Medium or Low |
| department | Department affected |
| asset_type | Type of asset involved, for example Laptop or File Server |
| detection_source | How it was found, for example Email Gateway or User Report |
| status | Open or Closed |
| related_risk_id | The risk in the risk register that this type of incident relates to (R-01 to R-14) |

The period is 1 Oct 2025 to 30 Sep 2026. Anything not resolved by 1 Oct 2026 is Open.

## sla_targets.csv (one row per severity)
| Column | Meaning |
|---|---|
| severity | Critical, High, Medium or Low |
| respond_target_hours | Target hours from detection to first response |
| resolve_target_hours | Target hours from detection to resolution |
| sort_order | 1 for Critical to 4 for Low, used to sort charts |

The targets are my own assumptions for this practice company.

## risk_register.csv (one row per risk)
| Column | Meaning |
|---|---|
| risk_id | R-01 to R-14 |
| risk_title | Short name of the risk |
| csf_function | NIST CSF 2.0 Function |
| csf_category | NIST CSF 2.0 Category |
| likelihood, impact | Scores from 1 to 5 |
| inherent_score, inherent_rating | Likelihood x impact today, and its rating |
| residual_score, residual_rating | Expected score after the recommended action |
| treatment | Mitigate, accept, transfer or avoid |
| owner_role | Role responsible for the risk |
| priority | When the action should be done |
| action_status | Made-up status of the action (Not started or In progress) for practice |

## Cleaning
The raw incident file (`data/raw/security_incidents_raw.csv`) had problems that I fixed before analysing. The cleaned file is `data/security_incidents.csv`. Every change is listed in `docs/cleaning-log.md`.
- 3 duplicate rows removed (same incident_id twice)
- 4 incident types fixed (lowercase with a space at the end)
- 5 blank departments set to "Unknown"
- `detected_date` column added

Blank `first_response_at` and `resolved_at` values were left blank on purpose. They mean nobody has responded yet, or the incident is still open.

After cleaning there are 414 incidents.
