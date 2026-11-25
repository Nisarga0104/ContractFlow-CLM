# Process Design — AS-IS and TO-BE

## AS-IS: fragmented contract process

```mermaid
flowchart TD
 A[Business user emails request] --> B[Legal / Procurement searches shared drive]
 B --> C[Template selected manually]
 C --> D[Draft exchanged by email]
 D --> E[Approvals requested manually]
 E --> F{All approvals received?}
 F -- No --> D
 F -- Yes --> G[Document signed]
 G --> H[Saved to team folder]
 H --> I[Expiry tracked in spreadsheet]
 I --> J[Manual management reporting]
```

## TO-BE: governed CLM process

```mermaid
flowchart TD
 A[Requester submits intake] --> B[Validate required metadata]
 B --> C{Request complete?}
 C -- No --> B
 C -- Yes --> D[Classify contract type and risk]
 D --> E[Create / select approved template]
 E --> F[Business Manager review]
 F --> G[Legal review]
 G --> H{Value above INR 10 lakh?}
 H -- Yes --> I[Finance approval]
 H -- No --> J[Approval complete]
 I --> J
 J --> K[Authorized execution]
 K --> L[Store executed contract and metadata]
 L --> M[Assign obligations and renewal owner]
 M --> N[Monitor alerts and report]
```

## Workflow definition

| Step | Actor | Input | Action | Output / control |
|---|---|---|---|---|
| Intake | Requester | Business need, counterparty, type, value, dates | Submit request | Request ID; mandatory fields |
| Completeness | System / coordinator | Submitted fields | Validate required metadata | Complete / returned |
| Manager review | Department manager | Request and business rationale | Approve / reject / return | Decision and comment |
| Legal review | Legal reviewer | Draft, template, deviations | Review clauses and terms | Legal approval / redline |
| Finance review | Finance approver | Value and financial terms | Validate commitment | Finance decision when threshold applies |
| Execution | Authorized signatories | Final approved version | Execute through approved process | Execution evidence |
| Repository | Contract administrator | Executed agreement | Store record and metadata | Searchable record |
| Obligation management | Contract owner | Contract terms | Assign obligations and dates | Owner and reminders |
| Renewal | Business owner / Legal | Notice terms and business need | Renew, renegotiate or terminate | Recorded decision |

## Exception paths

- Rejected request: return to requester with reason; retain history.
- Legal deviation: escalate to designated legal authority.
- Threshold exception: never bypass without documented authorized exception.
- Incomplete migration record: quarantine for remediation; do not silently import.
- Renewal owner missing: escalate before migration/go-live.
- Expired agreement: preserve historical record; do not treat as active.

## Process controls

- Segregation of duties for requester, approver and administrator where required.
- Approval delegation rules documented and time-bound.
- Immutable audit events in production.
- Version control for drafts and executed documents.
- Role-based access and confidential contract restrictions.
