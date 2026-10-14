# 07 — Evidence and Live Demo Checklist

## Evidence Rules
Only upload genuine screenshots or recordings captured from your own configured GHL/n8n test environment. Do not label mockups, conceptual diagrams, or generated UI illustrations as working software. Blur names, email addresses, phone numbers, tokens, and client details.

## Screenshot Checklist
- [ ] GHL pipeline showing synthetic opportunity stages
- [ ] Intake form and consent fields
- [ ] Contact record with source and qualification fields
- [ ] Workflow editor for new lead intake
- [ ] Qualification/routing workflow and owner assignment
- [ ] Booking calendar and test confirmation
- [ ] Consent/opt-out suppression proof
- [ ] Won opportunity triggering onboarding tasks
- [ ] Optional n8n execution with sensitive values hidden
- [ ] Optional AI output validation / human-review path
- [ ] Reporting view with clearly labeled synthetic data
- [ ] Test case results and defects log

## Suggested 6–8 Minute Demo
1. **Business problem (45 seconds):** Explain fragmented lead handling and intended outcomes.
2. **Architecture (45 seconds):** Show README diagram and system boundaries.
3. **Lead intake (60 seconds):** Submit a synthetic test lead.
4. **Qualification and pipeline (90 seconds):** Show field updates and routing.
5. **Booking and follow-up (60 seconds):** Demonstrate event and message guardrails.
6. **Won-to-onboarding (60 seconds):** Move synthetic opportunity and inspect tasks.
7. **Exceptions and results (60 seconds):** Show opt-out test, failure handling, and honest metrics.

## Evidence Naming Convention
`evidence/YYYY-MM-DD_TC-01_new-lead-intake.png` etc. Include an `evidence/README.md` later with screenshot descriptions and test environment information.

## Portfolio Case Study Template
**Challenge:** What business problem was addressed?

**Approach:** Which GHL workflows and integrations were implemented?

**Validation:** Which tests passed and what evidence proves them?

**Results:** Report only measured metrics with baseline, period, and methodology. If no production results exist, state that clearly.

**Next steps:** Known limitations, security considerations, and planned improvements.
