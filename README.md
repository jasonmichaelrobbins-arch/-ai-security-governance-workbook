# AI Security Risk Workbook v3.0

A program workbook for AI risk and the Claude skill that runs it. The workbook holds who you are, how you route decisions, the tools you own, the functions and guardrails you classify against, and the compliance mapping. The skill reads the workbook and produces one AI Risk Assessment Record per request, whether that request is a vendor product you are buying, a vendor adding AI to something you already run, or something your own team is building. Each assessment stands on its own: nothing in the workbook records what was approved before, so a second request is judged the way the first one was.

Two files to use, one to install:

1. **`AI_Security_Risk_v3.0.xlsx`**, the program workbook. Nine tabs.
2. **`AI_Intake_Form.xlsx`**, the standalone intake. The same form sits on a tab inside the workbook.
3. **`ai-tool-risk-assessment_v3.0.skill`**, the Claude skill. Install it in any Claude environment that supports `.skill` packages, hand it the workbook, and name a tool.

## The workbook

| Tab | What it holds |
|---|---|
| Start Here | How the pieces fit, the tab list, how a request runs, the four data classes and risk levels at a glance |
| Org Profile | Your context, governance routing by level (approver, risk acceptor, reviewer and the verifier who checks guardrails after deployment), the tools you already own with one or more tools per guardrail family, the program rules every new tool is held to (MCP policy, training position, data and autonomy ceilings, build gate), rules for AI use on vendor documents, and how records look. The keys in column A are what the skill reads. |
| Tool Function Mapping | The seven risk factors with four levels each, and 57 functions mapped to a risk level, the agentic flag, the guardrails each function requires (by name and by ID) and their families. The functions a tool performs decide its guardrails. |
| Guardrail Checklist | 65 guardrails across seven families, each with the rule that puts it in scope (Every tool for the program's own steps, Vendor products for anything bought, By function for the rest, with the functions that name it listed beside it), the agentic flag, what to verify and the evidence that proves it. Two optional columns: "Your control", the tool or mechanism that meets the guardrail where the family tools on the Org Profile are too coarse, and "Active", the switch that drops a guardrail from every record without deleting it |
| Intake Form | 45 rows, multiple choice wherever the answer has a fixed shape: 8 about the request, 16 on how the tool will be used, 10 for vendor products, 11 for internal builds. Only the tool name and the kind of request are required. |
| Tool Registry | Living inventory with risk, data class, owners, status, review dates and the record ID |
| Exception Tracker | Seven exception types with approval, duration and renewal, plus the log |
| AI Security Tool Landscape | The seven families and about 100 vendors mapped to primary, secondary and tertiary coverage, with statuses checked against public M&A reporting through September 2026 |
| Compliance Mapping | Every guardrail mapped to CSA AICM v1.1, the EU AI Act, ISO/IEC 42001, MITRE ATLAS (2026.09), NIST AI RMF, NIST AI 600-1, OWASP (LLM Top 10 and Agentic Top 10) and SOC 2. No blank cells. |

Cream cells are yours. Rose cells hold the keys and the calculated values. Every governance setting has a starter value, so a team can fill the Org Profile in an hour and change only what differs. Four data classes are fixed across the workbook: Public (Low), Internal (Medium), Confidential (High) and Restricted (Severe). A hidden Lists tab holds the longer pick lists; edit a list there to change the options a cell offers.

## The skill

Give it the completed workbook and a tool name. It works out which of the three kinds of request it has, researches what the vendor publishes or uncovers an internal build from the engineering owner, confirms the few facts only you know, scores the seven factors, and issues the record: the security team's assessment, in place of a vendor questionnaire, written in the third person so it reads as an auditable artifact. It carries the functions the tool performs with the guardrails each one brings and the control that meets each, a control-coverage section that totals, family by family, what the organization meets, what the vendor alone meets, and the gaps and the unknowns, a STRIDE threat model with compensating controls, the lethal-trifecta check and MITRE ATLAS technique IDs, the required guardrails grouped by family with what requires each one, its owner (vendor, internal or shared), its status at issue (identified, gap, unknown or not applicable) and the control that meets it, findings with owners and due points, and between zero and four questions for the vendor or the requester. A question is only asked where the answer would move a risk factor up or down; the one standing exception is ISO/IEC 42001 certification, which is the strongest vendor-side evidence and the first thing asked for.

The skill does not decide. Section 3 of the record, decision and approval, is blank when the record is issued and is completed by the approver the Org Profile names for the level; the script reads it back so the one file carries the decision, the answers to the questions and, later, the verification marks.

The record is an Excel file with three visible sheets. "Assessment" carries thirteen sections in the same order every time. "Verification" carries the required guardrails for a person to walk after deployment, marking each one Pass or Fail with the evidence seen, so security approves a tool with guardrails and then confirms they were put in place. "Coverage data" is one flat row per required guardrail (family, guardrail, functions, owner, status, control, the organization tools matched, the verification result) for the program's metrics: append it across records and the guardrail coverage, verification rate and gaps by family fall out of a pivot. A hidden data sheet lets a second pass or the verification pass pick up exactly where the first left off.

```
python scripts/read_workbook.py AI_Security_Risk_v3.0.xlsx --intake AI_Intake_Form.xlsx --out profile.json
python scripts/build_record.py record.json --profile profile.json
python scripts/build_record.py --extract AI_Risk_Assessment_<Tool>_<date>.xlsx record.json
```

## What changed in v3.0

- Rebuilt in the program-workbook layout: keyed Org Profile, libraries as tables the skill reads, one place to change each thing.
- Three kinds of request: vendor product, vendor-added AI feature, internal build. Internal builds get their own intake block, because there is nothing public to research.
- The intake dropped from about 70 fields to 45, multiple choice wherever the answer has a fixed shape.
- Four fixed data classes replace per-organization labels. Static lists of approved tools and platforms are gone; each assessment is independent.
- More than one tool can do guardrail duty: the family rows on the Org Profile take a comma-separated list, and the Guardrail Checklist names tools per guardrail where that is more precise.
- The guardrail checklist on a record is for after deployment. At issue the record says who owns each guardrail and which control meets it; the Verification sheet is where a person marks Pass or Fail once the tool is live.
- The record is an assessment, not a decision: the decision block is blank at issue and completed by the approver, and the whole record is written in the third person.
- A control-coverage section totals coverage per guardrail family, with gaps and unknowns by ID, and a Coverage data sheet carries one row per required guardrail with the organization tools matched by name, as the feed for the program's KPIs and maturity reporting.
- Section 13 holds the security review outcome as a mark-all-that-apply box (approved, approved with conditions, escalated, requires a policy exception, returned for information, not approved) with name, role and date fields for the checker and the signer, all blank at issue and read back by the script; section 3 holds the approver's decision. Findings print in priority order, Severe to Low.
- Questions on a record are asked only where the answer moves a risk factor, with ISO/IEC 42001 certification as the standing exception. Cap of four, set on the Org Profile.
- STRIDE threat modeling is back on every record, each row with its compensating controls, plus the lethal-trifecta check and ATLAS technique IDs.
- Guardrails are required by the functions a tool performs, not by its risk level. The level routes the decision; the functions decide the controls, plus a short baseline the program applies to every tool (and to every vendor product). A record for a drafting assistant and a record for an agent that runs shell commands carry different lists, and nothing on either list is there for no reason.
- The functions a tool performs have their own section on the record, with the guardrails each function requires printed under it, and the required-guardrail list says for every line what requires it: the baseline rule or the named functions.
- Two agentic guardrails added: agent behavior monitoring and agent memory protection. 65 guardrails in all, 21 flagged agentic.
- Compliance mapping narrowed to the seven frameworks a generic program answers to, across eight columns, with every cell filled. ATLAS references use the 2026.09 data release, including the agentic techniques and mitigations. OWASP includes the Agentic Top 10.
- Landscape refreshed: about 100 vendors, acquisitions through September 2026.
- Program Metrics, User Guide and Governance Guide retired. Their settings live on the Org Profile; the process lives in the skill.

## License

Apache License, Version 2.0. Copyright 2026 Jason Robbins. The license covers the workbook, the intake form, the skill and its scripts; see `LICENSE` for the terms and `NOTICE` for the attribution that travels with any redistribution. Fork it, edit it, run it against your own tool landscape and context, and ship it inside your own program; the only asks are that the license and the NOTICE file stay with it and that changed files say they were changed.

Vendor and product names are used to identify those products and do not imply endorsement of, or affiliation with, the vendors named. Framework names and control identifiers belong to their owners; the workbook cites them and does not reproduce their text. The worked examples use fictional organizations and vendors.

To cite the workbook, use `CITATION.cff` (GitHub renders it as a "Cite this repository" link). Contributions follow `CONTRIBUTING.md`.
