# Data Migration Strategy

## 1. Objective

Migrate approved legacy contract records from spreadsheets and shared folders into a governed repository while preserving record integrity, ownership, status and traceability.

## 2. Migration approach

1. Identify source systems, file owners and authoritative records.
2. Inventory files and document formats.
3. Profile data for completeness, duplicates, invalid dates, inconsistent categories and missing owners.
4. Agree target metadata and mapping.
5. Cleanse and enrich data with business owners.
6. Define migration inclusion/exclusion and archival rules.
7. Load a representative sample into a non-production environment.
8. Reconcile source and target counts, key fields and document links.
9. Obtain business owner sign-off.
10. Execute cutover migration with exception handling and rollback plan.

## 3. Example field mapping

| Source field | Target field | Transformation | Validation |
|---|---|---|---|
| Legacy Ref | Contract ID | Generate target ID; retain legacy ref separately | Uniqueness |
| Agreement Name | Contract title | Trim whitespace | Mandatory |
| Supplier / Customer | Counterparty | Match party master | Unmatched records quarantined |
| Agreement Category | Contract type | Map to controlled taxonomy | Approved value |
| Cost Centre | Department | Map to org structure | Valid department |
| Contract Manager | Business owner | Map to active user | Owner confirmed |
| Total Amount | Contract value | Parse numeric; retain source currency | Non-negative |
| Start Date | Effective date | Normalize to ISO date | Valid date |
| End Date | Expiry date | Normalize to ISO date | Not before start |
| Renewal Notice | Notice period | Normalize number + unit | Confirm against contract text |
| File Path | Document reference | Resolve and attach through approved process | File opens and checksum/metadata reconciles |

## 4. Data quality rules

- No duplicate target identifiers.
- Counterparty must map to an approved party record or exception queue.
- Dates must parse and be logically consistent.
- Currency must not be inferred from geography.
- Missing owner requires business remediation.
- Status must map to an approved target status.
- Executed document must be present or explicitly classified as missing.
- Notice date must not be guessed; verify source clause.

## 5. Reconciliation

Reconcile record counts by source, contract type, region and status. Compare critical fields and document counts. Record rejected rows, reasons, remediation owner and retest result. Business owner signs off before cutover.

## 6. Cutover and rollback

Agree freeze window, final extract, delta handling, load sequence, validation, business sign-off and communication. Retain protected source backup. Define rollback trigger and accountable decision-maker before migration.

## 7. Security and privacy

Use least-privilege access, approved transfer channels, encryption, retention controls and secure deletion of temporary extracts. Do not use real confidential contract data in this public portfolio.
