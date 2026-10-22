# Service Desk Ticket Lifecycle and Escalation Standard

## Purpose

This standard keeps incidents reviewable from intake through closure. It is platform-neutral and should be mapped to the organization’s service-management tool, SLA, routing model, and data policy.

## 1. Intake and classification

Create one primary record for one user-impacting issue. Link related records when multiple users report the same service failure.

Required intake fields:

- Concise subject using `service - component - symptom`
- Requester and contact channel
- Affected service, device, or location using approved inventory values
- Start time, last-known good time, and time zone
- Scope, impact, urgency, and business consequence
- Exact error and reproduction steps
- Current workaround, if any

Do not copy passwords, MFA codes, private keys, payment data, or unnecessary personal information into the ticket.

## 2. Priority

Set priority from impact and urgency, not a requester’s title.

- **Impact:** how many users, locations, or critical services are affected.
- **Urgency:** how quickly the consequence must be addressed.
- **Priority:** the service desk’s approved combination of impact and urgency.

Use the organization’s current priority matrix and SLA. Do not copy example response targets into a new environment without approval.

## 3. Working notes

Record each meaningful action in chronological order:

```text
Time:
Observation:
Action:
Result:
Interpretation:
Next step:
```

Distinguish user statements, observed facts, inference, change, and verified result. Attach only necessary, sanitized evidence. Screenshots must hide unrelated personal or confidential data.

## 4. Status model

- **Open or In Progress:** the assigned team is actively investigating or communicating.
- **Pending:** the record is waiting for an identified user, vendor, approval, part, or internal dependency. Record the owner and next review time.
- **Resolved:** service is restored or a confirmed outcome is delivered, and the requester has been informed.
- **Closed:** the organization’s review or reopen window has completed.

Tool labels vary. Follow the local workflow and automations.

## 5. Communication

At each meaningful state change, tell the requester:

- What is known
- What remains unknown
- What was changed, if anything
- Current impact or workaround
- Who owns the next action
- When the next update is expected

Do not promise a resolution time that is not supported by the active SLA or owning team.

## 6. Functional escalation

Escalate when the issue requires different authority, tooling, ownership, or expertise.

Before reassignment:

- Confirm scope and priority.
- Complete safe first-line checks.
- Record evidence and results.
- State the specific reason for escalation.
- Name the requested action or decision.
- Confirm the correct group and remove stale individual assignment when the workflow requires group pickup.
- Tell the requester what changes and what does not.

## 7. Hierarchical or incident escalation

Escalate to leadership or incident management when impact, urgency, safety, security, compliance, communication, or SLA risk exceeds the normal queue process. Do not wait for an SLA breach when critical impact is already known.

## 8. Change, rollback, and verification

For every consequential change, document:

- Authority and approval
- Pre-change state
- Intended outcome
- Maintenance or user-impact window
- Exact change
- Rollback method
- Post-change test
- Final user validation

A technical signal such as ping, service state, or connected status is not enough when the original user workflow still fails.

## 9. Resolution and closure

Resolution notes should state:

- Confirmed cause, or the narrowest supported explanation
- Corrective action
- Validation performed
- User confirmation or documented validation substitute
- Monitoring or recurrence plan
- Linked problem, change, or follow-up record

Do not state a root cause when evidence supports only correlation or temporary recovery.

## Quality checklist

- One clear issue and owner
- Accurate scope and priority
- No secrets or unnecessary personal data
- Chronological evidence
- Changes separated from observations
- Escalation reason and requested action
- User updates recorded
- Original workflow validated
- Rollback and follow-up documented

## Authoritative references

- [Freshservice: Viewing and accessing ticket information](https://support.freshservice.com/support/solutions/articles/154815-viewing-and-accessing-information-about-tickets)
- [Freshservice: Priority Matrix](https://support.freshservice.com/support/solutions/articles/218550-priority-matrix)
- [Freshservice: Managing ticket escalations](https://support.freshservice.com/support/solutions/articles/156464-managing-ticket-escalations-in-freshservice)
