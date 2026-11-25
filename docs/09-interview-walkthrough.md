# Interview Walkthrough — ContractFlow

## 60-second project explanation

"I designed ContractFlow as a self-directed CLM functional implementation simulation for a fictional multinational company. The client scenario involved contracts spread across spreadsheets and email, inconsistent approval routing and missed renewal visibility. I approached it as a Functional Consultant: I documented business requirements, mapped AS-IS and TO-BE processes, translated requirements into functional rules, designed metadata and conditional approvals, created a migration mapping, and prepared test cases, UAT and deployment plans. I also built a browser-based prototype to demonstrate contract intake, approval tasks, obligations and reporting. It is a simulation rather than an actual Icertis implementation, but it helped me understand the functional consulting lifecycle."

## Explain the approval rule

"The initial business rule is that all in-scope contracts go through manager and Legal review. Contracts whose total committed value exceeds INR 10 lakh additionally require Finance approval. I would validate whether the threshold is based on total contract value, annual value or another measure, and confirm currency conversion and regional delegation rules before configuration. I would then test values below, equal to and above the threshold."

## Explain requirements traceability

"I would link each business requirement to one or more functional requirements, configuration decisions, test cases and UAT evidence. That gives stakeholders traceability from the original business need through solution validation."

## Explain migration

"I would first inventory and profile the legacy sources, define the target data dictionary, map source fields, cleanse duplicates and invalid records, and run a sample migration. I would reconcile record counts and critical fields, route exceptions to owners and obtain business sign-off before cutover."

## Explain UAT

"UAT is business validation, not just technical testing. I would prepare realistic end-to-end scenarios, expected results and acceptance criteria, support business users during execution, log defects with severity and evidence, retest fixes and obtain formal sign-off."

## Explain AI

"I have treated AI as an assistive capability, not an autonomous legal decision-maker. A production design could extract metadata and surface unusual clauses, but every result needs source evidence, confidence, human validation, privacy controls and an approved legal playbook."

## Likely interviewer questions

1. How would you gather requirements from Legal, Procurement and Finance when their priorities conflict?
2. How do you distinguish a business requirement from a functional requirement?
3. What happens if a contract is rejected at Legal review?
4. How would you design approval routing for different contract values?
5. What data quality problems would you expect during migration?
6. How would you test an approval workflow?
7. What is the difference between SIT and UAT?
8. How would you handle a scope change after design sign-off?
9. How would you manage user resistance to a new CLM system?
10. What would you do if a user cannot access a confidential agreement?
11. What information should be captured for a contract renewal?
12. How can AI help contract operations without replacing legal judgment?

## Be accurate about your experience

Say "I designed a simulated CLM solution and prototype." Do not say "I configured Icertis," "I implemented this for a real client," or "I completed a production migration." A portfolio simulation demonstrates structured thinking, not product certification or professional implementation experience.
