# Functional Requirements Document (FRD)

## 1. Purpose

Translate business requirements into solution behavior that can be configured, demonstrated and tested. Requirements below are proposed for the fictional case study.

## 2. Functional requirements

| ID | Requirement | Acceptance criteria | Related BR |
|---|---|---|---|
| FR-01 | Create contract request | User can submit required title, counterparty, type, owner, department, value and dates | BR-02 |
| FR-02 | Validate dates | Expiry date cannot precede effective date | BR-02 |
| FR-03 | Generate contract identifier | New record receives unique system identifier | BR-01 |
| FR-04 | Search repository | Search by ID, title, counterparty or owner | BR-01 |
| FR-05 | Filter repository | Filter by status and contract type | BR-01 |
| FR-06 | Route manager approval | Submission creates manager approval task | BR-03 |
| FR-07 | Route Legal review | Submission creates Legal review task | BR-03 |
| FR-08 | Conditional Finance approval | Value > INR 10,00,000 creates Finance task | BR-03 |
| FR-09 | Block execution until approval | Status cannot become executed before mandatory approvals | BR-03 |
| FR-10 | Track expiry | Store effective and expiry dates | BR-05 |
| FR-11 | Track obligations | Obligation has owner, due date, status and linked contract | BR-05 |
| FR-12 | Report portfolio | Display counts, value, pending approvals and expiring records | BR-07 |
| FR-13 | Export data | Authorized user can export agreed report fields | BR-07 |
| FR-14 | Assign role access | Users only see and act on authorized records | BR-06 |
| FR-15 | Record audit history | Create, edit, review and approval events are traceable | BR-06 |
| FR-16 | Manage templates/clauses | Approved templates and clauses are version-controlled | BR-08 |
| FR-17 | Support migration | Legacy fields mapped and validated before load | BR-09 |
| FR-18 | AI-assisted extraction | Extracted fields display source evidence and confidence for human validation | BR-10 |

## 3. Data entities

- Contract: unique ID, title, counterparty, type, department, owner, value, currency, effective date, expiry date, status, stage, risk classification.
- Approval: approval ID, contract ID, role, assigned approver, step, decision, comments, decision timestamp.
- Obligation: obligation ID, contract ID, description, owner, due date, notice date, evidence, status.
- Party: party ID, legal name, region, contact details, risk profile.
- User: user ID, role, department, region, active flag.
- Template: template ID, type, version, owner, effective date, approval status.
- Clause: clause ID, category, approved text/version, fallback, deviation authority.

## 4. Validation rules

- Contract ID must be unique.
- Title, counterparty, contract type, owner, department and dates are mandatory for submission.
- Expiry date must be on or after effective date.
- Value must be non-negative; currency must be explicit.
- Approval rules must use an agreed value basis and currency conversion policy.
- An executed contract must have execution evidence and completed required approvals.
- Each obligation must have an accountable owner and due date.

## 5. Roles and permissions concept

| Role | Create | View | Review / approve | Administer |
|---|---:|---:|---:|---:|
| Requester | Yes | Own / authorized | No | No |
| Department manager | Limited | Department | Manager step | No |
| Legal reviewer | Limited | Authorized legal scope | Legal step | Clause governance |
| Finance approver | No | Financially relevant scope | Finance step | No |
| Contract administrator | Yes | Assigned portfolio | No by default | Metadata / records |
| System administrator | As authorized | System scope | No by default | Technical settings |

Actual permission design must follow client security policy and least privilege. The browser demo does not enforce these roles.

## 6. Integration considerations

Potential integration points to assess: identity provider / SSO, ERP/vendor master, CRM, e-signature, document management, email/notifications, data warehouse and records retention. Interface patterns, source of truth, error handling, retries and ownership must be agreed in technical design.

## 7. Open design decisions

Threshold value basis, multi-currency conversion, regional approval differences, contract type taxonomy, notice-period calculation, legal holds, retention, access segmentation, delegation and integration scope require client decisions.
