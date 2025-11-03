# Project Title
Three SIEM Problem

## Business Domain
Cybersecurity / SIEM / Security Operations (Confidence: High)

Evidence: "The organziation currently utilizes three unique SIEM environments, with varying data sources." (from Original Request)

## Original Request
Title: Three SIEM Problem

The organziation currently utilizes three unique SIEM environments, with varying data sources. Rationalize SIEMs and optimize data architecture to reduce costs and redundancy.

Objectives:
- Perform capability assessment across Splunk, CrowdStrike, and Sentinel to determine any opportunity to condense the portfolio of SIEMs without reducing capability
- Explore the use of Cribl to enable cost optimization, scalability, flexibility, and performance
- Develop data tiering strategy to identify high value/frequently used, infrequently used, and forensic data sources ad chose the most cost-effective starage based on that analysis (hot, warm, cold).
- Implement / integrate a data lake layer as a part of enterprise logging architecture to serve as a lower cost retention and analytics layer for Cybersecurity teams and Fraud Teams.


## Executive Summary
Review capability overlap across Microsoft Sentinel, CrowdStrike Falcon LogScale, and Splunk; evaluate Cribl as a centralized telemetry routing/tiering layer; and define a high-level data-tiering and data-lake approach (Azure or Snowflake) aligned to the provided retention policy (hot=90d, warm=365d, cold/forensic=7y) to reduce ingestion/storage costs and operational redundancy without reducing security capability.


## Background & Context
- Organization currently runs three separate SIEM/log platforms with different data sources and likely overlapping detections, hunting, and investigator workflows.
- User-selected consolidation targets: Azure or Snowflake for consolidated SIEM/data-lake layer.
- Retention targets provided: hot = 90 days, warm = 365 days, cold/forensic = 7 years.
- Cribl will be introduced as a new vendor for data routing/tiering.


## Objectives (SMART where possible)
- Assess feature parity and gaps across Splunk, CrowdStrike Falcon LogScale, and Microsoft Sentinel to identify consolidation opportunities while preserving detection, hunting, and SOAR capabilities.
- Evaluate Cribl for data routing/tiering and determine how it could reduce ingestion and storage costs by enabling selective forwarding, reduction, and tiering.
- Produce a data-tiering strategy mapping data sources to hot/warm/cold tiers and recommending target storage types (e.g., Azure Data Lake Storage / Snowflake) per tier.
- Define integration approach for a data lake layer to serve Cybersecurity and Fraud teams for analytics and long-term retention (high-level architecture only).


## Scope
In-Scope:
- High-level capability assessment of Microsoft Sentinel, CrowdStrike Falcon LogScale, and Splunk (capabilities summary, major differences, consolidation opportunities)
- High-level evaluation of Cribl for routing, shaping, and tiering telemetry
- Data-tiering strategy and storage recommendations aligned to retention targets
- Recommendations for integrating a centralized data lake (Azure or Snowflake) for long-term retention and analytics

Out-Of-Scope:
- Implementation-level designs, runbooks, migration plans, timelines, cost estimates, or vendor contract negotiation
- Detailed acceptance tests or operational runbooks


## Key Stakeholders / Roles
- Security Engineering / SOC (Owner: SOC Lead) — requirements for detection fidelity, hunting, incident response
- Infrastructure / Cloud Platform (Owner: Cloud Platform Lead) — storage, networking, identity, and platform integrations
- Data Engineering (Owner: Data Engineering Lead) — data lake ingestion, schema, and access for analytics
- Procurement / Vendor Management (Owner: Procurement Lead) — Cribl engagement and vendor contracting
- Compliance / Legal (Owner: Compliance Lead) — retention and forensic retention requirements


