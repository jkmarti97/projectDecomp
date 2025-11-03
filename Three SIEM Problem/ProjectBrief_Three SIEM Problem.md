# Project Title
Three SIEM Problem

## Business Domain
Cybersecurity / SIEM / Security Operations

### Original Request
The organziation currently utilizes three unique SIEM environments, with varying data sources. Rationalize SIEMs and optimize data architecture to reduce costs and redundancy.
Objectives:
- Perform capability assessment across Splunk, CrowdStrike, and Sentinel to determine any opportunity to condense the portfolio of SIEMs without reducing capability
- Explore the use of Cribl to enable cost optimization, scalability, flexibility, and performance
- Develop data tiering strategy to identify high value/frequently used, infrequently used, and forensic data sources ad chose the most cost-effective starage based on that analysis (hot, warm, cold).
- Implement / integrate a data lake layer as a part of enterprise logging architecture to serve as a lower cost retention and analytics layer for Cybersecurity teams and Fraud Teams.

## Executive Summary
The organization will consolidate to Splunk as the primary SIEM with Microsoft Sentinel and CrowdStrike (Falcon / LogScale) operating as sub-SIEMs for specialized telemetry and detection. The program will deliver capability assessments, a Cribl-based telemetry routing and tiering implementation, a data-tiering policy (hot=90d, warm=365d, cold/forensic=7y), and a data-lake ingestion and retention layer (Azure or Snowflake per user preference). The outcome reduces duplicated ingestion and storage costs, preserves detection capability, and delivers SOC enablement through updated runbooks, playbooks, and training.

## Background & Context
- The organization operates three separate SIEM products with overlapping telemetry sources and variable retention policies.
- Primary consolidation target: Splunk (per user direction). Sentinel and CrowdStrike remain for selected detections and specialized telemetry.
- User platform preference for long-term analytics: Azure or Snowflake; retention targets: hot=90 days, warm=365 days, cold/forensic=7 years.
- Cribl is a planned new vendor engagement to provide routing, shaping and tiering of telemetry before ingestion.

## Objectives (SMART where possible)
- Assess capabilities of Splunk, CrowdStrike Falcon/LogScale, and Microsoft Sentinel to identify any redundant capability and confirm Splunk can host SOC primary workflows (Specific, Measurable via capability checklist).
- Design a Cribl Stream-based routing and tiering configuration to reduce SIEM ingestion volume while preserving investigative fidelity (Measurable via percent reduction in ingested bytes; target to be defined during implementation).
- Define and formalize a data-tiering policy aligned to hot=90d, warm=365d, cold=7y and map data sources to tiers.
- Implement a data-lake ingestion pipeline (Azure Data Lake Storage Gen2 or Snowflake) for warm/cold retention and analytics accessible to Cybersecurity and Fraud teams.
- Deliver SOC enablement: updated runbooks, detection mappings, playbooks, training, and formal handover documentation.

## Scope
In-Scope
- Capability assessment and gap analysis for Splunk, CrowdStrike, and Microsoft Sentinel.
- Design and implementation of Cribl Stream configurations for routing, shaping, and tiering.
- Updates to Splunk ingestion pipelines, indexes, and data models to reflect reduced ingestion and tiering policies.
- Integration patterns between Splunk (primary), Sentinel, CrowdStrike, Cribl, and the chosen data-lake (Azure or Snowflake).
- Data-lake ingestion and lifecycle enforcement for warm and cold tiers.
- Validation/testing (ingest validation, search fidelity checks, SOC playbook validation), training, and handover.

Out-Of-Scope
- Low-level implementation code, detailed runbooks with step-by-step commands, scripts, specific timelines, or cost estimates.
- Replacement of Splunk as the primary SIEM.
- Any hardware procurement details beyond recommended platform choices.

## Key Stakeholders / Roles
- Project Sponsor: (TBD by organization) — owner: Executive Sponsor
- Project Manager: (TBD) — owner: PM
- Security Operations (SOC) Lead — owner: SOC Lead (responsible for validating SOC workflows)
- Splunk Platform Owner / Admin — owner: Splunk Admin (responsible for Splunk ingestion and data model changes)
- Cloud/Data Platform Owner (Azure / Snowflake) — owner: Cloud Platform Lead (data lake ingestion and lifecycle)
- Cribl Implementation Lead — owner: Cribl SME / Integrator
- CrowdStrike / Sentinel Integration Owner — owner: Threat Detection Lead
- Fraud Team Representative — owner: Fraud Team Lead (consumer of data-lake analytics)

## Success Criteria (metric + threshold + measurement approach)
- Retention compliance: All data mapped to tiers meet retention targets (hot=90d, warm=365d, cold=7y). Measurement: spot-check metadata and lifecycle policies in Splunk and data-lake.
- Ingest volume reduction to Splunk primary indexes: measurable reduction in bytes ingested to Splunk (baseline vs post-routing). Measurement approach: Splunk ingestion metrics and Cribl egress stats.
- Detection parity: Critical detection coverage maintained or improved (measured by capability checklist and SOC validation exercises). Measurement: detection test cases and incident drill results.
- Data accessibility: Fraud and Cybersecurity teams can query warm/cold datasets in the data-lake (validated by test queries and sample analytics jobs).
- Handover completeness: SOC runbooks, playbooks, training materials, and sign-off documented and accepted by SOC Lead.

