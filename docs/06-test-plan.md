# 06 — Functional Test Plan and UAT

**Current status:** Test cases authored; execution pending. Do not mark any case Passed until actual evidence exists.

| Test ID | Scenario | Steps | Expected result | Status |
|---|---|---|---|---|
| TC-01 | New valid lead | Submit test form with unique email | One contact and one eligible opportunity created | Not run |
| TC-02 | Duplicate intake | Submit same lead twice | No unintended duplicate opportunity/message | Not run |
| TC-03 | Missing required field | Submit invalid form/payload | Validation blocks or flags bad record | Not run |
| TC-04 | Qualified lead | Submit matching criteria | Correct qualification status and owner | Not run |
| TC-05 | Ambiguous lead | Submit incomplete/low-confidence profile | Routed to manual review | Not run |
| TC-06 | Email opt-out | Opt out then trigger follow-up | No prohibited email sent | Not run |
| TC-07 | SMS without consent | Trigger SMS workflow for ineligible contact | SMS suppressed | Not run |
| TC-08 | Appointment booked | Book via configured calendar | Opportunity and reminders reflect booking | Not run |
| TC-09 | Appointment canceled | Cancel test appointment | No stale reminders; rebooking path applied | Not run |
| TC-10 | Proposal converted | Move opportunity to Won | Proposal follow-up stops; onboarding starts once | Not run |
| TC-11 | Webhook replay | Deliver same event ID twice | External processing remains idempotent | Not run |
| TC-12 | Integration outage | Simulate timeout/5xx in test | Bounded retries and exception visibility | Not run |
| TC-13 | Human override | Change qualification manually | Automated process respects documented override | Not run |
| TC-14 | Pipeline reporting | Move synthetic deals through stages | Reported counts align with test records | Not run |

## Evidence Template
For each executed case, record: date/time, tester, environment, anonymized test record ID, steps performed, expected result, actual result, pass/fail, defect ID, and screenshot path.

## UAT Exit Criteria
All critical tests pass, consent/opt-out scenarios pass, high-severity defects are resolved, operational owners approve routing and messaging, and real evidence is captured.