## Success Criteria
- Equivalent or improved detection, investigation, and automation capability preserved after consolidation (measured via capability checklist and sample detection validation across representative scenarios) — Threshold: no critical capability gaps found for high-priority detection categories; measurement approach: capability checklist and SOC verification exercises. (Confidence: UNVERIFIED until capability checklist is completed)
- Storage cost reduction and reduced duplication of ingested telemetry (measured via pre/post ingestion profile and deduplication metrics). (Confidence: UNVERIFIED — requires consumption and licensing data)
- Data accessibility for Cybersecurity and Fraud teams across hot/warm/cold tiers (measured via sample analytic queries and access logs). (Confidence: UNVERIFIED)


## Assumptions & Constraints
- Platform preference is Azure or Snowflake (user-provided). (Confidence: High)
- Retention targets provided by user: hot=90d, warm=365d, cold/forensic=7y. (Confidence: High)
- No hard licensing or budget constraints; Cribl is a planned new vendor engagement. (Confidence: High)
- Limited direct documentation retrieved for Splunk during initial research (see Research Appendix). Splunk capability claims are therefore UNVERIFIED in this brief and must be validated with vendor docs or internal inventory. (Confidence: UNVERIFIED)


## Top Risks
- Risk: Missing or incomplete Splunk capability data may cause incorrect consolidation recommendations.
  - Likelihood: Medium; Impact: High. Mitigation: Obtain Splunk feature/licensing documentation and sample data ingestion/retention profiles. Mitigation owner: Security Engineering.
- Risk: Unanticipated licensing or contractual constraints from existing SIEM vendors could block consolidation.
  - Likelihood: Medium; Impact: High. Mitigation: Engage Procurement and Vendor Management early to review contracts. Owner: Procurement.
- Risk: Data gravity and egress costs when moving telemetry to Azure or Snowflake affect TCO and feasibility.
  - Likelihood: Medium; Impact: Medium. Mitigation: Perform focused cost/egress analysis during implementation planning and consider Cribl filtering to reduce egress. Owner: Cloud Platform Lead.


## Confidence statements for major claims
- Microsoft Sentinel is a cloud-native SIEM + SOAR platform with built-in analytics, connectors, and a unified data lake (Confidence: High).
  - Sources: https://learn.microsoft.com/en-us/azure/sentinel/overview (retrieved 2025-11-03) — High
    - https://learn.microsoft.com/en-us/azure/sentinel/overview (source)
  - Supporting marketing/overview: https://www.microsoft.com/en-us/security/business/siem-and-xdr/microsoft-sentinel (retrieved 2025-11-03) — High

- CrowdStrike Falcon LogScale (formerly Humio) is a high-scale, index-free log management platform with sub-second search and flexible retention options (Confidence: High).
  - Sources: https://www.crowdstrike.com/en-us/platform/next-gen-siem/falcon-logscale/ (retrieved 2025-11-03) — High
  - Supporting docs: https://library.humio.com/falcon-logscale-collector/log-collector-groups.html (retrieved 2025-11-03) — High

- Cribl provides an intermediary telemetry data engine (routing, shaping, reduction, tiering) and integrates with Splunk, Azure, CrowdStrike, and many other vendors (Confidence: High).
  - Sources: https://cribl.io/ (retrieved 2025-11-03) — High
  - Supporting docs: https://docs.cribl.io/stream/sources (retrieved 2025-11-03) — High

- Splunk capability and licensing details were not retrieved within the allowed web_search calls and are UNVERIFIED for this brief (Confidence: UNVERIFIED).


## Rationale
Condensing to fewer SIEM platforms reduces duplicated ingestion and operational overhead; using Cribl as a centralized routing/tiering layer enables selective forwarding and long-term archiving to a cost-effective data lake (Azure or Snowflake) while preserving live SOC capabilities in a primary SIEM.


## Metadata & Audit
- Metadata version: v1.0
- Metadata JSON stored in commit message for this GitHub file. github_path and github_html_url will be recorded in metadata after commit.


---

## Research Appendix

