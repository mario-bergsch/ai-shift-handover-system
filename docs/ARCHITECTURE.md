# Architecture Overview

## System Flow

```
SHIFT NOTES (Markdown/Text)
    ↓
CLAUDE 3 SONNET API
    ↓
    ├─→ SBAR Report Generator
    │   └─→ Structured 1-page handover
    │
    └─→ RCA Analysis Generator
        └─→ 6M + 5-Why root cause
    ↓
[OUTPUTS: Markdown files]
    ↓
n8n WORKFLOW (Phase 2)
    ├─→ Parse outputs
    ├─→ Post to Slack
    ├─→ Archive to Obsidian
    └─→ Trigger escalations
```

---

## Components

### Input: Shift Notes

Standard format: Markdown or structured text with sections:
- Production data (throughput, OEE)
- Quality issues (problem, line, cause, action)
- Safety incidents
- Open actions
- Material status

### Claude AI Processing

**Model:** Claude 3 Sonnet (Anthropic)

**Two parallel prompts:**
1. SBAR Prompt → Generates structured handover report
2. RCA Prompt → Generates root cause analysis

**Key constraints:**
- No hallucinations (marks missing data)
- Concrete recommendations only
- German language
- Max 1 page for SBAR

### Outputs

**SBAR Report:**
- SITUATION (critical facts first)
- BACKGROUND (problems and context)
- ASSESSMENT (evaluation and risks)
- RECOMMENDATION (concrete next steps)

**RCA Report:**
- 6M categorization (Machine/Material/Method/Milieu/Mensch/Messung)
- 5-Level Why analysis
- Severity classification
- Containment actions
- Prevention measures

---

## Data Flow

```
Raw Shift Data
    ↓
[Validation]
    ├─→ Check for missing fields
    ├─→ Mark ambiguities
    └─→ Extract key facts
    ↓
[Claude Processing]
    ├─→ Parse shift notes
    ├─→ Extract problems
    ├─→ Categorize by severity
    └─→ Generate structured reports
    ↓
[Quality Checks]
    ├─→ Verify accuracy
    ├─→ Check completeness
    └─→ Validate recommendations
    ↓
[Output]
    ├─→ SBAR Report (Markdown)
    └─→ RCA Report (Markdown)
```

---

## Integration Points (Phase 2+)

### n8n Workflow

- **Trigger:** New shift notes file created
- **Step 1:** Read shift notes from Obsidian / file storage
- **Step 2:** Call Claude SBAR API
- **Step 3:** Call Claude RCA API
- **Step 4:** Post results to Slack channel
- **Step 5:** Archive to knowledge base

### Slack Integration

- Post SBAR to #shift-reports channel
- Post critical items to #escalations
- Include links to full reports

### Obsidian Integration

- Store all shift notes
- Archive generated reports
- Link related incidents
- Track metrics over time

### SAP Integration (Phase 3)

- Fetch OEE data from SAP via OData
- Enrich reports with context
- Post quality issues to SAP
- Track improvement KPIs

---

## Deployment Options

### Option 1: Manual (Today)
- Copy shift notes
- Paste into ChatGPT / Claude
- Copy outputs to Slack/Obsidian

### Option 2: CLI (Phase 2)
- Python script with Claude SDK
- `shift-report input.md → output.md`
- Programmatic automation

### Option 3: API (Phase 2)
- n8n workflow with REST calls
- Automatic file monitoring
- Scheduled execution

### Option 4: Full Platform (Phase 3+)
- Docker containers
- Kubernetes deployment
- Multi-shift orchestration
- SAP integration

---

**Created:** 2026-06-04  
**Status:** MVP Phase (Phase 1 complete, Phase 2 in planning)
