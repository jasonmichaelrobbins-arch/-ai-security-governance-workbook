[AI_Security_Governance_README.md](https://github.com/user-attachments/files/24049635/AI_Security_Governance_README.md)
# Enterprise AI Security Governance Framework

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

A complete, operational framework for managing AI tools in your organization—from intake and risk classification through ongoing governance, compliance mapping, and program metrics.

---

## Why This Exists

Security teams are getting buried in AI tool requests with no consistent way to evaluate them. Questions pile up:

- How do we classify risk for a new AI tool?
- What guardrails are required before we approve it?
- Which security products cover which AI risks?
- How do we track exceptions for high-risk tools?
- What does "good" look like for an AI security program?

This framework answers all of that with an opinionated, ready-to-use workbook. It's not theoretical—it's built to be dropped into your environment and used on day one.

**This is a living document.** AI security practices are evolving rapidly. Contributions welcome.

---

## Table of Contents

- [What's Included](#whats-included)
- [Quick Start](#quick-start)
- [Framework Components](#framework-components)
  - [Tool Registry](#tool-registry)
  - [Intake Form](#intake-form)
  - [Guardrail Checklist](#guardrail-checklist)
  - [Exception Tracker](#exception-tracker)
  - [Governance Guide](#governance-guide)
  - [Tool Function Mapping](#tool-function-mapping)
  - [AI Security Tool Landscape](#ai-security-tool-landscape)
  - [Compliance Mapping](#compliance-mapping)
  - [Program Metrics](#program-metrics)
- [Risk Classification Model](#risk-classification-model)
- [Product Families](#product-families)
- [Compliance Frameworks](#compliance-frameworks)
- [Customization](#customization)
- [Contributing](#contributing)
- [License](#license)
- [Author](#author)

---

## What's Included

| Component | Purpose |
|-----------|---------|
| **Tool Registry** | Living inventory of approved AI tools with risk levels, owners, and review status |
| **Intake Form** | Two-part request form (requestor + security) for new tool evaluations |
| **Guardrail Checklist** | Verification checklist by product family with evidence requirements |
| **Exception Tracker** | Track and manage exceptions for Severe-risk tools and guardrail deviations |
| **Governance Guide** | Committee structure, lifecycle workflow, approval process, enforcement |
| **Tool Function Mapping** | 45 functions mapped to risk levels, guardrails, and security products (includes agentic AI) |
| **AI Security Tool Landscape** | 74 vendors mapped to 7 product families |
| **Compliance Mapping** | 46 guardrails mapped to 10 compliance frameworks |
| **Program Metrics** | KPIs, SLOs, and measurement framework for program effectiveness |

---

## Quick Start

1. **Download the workbook** (`.xlsx`)
2. **Start with the User Guide tab** — detailed instructions and common scenarios
3. **When a new tool request comes in:**
   - Have requestor complete Intake Form Part 1
   - Security completes Part 2 (risk classification)
   - Use Tool Function Mapping to identify required guardrails
   - Verify guardrails with the Guardrail Checklist
   - Add approved tool to Tool Registry
4. **For Severe-risk tools:** Use Exception Tracker and Governance Guide Section 4
5. **For security product selection:** Use AI Security Tool Landscape

---

## Framework Components

### Tool Registry

Living inventory of all AI tools in your environment.

| Field | Purpose |
|-------|---------|
| Tool Name / Vendor | What it is |
| Risk Level | Low / Medium / High / Severe |
| Data Classification | Public / Internal / Confidential / PII-Regulated |
| Functions | What capabilities does this tool have? |
| Required Families | Which security product families are required? |
| Guardrails | What controls are in place? |
| Business / Technical Owner | Who's accountable? |
| Approval Date / Last Review / Next Review | Lifecycle tracking |
| Status | Active / Under Review / Suspended / Decommissioned |
| Exception # | Link to Exception Tracker if applicable |

**Review cadence by risk:**

| Risk Level | Approval Required | Review Frequency |
|------------|-------------------|------------------|
| Low | Standard | Annual |
| Medium | Department lead | Semi-annual |
| High | Committee | Quarterly |
| Severe | Exception | Monthly |

---

### Intake Form

Two-part request form for new AI tools.

**Part 1 — Requestor Completes:**
- Contact information
- Tool name, vendor, website
- Use case and business justification
- Data types accessed
- Integrations required

**Part 2 — Security Completes:**
- Risk factor assessment (6 criteria)
- Overall risk classification
- Required product families
- Required guardrails
- Approval recommendation

---

### Guardrail Checklist

Verification checklist organized by product family. For each guardrail:

- **In Scope:** Which risk levels require this? (All, Med+, High+, Severe)
- **Verification Criteria:** How do you confirm it's implemented?
- **Evidence Artifact:** What documentation is required?
- **Pass/Fail:** Verification status

**Product families covered:**
- AI Posture & Governance
- Runtime Protection & Guardrails
- Shadow AI & Usage Discovery
- Observability & Evaluation
- Data Protection for AI
- NHI & Agentic Access
- AI Supply Chain

---

### Exception Tracker

Track exceptions for Severe-risk tools and guardrail deviations.

**Exception Types:**

| Type | Description | Approval Required | Max Duration |
|------|-------------|-------------------|--------------|
| Severe Tool | Severe-risk tool approval (prohibited by default) | CISO + Committee + Executive | 12 months |
| Guardrail Bypass | Specific guardrail cannot be implemented | Committee | 6 months |
| Vendor Risk | Vendor doesn't meet security assessment criteria | Committee + Legal | 6 months |
| Compliance Gap | Framework control cannot be satisfied | Committee + Compliance | Until remediated |
| Emergency Use | Urgent business need, expedited review | CISO (48hr retroactive) | 30 days |

**Status workflow:** Active → Renewal Due → Expired → Closed

---

### Governance Guide

Complete governance framework including:

**1. Governance Committee**
- Cross-functional body (Security, IT Ops, Data Governance, Development, Compliance, Business)
- Owns tool classification, approves deployments, handles exceptions
- "Enable responsible AI adoption—security is a strategic partner, not an office of no"

**2. Tool Lifecycle Workflow**
- Submit Request → Classify Risk → Determine Families → Map Guardrails → Review → Approve/Deny → Implement → Verify → Register → Periodic Review

**3. Review Requirements**
- Risk-based review cadence
- Review triggers (security incidents, vendor changes, capability expansion)
- Re-classification criteria

**4. Exception Process**
- Types, approval requirements, duration limits, renewal workflow

**5. Enforcement (Tiered Revocation)**
- Warning → Restricted → Suspended → Revoked → Decommissioned

**6. Decommissioning**
- Exit criteria, data handling, access revocation, documentation

---

### Tool Function Mapping

**Risk Classification Criteria (6 factors):**

| Factor | Low | Medium | High | Severe |
|--------|-----|--------|------|--------|
| Data Sensitivity | Public only | Internal | Confidential | PII / Regulated |
| Access Permissions | Read-only | Limited write | Full read/write | Admin/root |
| Integration Depth | Isolated | Limited API | Direct system | Privileged control |
| Misuse Potential | Low | Medium | High | Severe |
| Data Persistence | — | Session only | Cached | Training data |
| External Access | — | Allowlisted | Broad internet | Unrestricted |

**Overall risk = HIGHEST rating across any factor**

**45 Tool Functions** mapped to:
- Risk level
- Required guardrails
- Recommended security products
- Product families

**New in v2.0:** Agentic AI functions including MCP Server Integration, RAG/Vector Database operations, Multi-agent orchestration, Agent task delegation, and Autonomous decision-making.

---

### AI Security Tool Landscape

**74 enterprise vendors** mapped to **7 product families**.

**New in v2.0:** Added 16 vendors including Straiker, Maxim AI, Braintrust, LangFuse, Spectra Assure, Torq, Radiant Security, Stellar Cyber, Strata Identity, NVIDIA NeMo Guardrails, Holistic AI, Airia, Adri, Prophet Security, Hex Security. Updated acquisition status for Google/Wiz ($32B pending), Palo Alto/Protect AI, CrowdStrike/Pangea, Check Point/Lakera.

| Family | Focus | Key Guardrails |
|--------|-------|----------------|
| AI Posture & Governance | Inventory, compliance, policy | Tool registration, risk classification, policy enforcement |
| Runtime Protection & Guardrails | Real-time inference protection | Prompt injection, jailbreak, output filtering, content safety |
| Shadow AI & Usage Discovery | Unauthorized AI detection | Shadow AI detection, usage logging, sanctioned status |
| Observability & Evaluation | Monitor and test AI systems | Audit logging, SIEM integration, alerting, drift detection |
| Data Protection for AI | Prevent data exposure | DLP, PII detection, encryption, data masking |
| NHI & Agentic Access | Non-human identity management | Service accounts, secrets vault, mTLS, credential rotation |
| AI Supply Chain | Model & pipeline integrity | Model provenance, training data lineage, ML pipeline security |

Each vendor entry includes:
- Status (Independent / Acquired / Platform)
- Primary / Secondary / Tertiary family coverage
- Executive summary
- Best for (use case fit)

---

### Compliance Mapping

**46 guardrails** mapped to **10 compliance frameworks:**

| Framework | Full Name | Structure |
|-----------|-----------|-----------|
| CSA AI Safety | Cloud Security Alliance AI Controls (2024) | Shared responsibility model |
| EU AI Act | European AI Regulation (2024) | Articles 9-17 for high-risk AI |
| ISO 42001 | AI Management System Standard (2023) | Clauses 5-10; Annexes A, B |
| MITRE ATLAS | Adversarial Threat Landscape for AI (2025) | 15 tactics, 66 techniques, 46 sub-techniques |
| NIST AI RMF | AI Risk Management Framework 1.0 (2023) | GOVERN, MAP, MEASURE, MANAGE |
| NIST AI 600-1 | Generative AI Profile (July 2024) | 200+ actions for GenAI risks |
| NIST IR 8596 | Cybersecurity AI Profile (Draft Jan 2026) | AI-specific cybersecurity controls |
| NIST CSF 2.0 | Cybersecurity Framework v2.0 (2024) | GOVERN, IDENTIFY, PROTECT, DETECT, RESPOND, RECOVER |
| OWASP LLM Top 10 | LLM Application Security Risks (2025) | LLM01-LLM10 |
| SOC 2 | Service Organization Control 2 (AICPA) | Trust Service Criteria |

Use for audit evidence and gap analysis.

---

### Program Metrics

**Key Performance Indicators (KPIs):**

| KPI | Description | Frequency |
|-----|-------------|-----------|
| Tool Inventory Coverage | % of AI tools in registry vs. discovered | Weekly |
| Review Completion Rate | % of reviews completed on schedule | Monthly |
| Guardrail Verification Rate | % of tools with all required guardrails verified | Monthly |
| Mean Time to Approval | Average days from request to decision | Monthly |
| Exception Rate | % of tools operating under exception | Monthly |
| Non-Compliance Rate | % of tools with failed guardrails | Monthly |
| Shadow AI Detection Rate | New unauthorized tools discovered per period | Weekly |
| Incident Rate | Security incidents involving AI tools | Monthly |
| Vendor Risk Score | Average risk score across AI vendors | Quarterly |
| Training Completion | % of users completing AI security training | Quarterly |
| **Agent Inventory Coverage** | % of AI agents registered vs. discovered | Weekly |
| **Autonomous Action Rate** | % of agent actions without human approval | Monthly |
| **Agent Incident Rate** | Security incidents involving AI agents | Monthly |

**Service Level Objectives (SLOs)** included for each metric with targets and thresholds.

**New in v2.0:** Added Agentic AI-specific KPIs to track agent deployments, autonomous actions, and agent-related incidents.

---

## Risk Classification Model

| Risk Level | Approval | Review Cadence | Characteristics |
|------------|----------|----------------|-----------------|
| **Low** | Standard | Annual | Public data, read-only, isolated |
| **Medium** | Department lead | Semi-annual | Internal data, limited write, bounded scope |
| **High** | Committee | Quarterly | Confidential data, system access, significant impact |
| **Severe** | Exception required | Monthly | Regulated data, privileged access, autonomous actions |

---

## Product Families

The framework organizes AI security controls into 7 product families:

1. **AI Posture & Governance** — Know what you have, enforce policy
2. **Runtime Protection & Guardrails** — Stop bad things in real-time
3. **Shadow AI & Usage Discovery** — Find unauthorized AI usage
4. **Observability & Evaluation** — Monitor, test, detect drift
5. **Data Protection for AI** — Prevent data exposure
6. **NHI & Agentic Access** — Manage non-human identities
7. **AI Supply Chain** — Secure models and pipelines

Required families are determined by tool risk level and functions.

---

## Compliance Frameworks

The framework maps controls to 10 industry frameworks:

- **CSA AI Safety** — Cloud-focused AI controls
- **EU AI Act** — European regulatory requirements
- **ISO 42001** — AI management system standard
- **MITRE ATLAS** — Adversarial threat coverage (2025 edition)
- **NIST AI RMF** — US government AI risk framework
- **NIST AI 600-1** — Generative AI Profile (July 2024)
- **NIST IR 8596** — Cybersecurity AI Profile (Draft Jan 2026)
- **NIST CSF 2.0** — General cybersecurity framework
- **OWASP LLM Top 10** — LLM-specific vulnerabilities (2025 edition)
- **SOC 2** — Service organization controls

---

## Customization

The framework is designed to be adapted to your environment:

| Component | Customization Options |
|-----------|----------------------|
| Governance Guide | Adjust committee roles, review cadences, enforcement actions |
| Tool Registry | Add columns for cost center, contract expiration, etc. |
| Intake Form | Add organization-specific questions (approvals, budget codes) |
| Guardrail Checklist | Add or remove guardrail items per your requirements |
| Tool Function Mapping | Add environment-specific functions; adjust product recommendations |
| Program Metrics | Adjust targets and thresholds to your maturity level |

---

## Contributing

This framework will evolve as AI security practices mature. Contributions welcome:

- **Issues:** Found a gap? Have a question? Open an issue.
- **Pull Requests:** Additions, clarifications, real-world examples—all welcome.
- **Experience reports:** Implemented this? I'd love to hear what worked and what didn't.
- **Vendor updates:** The landscape changes fast—help keep it current.

---

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

You are free to:
- **Share** — copy and redistribute in any medium or format
- **Adapt** — remix, transform, and build upon the material for any purpose

With attribution.

---

## Author

**Jason Robbins**

---

*Built for the security community. Not paywalled.*