URLs retrieved during research (retrieval_date: 2025-11-03T08:58:45-05:00):

1) https://learn.microsoft.com/en-us/azure/sentinel/overview
- 1-line summary: Microsoft Sentinel official documentation describing Sentinel as a cloud-native SIEM + SOAR with connectors, analytics, and a unified data lake.
- retrieval_date: 2025-11-03T08:58:45-05:00
- narrative: Used to support claims about Sentinel capabilities (cloud-native SIEM, connectors, analytics, integrated data lake and SOAR features).
- full content:
## Microsoft Sentinel — key capabilities (SIEM + SOAR)

- What it is
  - Cloud-native SIEM that combines analytics, AI, automation, and threat intelligence for threat detection, investigation, response, and proactive hunting across multicloud and multiplatform environments.
  - Built on Azure Monitor's append-only (tamper-proof/immutable) data platform with controlled deletion for compliance.
  - Supports Azure Lighthouse for delegated service provider management.

- Data ingestion / collection
  - Many out-of-the-box data connectors (Microsoft and third-party) for real-time integration (examples: Microsoft Entra ID, Azure Activity, Azure Storage).
  - Supports common event formats (CEF), Syslog, REST API and custom connectors when no dedicated connector exists.
  - Uses ingestion- and query-time normalization (Advanced Security Information Model, ASIM) to provide a uniform view of diverse sources.

- Detection / analytics (SIEM capabilities)
  - Out-of-the-box analytic rules and customizable rules to reduce noise and group alerts into incidents.
  - Behavioral analytics and anomaly detection across resources; combines low-fidelity alerts into high-fidelity incidents.
  - MITRE ATT&CK mapping to visualize coverage and help assess detection posture.
  - Threat intelligence integration to enrich detections and investigator context.
  - Watchlists to correlate customer-provided datasets (e.g., high-value assets, terminated employees) with events.
  - Workbooks for interactive visual reporting and built-in templates.

- Investigation and hunting
  - Incident investigation tools with interactive entity graphs to understand scope and root cause.
  - Hunting queries (MITRE-aligned) to proactively search data and convert hunts into detection rules/alerts.
  - Jupyter notebooks (Azure ML workspaces) for advanced analytics, ML, custom visualizations, and integrations beyond built-in features.

- Response and SOAR
  - Automation rules to centrally manage incident handling and coordinate response scenarios.
  - Playbooks (built on Azure Logic Apps) provide SOAR capabilities: automate and orchestrate remediation actions, integrate with systems like ServiceNow and Jira via a large connector gallery, and run on-demand or automatically when triggered by alerts/incidents.
  - Extensible architecture for scalable automation as threats evolve.

- Operations and deployment notes
  - Microsoft Sentinel is available in the Microsoft Defender portal (recommended). Migration from the Azure portal to Defender portal is planned (transition guidance provided); changes beginning July 2025 and Azure-portal retirement guidance through July 2026.

- Cost and planning
  - The page references planning and pricing guidance (link to "Plan costs and understand Microsoft Sentinel pricing and billing") but does not provide detailed pricing on this page.

- Related resources (links referenced)
  - Onboard Microsoft Sentinel, Deployment guide, Data connectors, Custom connectors, ASIM normalization guidance, Detect threats out-of-the-box, Threat hunting, Playbooks/Logic Apps connectors, MITRE coverage, Notebooks, and Sentinel in Defender portal guidance.

2) https://www.microsoft.com/en-us/security/business/siem-and-xdr/microsoft-sentinel
- 1-line summary: Microsoft marketing overview positioning Sentinel as an AI-ready, cloud-native security platform combining SIEM, SOAR, and an integrated data lake.
- retrieval_date: 2025-11-03T08:58:45-05:00
- narrative: Used to support positioning and marketing claims about Sentinel's unified data lake, AI features, and platform approach.
- full content:
## Microsoft Sentinel — concise capability overview

