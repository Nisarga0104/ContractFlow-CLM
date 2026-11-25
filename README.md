# ContractFlow — Enterprise CLM Functional Implementation Simulation

**Portfolio case study | Fictional client: Apex Global Technologies**

ContractFlow demonstrates how a Functional Consultant could approach a contract lifecycle management (CLM) implementation: discover business needs, translate them into functional requirements, design workflows and configuration, plan data migration, validate the solution through testing/UAT, and prepare deployment and handover.

> **Important:** ContractFlow is an independently created educational simulation. It is not Icertis software, is not connected to the Icertis platform, and does not demonstrate hands-on Icertis configuration. It is not legal advice. All client names, contract records, values, workflow rules and sample metrics are fictional.

## Live demo

Deploy this repository to Vercel using the steps in `docs/08-deployment-and-handover.md`. The app is static HTML/CSS/JavaScript and requires no build command.

## Features

- Executive dashboard and contract portfolio summary
- Searchable contract repository
- Create and submit a contract
- Simulated approval routing: manager + legal; finance added for values above INR 10,00,000
- Approval decision simulation
- Obligation and renewal tracking
- Contract intelligence review queue with transparent demo limitations
- Portfolio reports and CSV export
- Browser-local persistence using `localStorage`

## Run locally

Open `index.html` in a browser, or serve the folder with VS Code Live Server. No backend, API key, package installation or database is required.

## Repository map

- `index.html`, `styles.css`, `app.js`: deployable demo application
- `docs/`: consulting implementation artifacts
- `data/`: fictional sample records and migration template
- `tests/`: test scenarios and acceptance criteria
- `assets/`: reserved for process diagrams/screenshots added by the author

## Demo workflow

1. Open Overview and inspect the sample portfolio.
2. Open Contracts and create a contract.
3. Enter a contract value above INR 10,00,000.
4. Open Approvals and observe the simulated approval tasks.
5. Approve or reject tasks to see status changes.
6. Open Obligations & renewals and complete an obligation.
7. Open Reports and export the contracts CSV.

## Known limitations

This is a front-end portfolio simulation, not a production CLM application.

- Data is stored in the current browser's local storage; it is not shared across users or devices.
- No authentication, authorization enforcement, backend API, database, audit-grade event log, encryption-at-rest, document repository or e-signature integration is implemented.
- Approval actions are simulated in the browser and are not legally binding.
- The intelligence module is rule-/metadata-based demonstration content, not an AI model or contract parser.
- Sample dates and figures are illustrative.
- Production implementation would require security architecture, privacy/legal review, identity integration, backend services, database controls, audit logging, monitoring, backups, disaster recovery and client-specific configuration.

## Consulting artifacts

Start with `docs/00-project-charter.md`, then read the BRD, stakeholder matrix, process design, FRD, configuration workbook (CSV), migration mapping, test scenarios, UAT and deployment plan. See `docs/09-interview-walkthrough.md` for a suggested interview narrative.

## Suggested portfolio description

**ContractFlow — Enterprise CLM Functional Implementation Simulation:** Designed an end-to-end CLM implementation case study for a fictional multinational enterprise. Produced business and functional requirements, stakeholder analysis, AS-IS/TO-BE process design, approval workflow specifications, configuration and data-mapping matrices, test scenarios, UAT and deployment documentation. Built a browser-based prototype demonstrating contract intake, approval routing, obligation tracking and portfolio reporting.

Be transparent that this was a self-directed simulation and distinguish the prototype from actual Icertis product configuration.
