# 02 — CRM and Data Model

## Proposed Pipeline Stages
| Stage | Entry criteria | Primary owner action | Exit condition |
|---|---|---|---|
| New Lead | Intake accepted | Review source and consent | Outreach attempted |
| Contact Attempted | Outreach recorded | Retry within approved policy | Response or disqualification |
| Engaged | Two-way interaction | Collect qualifying details | Fit evaluated |
| Qualified | Qualification rules met | Invite booking | Appointment booked |
| Appointment Booked | Calendar event confirmed | Prepare consultation | Meeting completed / rescheduled |
| Proposal Sent | Proposal delivered | Track decision and follow-up | Won or Lost |
| Won | Commercial acceptance confirmed | Initiate onboarding | Handoff complete |
| Lost | Closed without sale | Record reason and permitted re-engagement | Closed |

## Recommended Custom Fields
| Field | Type | Notes |
|---|---|---|
| lead_source | Enum/text | Origin system or campaign |
| service_interest | Enum | Requested service |
| estimated_budget_band | Enum | Optional; avoid unnecessary precision |
| timeline | Enum | Desired start timeframe |
| qualification_status | Enum | Unreviewed / Qualified / Review / Disqualified |
| qualification_reason | Text | Brief human-readable explanation |
| assigned_team | Enum/text | Routing destination |
| consent_email | Boolean + timestamp/source | Maintain auditable evidence |
| consent_sms | Boolean + timestamp/source | Separate from email consent |
| last_contact_attempt | Date/time | Outreach reporting |
| lost_reason | Enum | Reporting and analysis |

## Record Management Rules
- Define match precedence (for example normalized email; phone only when appropriate).
- Never silently merge ambiguous identities; route for review.
- Treat contact and opportunity as different entities; one contact may have multiple service opportunities.
- Preserve original lead source when required and track latest campaign separately.
- Restrict field access by role; avoid storing secrets or sensitive information in free text.

## Reporting KPIs
Time to first outreach, qualified-lead percentage, appointment booking percentage, show percentage, proposal win percentage, and opt-out rate. Define numerator, denominator, time window, and exclusions before publishing dashboards.
