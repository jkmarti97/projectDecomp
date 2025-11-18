# Portfolio Epic: Unified Cybersecurity Detection Modernization
Epic ID: <<REQUIRED: Epic ID>>  
Epic Owner: <<REQUIRED: Epic Owner>>  
Lean Business Owner: <<REQUIRED: Lean Business Owner>>  
Epic Sponsor: <<REQUIRED: Epic Sponsor>>  
Date Prepared: <<REQUIRED: Date Prepared>>

## 1. Epic Vision
This epic will unify and modernize detection engineering across all enterprise security platforms by establishing centralized ownership, standardized documentation, automated enrichment, and improved operational visibility. The outcome will be a consistent, data-driven detection capability that strengthens the organization’s ability to identify threats quickly, attribute activity, and prevent attacker lateral movement. The vision aligns with enterprise value streams that depend on reliable threat detection, rapid triage, and high-fidelity intelligence.

## 2. Problem Statement
- Detection ownership is fragmented across teams and tools, leading to inconsistent tuning and duplicate efforts.  
  Current impact: Delays in triage and increased alert noise.
- Telemetry and alerting sources lack a unified inventory, reducing ability to rationalize tooling or identify visibility gaps.  
  Current impact: Overlapping spend and blind spots in key attack surfaces.
- Benign positives require excessive manual review.  
  Current impact: SOC analysts spend an estimated high percentage of time triaging non-malicious alerts.
- TIP integration with security tooling is inconsistent or manual.  
  Current impact: Threat intel is not fully utilized, slowing attribution and campaign detection.
- Splunk documentation does not reliably capture use cases, data sources, and integration points.  
  Current impact: Engineering teams face rework and onboarding inefficiencies.
- Splunk’s index structure is overly complex and inconsistent.  
  Current impact: Inefficient searches and longer MTTR for investigations.
- SOC alert TTPs are not automatically reported for threat intel review.  
  Current impact: Reduced ability to identify emerging campaigns and correlate multi-source activity.

## 3. Proposed Solution (high-level)
Implement an enterprise-wide detection governance and automation framework that centralizes ownership, inventories all telemetry and alerting sources, integrates TIP enrichment, simplifies SIEM index structures, and automates TTP reporting. The solution includes four major feature areas:

### Feature: Centralized Detection Ownership Model
- Description: Establish a unified governance model defining roles, responsibilities, and approval workflows for ALL detection platforms.  
- Primary Owner: Cybersecurity Detection Engineering  
- Success Criteria: RACI published and adopted; ownership field populated for 100 percent of detections.  
- Dependencies: SOC, Threat Intel, SIEM Administrators.

### Feature: Enterprise Telemetry & Tooling Inventory
- Description: Create a consolidated inventory of all alerting, logging, and detection tools.  
- Primary Owner: Detection Engineering  
- Success Criteria: Inventory published; visibility gaps identified; quarterly update cycle established.  
- Dependencies: Platform teams, Network Engineering, SOAR team.

### Feature: Automation for Benign Positive Identification & TIP Integration
- Description: Build automations that enrich detections with TIP data and suppress confirmed benign positives.  
- Primary Owner: Detection Engineering Automation Team  
- Success Criteria: Reduction in benign positives; automated enrichment applied to priority data sources.  
- Dependencies: SOAR, TIP vendor APIs, SOC feedback.

### Feature: Splunk Documentation and Index Structure Modernization
- Description: Standardize Splunk detection documentation and simplify index taxonomy.  
- Primary Owner: Splunk Engineering  
- Success Criteria: Documentation for all detections complete; index footprint reduced and aligned to best practices.  
- Dependencies: Data Owners, Splunk Admins.

### Feature: Automated SOC Alert TTP Reporting
- Description: Automate daily/weekly reporting of SOC alert TTPs for threat intelligence analysis.  
- Primary Owner: Threat Intel Team (in partnership with Detection Engineering)  
- Success Criteria: Automated report delivered; campaign correlation achieved.  
- Dependencies: SIEM APIs, TIP, SOC operations.

### Minimum Viable Product (MVP)
- Centralized detection ownership established with RACI.  
- Initial telemetry and tooling inventory published.  
- TIP enrichment automation implemented for at least one high-value dataset.  
- Baseline Splunk documentation template published and adopted.  
- Automated TTP reporting prototype operational.

## 4. Lean Business Case
| Element | Details |
|---|---|
| Benefit Hypothesis | If detection ownership is centralized and key automations are implemented, the organization will reduce alert noise, shorten time to detection, and improve attribution accuracy. |
| Leading Indicators | Adoption of ownership model; reduction in benign positives; percentage of detections documented; TIP enrichment rate; number of telemetry sources cataloged. |
| Expected Outcomes | 20 percent reduction in benign positives; 30 percent improvement in attribution cycle time; complete visibility inventory; simplified index structure improving search performance by an estimated measurable margin. |
| Non-Financial Benefits | Improved SOC analyst experience; better cross-team collaboration; improved onboarding; stronger threat-informed defense. |
| Cost Estimates | 20–30 team-weeks across Detection Engineering, Splunk Engineering, and Threat Intel; infrastructure for automation; possible small licensing increases for TIP API capacity. |
| ROI & Payback | <<REQUIRED: ROI inputs needed>> |
| Minimum Viable Product (MVP) | - Ownership RACI documented and approved (Acceptance: validated by SOC and LBO).<br>- First version of telemetry inventory published (Acceptance: reviewed by platform owners).<br>- TIP enrichment MVP pipeline functional (Acceptance: validated with at least two real alerts).<br>- Splunk documentation template finalized and used for at least five detections.<br>- TTP reporting prototype running on scheduled automation. |

