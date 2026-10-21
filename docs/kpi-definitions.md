# KPI definitions

These are the measures used on the dashboard, and how I worked each one out.

| KPI | Definition |
|---|---|
| Total incidents | Count of incidents in the selected period |
| Open incidents | Incidents with status Open |
| Open Critical and High | Open incidents with severity Critical or High |
| Average hours to respond | Average of (first_response_at minus detected_at) in hours, for incidents that have a response |
| Mean time to resolve (MTTR) | Average of (resolved_at minus detected_at) in hours, for Closed incidents only |
| Resolved within SLA % | Closed incidents resolved within the resolve target for their severity, divided by all Closed incidents |
| Responded within SLA % | Incidents responded to within the respond target for their severity, divided by all incidents with a response |
| Incidents per risk | Count of incidents linked to a risk through related_risk_id |
| Inherent and residual score | Taken from the Project 2 risk register |

## SLA targets (assumed)
| Severity | Respond within | Resolve within |
|---|---|---|
| Critical | 1 hour | 24 hours |
| High | 4 hours | 72 hours |
| Medium | 8 hours | 120 hours |
| Low | 24 hours | 240 hours |

## Notes
- Open incidents are left out of MTTR and the resolve SLA, because they have no resolution time yet.
- The links between incident types and risks are my own judgement. For example, phishing incidents are linked to R-03 (email accounts taken over).
