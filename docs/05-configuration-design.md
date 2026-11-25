# Functional Configuration Design

This document describes conceptual configuration decisions for an enterprise CLM platform. It is not an Icertis configuration guide and does not claim that the settings below were deployed in Icertis.

## Contract type matrix

| Contract type | Typical owner | Required metadata | Review path |
|---|---|---|---|
| Vendor Agreement | Procurement | Vendor, spend, term, renewal, data access | Manager → Legal → Finance if threshold |
| Customer Agreement | Sales | Customer, region, value, service, liability | Manager → Legal → Finance if threshold |
| NDA | Legal / business owner | Parties, purpose, term, confidentiality scope | Manager → Legal |
| Employment Agreement | HR | Employee reference, jurisdiction, start/end | HR authority → Legal as policy requires |
| Statement of Work | Delivery / Procurement | Parent agreement, scope, fees, milestones | Manager → Legal → Finance if threshold |

## Metadata dictionary

| Field | Type | Mandatory | Validation / use |
|---|---|---:|---|
| Contract ID | Unique text | System | Unique identifier |
| Contract title | Text | Yes | 3–150 characters |
| Counterparty | Party reference | Yes | Match approved party record |
| Contract type | Controlled list | Yes | Approved taxonomy |
| Department | Controlled list | Yes | Approved organizational unit |
| Business owner | User reference | Yes | Active accountable owner |
| Contract value | Decimal | Yes | Non-negative |
| Currency | ISO currency code | Yes | Explicit; no assumed conversion |
| Effective date | Date | Yes | Valid date |
| Expiry date | Date | Yes | On/after effective date |
| Notice period | Integer + unit | Conditional | Based on actual clause |
| Notice date | Date | Conditional | Derived from notice period and contract terms |
| Status | Controlled list | System | Draft, Pending, In Review, Active, Expiring, Expired, Rejected |
| Confidentiality | Controlled list | Yes | Access policy input |
| Risk rating | Controlled list | Conditional | Based on approved review methodology |

## Approval matrix (illustrative)

| Condition | Required steps | Control |
|---|---|---|
| All new in-scope agreements | Department Manager → Legal | Mandatory sequence |
| Total committed value > INR 10,00,000 | Manager → Legal → Finance | Finance is additional mandatory step |
| NDA with no financial commitment | Manager → Legal | Legal policy validation |
| Non-standard liability / indemnity clause | Legal escalation | Designated legal authority |
| Restricted data / high-risk supplier | Security review | Risk-based additional review |

The demo implements only a simplified manager + legal sequence and adds finance above the threshold. It does not implement all matrix branches.

## Clause governance

Each standard clause should have: clause identifier, category, approved text, version, owner, effective date, fallback position, permitted deviation, approval authority and review date. Legal owns the approved clause library. Non-standard language must be captured and routed according to policy.

## Template governance

Templates should be mapped to contract type, jurisdiction, language and business unit. Each template needs an owner, version, effective date, approval state and retirement process. Users should not independently modify approved master templates.

## Environment and release controls

Maintain separate development, test/UAT and production environments in an actual implementation. Promote approved configuration through controlled release management, with versioning, test evidence, rollback planning and change approval.