## 5. Success Metrics
- MTTD reduction: 20 percent within 6 months of MVP; measured via SIEM/RCA data; Owner: Detection Engineering.  
- Benign positive reduction: 15 percent within 2 PIs; measured via SOC ticketing metrics; Owner: SOC Lead.  
- Detections documented: 100 percent of active detections within 1 PI; measured via documentation repository; Owner: Splunk Engineering.  
- TIP enrichment adoption: 60 percent of high-priority data sources enriched within 6 months; measured via automation logs; Owner: Threat Intel Lead.  
- Inventory completeness: 95 percent of tools/log sources cataloged by end of PI 2; measured via inventory audits; Owner: Detection Engineering.

## 6. Risk & Mitigation Plan
| Risk | Impact | Mitigation Strategy |
|---|---:|---|
| Lack of cross-team alignment | High | Establish governance council and monthly review cadence. |
| Incomplete visibility inventory | Medium | Require platform team participation via PI objectives. |
| TIP API limits restrict automation | Medium | Evaluate vendor licensing and implement rate controls. |
| SOC resistance to ownership changes | High | Engage SOC early and incorporate feedback loops. |
| Automation errors suppress valid alerts | High | A/B testing, human-in-the-loop validation during rollout. |
| Index restructuring disrupts searches | Medium | Phased migration with aliasing and versioned dashboards. |

## 7. Decomposition Guidance
### Feature 1: Centralized Detection Ownership Model
- Acceptance Criteria: RACI approved; ownership assigned for all detections.  
- Size: Medium (3–5 team-weeks).  
- Story Guidance: Define roles, build catalog integration, align workflows with SOC.

### Feature 2: Telemetry & Tooling Inventory
- Acceptance Criteria: Completed inventory; documented visibility gaps.  
- Size: Medium.  
- Story Guidance: Collect platform data, normalize taxonomy, create dashboard representation.

### Feature 3: Automation for TIP Enrichment and Benign Positive Suppression
- Acceptance Criteria: MVP automation functioning; enrichment logs available.  
- Size: Large (6–8 team-weeks).  
- Story Guidance: Integrate APIs, define enrichment schema, develop suppression logic, SOC validation.

### Feature 4: Splunk Documentation & Index Modernization
- Acceptance Criteria: Template adopted; index simplification plan published.  
- Size: Large.  
- Story Guidance: Build documentation model, map current indexes, align with best practices.

### Feature 5: TTP Reporting Automation
- Acceptance Criteria: Automated reports delivered; threat intel uses them for attribution.  
- Size: Medium.  
- Story Guidance: Build export pipeline, normalize alert metadata, map TTPs.

### PI Planning Inputs
- Call out dependencies on SOC, Threat Intel, SIEM admins, SOAR.  
- Ensure objectives include documentation adoption, inventory completion, and MVP automation.  
- Risks: Cross-team alignment, automation accuracy, migration of Splunk indexes.

## 8. Dependencies & Assumptions
### Dependencies
- SOC workflows and approval processes  
- SIEM platforms: Splunk, Sentinel, StealthWatch, CrowdStrike  
- SOAR/TIP integrations  
- Platform and network teams for telemetry sources

### Assumptions
- TIP vendor API stable and available  
- SOC analysts available for validation  
- Funding approved for automation infrastructure  
- Access to all SIEM and alerting tool repositories

## 9. Implementation Roadmap (High-level)
- PI 1: Ownership RACI; telemetry inventory baseline; initial Splunk documentation template  
- PI 2: TIP enrichment MVP; first automation for benign positives; TTP reporting prototype  
- PI 3: Index restructuring; expanded automations; documentation fully adopted  
- Capacity: <<REQUIRED: capacity info needed>>

## 10. Acceptance Criteria & Sign-off
### Epic-Level Acceptance Criteria
- Ownership model implemented and adopted  
- Complete telemetry and tooling inventory  
- TIP enrichment MVP running and validated  
- Splunk documentation template in full use  
- TTP reporting automation operational  
- SOC sign-off on alert quality improvements

### Sign-off Stakeholders
- <<REQUIRED: Epic Owner>>  
- <<REQUIRED: Lean Business Owner>>  
- <<REQUIRED: Epic Sponsor>>  
- SOC Leadership  
- Threat Intelligence Lead  
- Splunk Engineering Lead

## 11. Appendix (optional)
- Example documentation template  
- Example telemetry inventory layout  
- TTP reporting schema  
- API integration examples

## 12. References
- Scaled Agile, Inc. (2023). SAFe 6.0 Overview. Retrieved from https://scaledagileframework.com/  
- Splunk Inc. (2024). Splunk Enterprise Documentation. Retrieved from https://docs.splunk.com/  
- Microsoft. (2024). Microsoft Sentinel Documentation. Retrieved from https://learn.microsoft.com/azure/sentinel/  
- CrowdStrike. (2024). Falcon Platform Documentation. Retrieved from https://www.crowdstrike.com/resources/  
- Mandiant. (2024). Threat Intelligence Best Practices. Retrieved from https://www.mandiant.com/resources
