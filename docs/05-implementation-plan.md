# 05 — Step-by-Step Implementation Plan

This is a recommended execution sequence; exact UI labels may differ by GHL account/version.

## Phase A — Discovery and Setup
1. Confirm target agency, sample services, lead sources, and buyer journey.
2. Establish GHL sub-account, authorized users, permissions, and test-only contact records.
3. Verify calendars, sender domains, phone/messaging configuration, and consent requirements.
4. Record baseline funnel KPIs and approve message templates.

**Deliverable:** Requirements and configuration checklist approved.

## Phase B — CRM Foundation
5. Create the sales opportunity pipeline and stage definitions from `02-crm-data-model.md`.
6. Configure custom fields, tags, and lead source taxonomy.
7. Define contact deduplication, routing, and ownership rules.
8. Create intake forms/landing page with explicit consent capture.

**Deliverable:** Synthetic form submission creates correct CRM records.

## Phase C — Core Automations
9. Build and test WF-01 intake before enabling downstream workflows.
10. Build qualification and assignment logic with review fallback.
11. Build approved acknowledgments and outreach tasks.
12. Configure booking calendar and appointment state changes.
13. Add proposal follow-up, onboarding, and re-engagement workflows.
14. Confirm stop conditions, opt-outs, duplicate prevention, and manual overrides.

**Deliverable:** Core lead-to-onboarding happy path works in test environment.

## Phase D — Optional Advanced Integrations
15. Define webhook payload contracts and authentication.
16. Configure n8n flow, secrets, validation, logging, and retry handling.
17. Add optional AI classification with schema checks and human review.
18. Verify rate limits, timeouts, error alerts, and field mappings.

**Deliverable:** Optional integrations pass controlled tests or remain explicitly out of scope.

## Phase E — QA, Demo, and Handover
19. Execute the test plan using synthetic contacts.
20. Fix defects and rerun failed tests.
21. Capture genuine screenshots of forms, workflows, pipeline, calendars, and results.
22. Record a reproducible demo with no real client personal data.
23. Update README status checkboxes and publish an honest case study.

**Deliverable:** Evidence-backed portfolio repository.

## Suggested GitHub Folder Layout
```text
ghl-ai-marketing-agency-os/
├── README.md
├── docs/
│   ├── 01-project-overview.md
│   ├── 02-crm-data-model.md
│   ├── 03-automation-workflows.md
│   ├── 04-integrations-architecture.md
│   ├── 05-implementation-plan.md
│   ├── 06-test-plan.md
│   └── 07-evidence-demo.md
└── evidence/            # Add only real, sanitized evidence later
```
