# 04 — Integrations and Technical Architecture

## System of Record
GoHighLevel is the proposed operational CRM for contacts, opportunities, and appointments. External tools must not overwrite authoritative fields without a documented mapping and conflict policy.

## Optional Integration Patterns
| Source | Destination | Method | Data | Controls |
|---|---|---|---|---|
| Website form | GHL | Native form or supported API | Lead details and consent | Validation and deduplication |
| GHL workflow | n8n | Authenticated webhook | Event ID, contact reference, type | Authentication, replay protection |
| n8n | AI API | HTTPS API | Minimum necessary qualification context | Redaction, policy, schema validation |
| n8n | GHL | Supported API | Qualification result, routing decision | Rate limiting, retries, permissions |
| GHL | Messaging provider | Native supported channel | Approved notifications | Consent, opt-out, quiet hours |

## Example Logical Sequence
1. Lead is submitted through approved source.
2. GHL creates or updates the contact.
3. GHL workflow invokes n8n only when external processing is needed.
4. n8n validates request and processes event with a stable event ID.
5. Optional AI returns a structured suggestion.
6. n8n validates response and updates only permitted fields in GHL.
7. GHL assigns owner and triggers appropriate follow-up.

## Failure and Reliability Design
- Maintain event identifiers to avoid duplicate processing.
- Retry transient failures with bounded exponential backoff; do not retry permanent validation errors indefinitely.
- Route persistent failures to an exception queue or alert.
- Respect API rate limits and webhook provider guidance.
- Record correlation IDs, timestamps, status, and non-sensitive diagnostics.

## Security
Store secrets in platform-managed credentials/environment secrets, not GitHub. Use least-privilege API permissions. Restrict webhook endpoints, rotate credentials, audit access, and avoid exposing customer PII in logs or AI prompts.

## Decisions to Confirm Before Build
GHL plan/features, exact channels and messaging regions, third-party integration availability, hosting for n8n, AI vendor approval, retention periods, and authoritative data ownership.
