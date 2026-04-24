# AI Security Risk — v2.0 Release

Two files to upload to the repo root:

1. **`AI_Security_Risk_v2.0.xlsx`** — the governance workbook.
   - 11 tabs: Overview, User Guide, Governance Guide, Tool Function Mapping, Intake Form, Guardrail Checklist, Tool Registry, Exception Tracker, AI Security Tool Landscape, Compliance Mapping, Program Metrics.
   - Counts: 57 tool functions, 64 guardrails (with Agentic dual-tag), 88 security vendors, 21 compliance frameworks.
   - Acquisition statuses current through April 2026 (includes Palo Alto / CyberArk $25B close Feb 2026, Google / Wiz $32B close Mar 2026, plus the 2025 consolidation wave).
   - Unified muted color palette: 4 risk tiers + 7 family colors + status colors + CMM-level progression.
   - Intake Form uses structured selectors (checkbox groups) for every field that can be structured.
   - Every row sized explicitly to fit its content.

2. **`ai-tool-risk-assessment_v2.0.skill`** — the Claude skill that consumes the workbook as a reference template and produces per-tool or per-option assessments.
   - Install in any Claude environment that supports `.skill` packages.
   - Runs against any 1.2-style or v2.x-style reference workbook (auto-detects column layout).
   - Operates with a principal security architect mindset (STRIDE threat modeling, Zero Trust, assume-breach, residual risk, graduated agent autonomy, NIST AI RMF / OWASP LLM / MITRE ATLAS framing).
   - Three modes: single-tool (default), multi-tool portfolio, deployment-option comparison.
   - Output sections per tool: profile, threat model, data handling / logging / retention / isolation, prompt-injection deep dive, guardrail coverage by family, concerns with severity, PAM integration pattern, deployment recommendation, applicable functions, applicable guardrails (trust-but-verify with Pass/Fail/Notes/Evidence columns), recommended products, architect approval signoff block.

## Suggested repo layout (flat)

```
AI_Security_Risk_v2.0.xlsx
ai-tool-risk-assessment_v2.0.skill
README.md                 # this file, renamed
```

## Release notes

- Acquisition refresh (Palo Alto / CyberArk $25B closed Feb 2026; Google / Wiz $32B closed Mar 2026; Check Point / Lakera, SentinelOne / Prompt + Observo, CrowdStrike / Pangea, F5 / CalypsoAI, Cato / AIM all confirmed closed).
- Intake Form restructured with structured selectors instead of open text.
- Unified dusty-pastel palette: 4 risk tiers + 7 distinct family colors, all muted and cohesive with the risk scale.
- Tool Landscape: Primary / Secondary / Tertiary family columns color-coded consistently across 88 vendors.
- Compliance Mapping: scroll-through layout with family-banded guardrail matrix (no freeze panes that hid the view).
- Guardrail Checklist: Pass / Fail columns center-aligned.
- Program Metrics: CMM maturity levels color-graduated from terracotta (L1) to deep sage (L5).
- Row heights computed per cell so wrapped text displays fully without reader-side resize.
- Skill's extractor auto-detects column positions, working across 1.2 and v2.x layouts.

## License / sharing

The workbook is a template. Fork, edit, run against your own vendor landscape and org context. The skill's `Your Org's Context` block in SKILL.md is where your friend sets PAM / IdP / SIEM / DLP values for their environment — Claude uses those values when generating assessments.
