# 03 — Automation Workflow Specifications

All workflows below are **design specifications**, not claims of completed GHL configurations.

## WF-01 — New Lead Intake
**Trigger:** Approved GHL form submission or authenticated inbound integration.

1. Validate required fields and normalize email/phone.
2. Apply matching rules; create or update contact.
3. Record source, submission timestamp, and consent provenance.
4. Create opportunity only if an appropriate active opportunity does not already exist.
5. Set stage `New Lead` and invoke qualification/routing.
6. Log errors and queue records for manual review where needed.

**Guardrails:** Duplicate prevention, malformed payload rejection, no automatic consent assumption.

## WF-02 — Lead Qualification and Routing
**Trigger:** Validated new/updated lead with sufficient fields.

1. Evaluate explicit fit criteria (service, geography, budget band, timeline).
2. Optionally request AI structured classification; validate schema and confidence.
3. Route low-confidence/ambiguous results to human review.
4. Assign an eligible owner or a review queue; record routing reason.
5. Update qualification status without overwriting human decisions.

**Guardrails:** No discriminatory protected-attribute scoring; AI is advisory, not sole arbiter of consequential decisions.

## WF-03 — Initial Acknowledgment and Follow-Up
**Trigger:** New eligible lead with permitted communication channel.

1. Check consent, suppression, and contact-hours policy.
2. Send approved acknowledgment once.
3. Create an owner follow-up task.
4. Stop or branch on reply, appointment, opt-out, or invalid contact.
5. Prevent duplicate messages on resubmission.

## WF-04 — Appointment Lifecycle
**Trigger:** Appointment booked, rescheduled, canceled, or completed.

1. Match event to contact/opportunity.
2. Move to `Appointment Booked` where appropriate.
3. Send approved confirmation/reminders respecting consent and time zone.
4. On cancellation, offer an approved rebooking path.
5. On no-show, start limited recovery workflow with opt-out checks.

## WF-05 — Proposal Follow-Up
**Trigger:** Opportunity enters `Proposal Sent`.

1. Record proposal date and owner.
2. Schedule internal follow-up task.
3. Send approved reminders only while opportunity remains open and contact is eligible.
4. Stop on `Won`, `Lost`, opt-out, or explicit manual hold.

## WF-06 — Won Deal Onboarding
**Trigger:** Opportunity marked `Won` by authorized user.

1. Validate deal metadata and primary contact.
2. Create internal onboarding tasks/checklist.
3. Notify delivery owner.
4. Send approved welcome message if permitted.
5. Flag incomplete handoff data for human resolution.

## WF-07 — Inactive Lead Re-Engagement
**Trigger:** Lead inactivity exceeds approved threshold.

1. Check no active deal, no suppression, no recent conversation, and valid consent.
2. Start bounded, personalized re-engagement sequence.
3. Stop immediately on reply, opt-out, booking, or status change.
4. Record campaign results without assuming revenue attribution.

## Operational Standards
- Every workflow needs: owner, trigger, entry conditions, exit conditions, idempotency behavior, error handling, and rollback plan.
- Use synthetic records for testing and include negative cases.
- Document exact GHL trigger/action names after implementation because availability may vary by account.