## Assumptions & Constraints
- Assumption: Splunk will serve as primary SIEM and host SOC live workflows.
- Assumption: Data-lake will be implemented on Azure Data Lake Storage Gen2 or Snowflake per final selection.
- Constraint: No hard licensing or budget constraints specified; Cribl is a new vendor engagement.
- UNVERIFIED: Specific Splunk deployment type (Splunk Cloud vs Splunk Enterprise on-prem/hybrid) — affects some integration patterns and must be confirmed.

## Top Risks (likelihood, impact, mitigation, mitigation owner)
- Risk: Integration complexity if Splunk deployment type is on-prem and data-lake is cloud (Likelihood: Medium; Impact: High). Mitigation: Confirm deployment types early; use secure connectors and tokenized transfer; owner: Cloud Platform Lead.
- Risk: Loss of investigative fidelity from aggressive data shaping (Likelihood: Medium; Impact: High). Mitigation: Preserve raw or sufficiently detailed forensic data to cold tier; implement validation test cases; owner: Cribl Implementation Lead & SOC Lead.
- Risk: Stakeholder resistance to changing SOC workflows (Likelihood: Medium; Impact: Medium). Mitigation: SOC engagement, training, and phased cutover; owner: SOC Lead.

## Confidence statements for major claims (label + supporting URLs)
- Microsoft Sentinel provides cloud-native SIEM + SOAR and a unified security data lake (High). Sources: https://learn.microsoft.com/en-us/azure/sentinel/overview (Microsoft docs) and https://www.microsoft.com/en-us/security/business/siem-and-xdr/microsoft-sentinel (Microsoft product overview).
- Cribl provides telemetry routing, shaping, and tiering that integrates with Splunk, cloud object storage, and other SIEMs (High). Sources: https://cribl.io/ and https://docs.cribl.io/stream/sources.
- CrowdStrike Falcon LogScale (Humio) is a high-scale log management platform optimized for real-time ingestion and search (Medium). Source: https://www.crowdstrike.com/en-us/platform/next-gen-siem/falcon-logscale/.
- Splunk capability and recommended integration/ingestion adjustments are currently UNVERIFIED in this brief because credible vendor documentation was not retrieved within the current research set. This must be confirmed; recommended source: Splunk documentation (https://www.splunk.com) — UNVERIFIED.

## Rationale
Splunk is selected as primary to preserve existing SOC workflows and leverage existing detection investments while using Cribl and a data-lake (Azure or Snowflake) to offload warm/cold retention and reduce primary SIEM ingestion costs.

## Metadata & Audit
- GitHub path: Three SIEM Problem/ProjectBrief_Three SIEM Problem.md
- Version: v1.1
- Metadata object stored as commit message in GitHub (see repository commit history).

## Research Appendix
- https://learn.microsoft.com/en-us/azure/sentinel/overview
  - 1-line summary: Official Microsoft documentation describing Sentinel as a cloud-native SIEM + SOAR and its data ingestion/analytics capabilities.
  - retrieval_date: 2025-11-03T08:58:45-05:00
  - narrative: Supports claims about Sentinel capabilities and unified data-lake positioning used to justify Sentinel's role as a sub-SIEM and for integration considerations.
  - full content: Microsoft Sentinel — key capabilities (SIEM + SOAR) (full content saved where available).

- https://www.microsoft.com/en-us/security/business/siem-and-xdr/microsoft-sentinel
  - 1-line summary: Microsoft marketing overview positioning Sentinel as cloud-native SIEM + SOAR and data-lake.
  - retrieval_date: 2025-11-03T08:58:45-05:00
  - narrative: Supplemental capability description for Sentinel and data-lake integration.
  - full content: Microsoft Sentinel — concise capability overview (full content saved where available).

- https://www.crowdstrike.com/en-us/platform/next-gen-siem/falcon-logscale/
  - 1-line summary: CrowdStrike Falcon LogScale product page describing high-scale, index-free log management.
  - retrieval_date: 2025-11-03T08:58:45-05:00
  - narrative: Supports capability claims about CrowdStrike's log management strengths and real-time search characteristics.
  - full content: CrowdStrike Falcon LogScale — capabilities, ingestion, and storage model (full content saved where available).

- https://cribl.io/
  - 1-line summary: Cribl marketing overview describing Cribl as a telemetry data engine for routing, shaping, and tiering.
  - retrieval_date: 2025-11-03T08:58:45-05:00
  - narrative: Used to justify Cribl's role in cost optimization, routing, and pre-ingest shaping.
  - full content: Cribl overview (marketing) (full content saved where available).

- https://docs.cribl.io/stream/sources
  - 1-line summary: Cribl Stream sources documentation describing supported sources and operational notes.
  - retrieval_date: 2025-11-03T08:58:45-05:00
  - narrative: Supports claims about Cribl's integration patterns and supported sources (Splunk, syslog, Kafka, etc.).
  - full content: Cribl Stream — Sources Overview (full content saved where available).

- UNVERIFIED: Splunk documentation and precise integration guidance (no Splunk vendor URL retrieved in current research set). Recommended source to confirm: https://www.splunk.com