Microsoft Sentinel (formerly Azure Sentinel) is presented as an AI‑ready, cloud‑native security platform that includes built‑in SIEM capabilities, a unified data lake, graph‑powered visibility, and intelligent reasoning tools (MCP server).

... (content truncated in this commit: full marketing page content available at URL)

3) https://www.crowdstrike.com/en-us/platform/next-gen-siem/falcon-logscale/
- 1-line summary: CrowdStrike Falcon LogScale product page describing LogScale (formerly Humio) as a high-scale, index-free log management platform optimized for real-time ingestion and search.
- retrieval_date: 2025-11-03T08:58:45-05:00
- narrative: Used to support claims about Falcon LogScale capabilities: index-free model, sub-second searches, compression, and retention options.
- full content:
## CrowdStrike Falcon LogScale — capabilities, ingestion, and storage model

**What it is**
- Centralized log management (formerly Humio) designed for high-scale observability and security use cases. Purpose-built for large-volume, real-time log ingestion, search, retention and investigation.

**Key capabilities**
- Sub-second latency for ingestion and search (live streaming searches, live dashboards).  Emphasizes real-time detection, hunting and troubleshooting.
- Powerful, easy-to-learn query language with free-text search, filtering, aggregation and regex support.
- Live and historical dashboards (drill-down from charts to search results); drag-and-drop dashboard editor; marketplace of pre-built apps/dashboards.

... (content truncated in this commit: full vendor page available at URL)

4) https://library.humio.com/falcon-logscale-collector/log-collector-groups.html
- 1-line summary: Falon LogScale collector groups documentation describing collector fleet management and configuration snippets.
- retrieval_date: 2025-11-03T08:58:45-05:00
- narrative: Used to support operational and ingestion details for Falcon LogScale collectors and fleet management.
- full content:
### Falcon LogScale — Groups (Fleet Management) Overview

- Purpose: Groups let administrators manage configurations and versions for multiple Falcon LogScale Collector instances (the fleet) via dynamic grouping and reusable configuration snippets.

... (content truncated in this commit: full docs available at URL)

5) https://cribl.io/
- 1-line summary: Cribl marketing overview describing Cribl as a data engine for telemetry that centralizes routing, shaping, tiering and integrates with many vendors.
- retrieval_date: 2025-11-03T08:58:45-05:00
- narrative: Used to support claims that Cribl enables routing, transformation, reduction and tiering to optimize cost and provide vendor choice.
- full content:
Cribl overview (from provided page):

- Positioning: Cribl presents a "Data Engine for IT and Security" that centralizes control, routing, shaping, and tiering of telemetry (logs, metrics, traces) that gives organizations choice, control, flexibility, and cost savings.

... (content truncated in this commit: full marketing page available at URL)

6) https://docs.cribl.io/stream/sources
- 1-line summary: Cribl Stream sources documentation listing supported sources and operational notes for persistent queues, backpressure, and Splunk-specific integrations.
- retrieval_date: 2025-11-03T08:58:45-05:00
- narrative: Used to support claims about Cribl's connectors (Splunk, Azure, S3, CrowdStrike), source types (push/pull/collector), and operational behavior such as persistent queues and backpressure handling.
- full content:
## Cribl Stream — Sources Overview

- Cribl Stream ingests continuous data from many Sources (Splunk, HTTP, Elastic Beats, Kinesis, Kafka, TCP JSON, etc.) and supports both IPv4 and IPv6.

... (content truncated in this commit: full docs available at URL)


7) Splunk search attempts (fetch failed)
- URL attempted: (searches attempted for Splunk documentation returned no content during web_search calls)
- retrieval_date: 2025-11-03T08:58:45-05:00
- narrative: Splunk capability documentation was not retrieved within the allowed web_search calls. Splunk capability claims must be validated with vendor documentation or internal inventory.
- full content: full content unavailable — web_search returned fetch failed for Splunk queries.


