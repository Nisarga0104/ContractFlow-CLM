# Testing Strategy and UAT

## Test levels

- Functional testing: validate individual fields, screens and workflow rules.
- Integration testing: validate interfaces and error handling where integrations exist.
- Security testing: validate role access, confidentiality and audit behavior.
- Regression testing: confirm changes do not break existing flows.
- UAT: business users validate end-to-end scenarios against approved requirements.

## Entry criteria

Approved baseline requirements, test environment available, test data prepared, configuration version recorded, test users and roles provisioned, and known blockers documented.

## Exit criteria

All critical tests pass; no unresolved Severity 1 or 2 defects; lower-severity defects have accepted workarounds and owners; business process owners approve UAT; training and cutover readiness reviewed.

## UAT sign-off template

| Field | Value |
|---|---|
| Business process | Contract intake and approval |
| Test cycle | UAT |
| Environment | To be confirmed |
| Build / configuration version | To be recorded |
| Business owner | To be assigned |
| Result | Pending execution |
| Open critical defects | Must be zero for sign-off |
| Sign-off | Not yet obtained |

## Defect severity

- Sev 1 Critical: security breach, data loss, core process unavailable.
- Sev 2 High: major business function blocked, no acceptable workaround.
- Sev 3 Medium: function impaired, workaround available.
- Sev 4 Low: cosmetic or minor usability issue.

## Defect log template

Use `../tests/defect-log.csv`. Every defect should include reproducible steps, expected vs actual result, environment, evidence, severity, owner, fix version and retest result.

## Important distinction

The test cases supplied with this repository are designed scenarios. They have not been executed against a production CLM platform. Do not claim UAT completion or business sign-off unless you actually conduct and document it.
