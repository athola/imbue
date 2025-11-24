---
name: catchup
description: A methodology for summarizing changes, extracting insights, and identifying follow-up actions.
category: analysis-methods
tags: [summarization, context-acquisition, insights, follow-ups, efficiency]
dependencies: []
tools: [git, log-tools]
usage_patterns:
  - context-catchup
  - handoff-preparation
  - progress-review
complexity: intermediate
estimated_tokens: 1600
---

# Catchup Analysis Methodology

## Overview

This document outlines a structured method for quickly understanding recent changes in a project or task. It helps to answer "what changed and what matters?". While the examples focus on git, this method can be applied to reviewing meeting notes, sprint progress, document revisions, or system logs.

## When to Use
- When joining ongoing work and need to understand current state
- Before planning sessions to understand what's already done
- After returning from absence to catch up on progress
- When reviewing someone else's work for handoff
- Any context requiring efficient extraction of "what happened and what's next"

## Activation Patterns
**Trigger Keywords**: catchup, summary, status, what's new, progress, context, state, handoff
**Contextual Cues**:
- "get me up to speed" or "catch me up"
- "what's the current status" or "where are we"
- "summarize the progress" or "what have I missed"
- "help me understand this project"
- "what's the context here"

**Auto-Load When**: Returning to work after absence, joining new projects, or when rapid context acquisition is needed.

## Required TodoWrite Items
1. `catchup:context-confirmed`
2. `catchup:delta-captured`
3. `catchup:insights-extracted`
4. `catchup:followups-recorded`

Mark them complete as you finish each section. Keep tokens lean—reference rather than reproduce.

## Step 1: Confirm Context (`catchup:context-confirmed`)
Establish the boundaries of your catchup:
- **Scope**: What are you catching up on? (e.g., a git branch, a sprint, a project, a series of meetings)
- **Baseline**: What is your last known state? (e.g., a specific commit, date, or version)
- **Current**: What is the target state to understand? (e.g., the `HEAD` of a branch, today's date, the latest release)

**Git Example:**
These commands help establish context in a git repository:
```bash
pwd                                                 # Show current directory
git status -sb | head -n 1                          # Show current branch and status
git rev-parse --abbrev-ref --symbolic-full-name @{u}  # Show the upstream branch, if one is being tracked
```

**Generic Application:** For a sprint catchup, identify the last standup you attended. For a document review, note the last version you read. For logs, identify the time window to review.

## Step 2: Capture Delta (`catchup:delta-captured`)
Gather the raw change information efficiently:

**Enumeration Approach:**
- List changed items without deep-diving yet
- Capture metrics: count, size, categories affected
- Prioritize: source/config/docs over generated/cache/build artifacts

**Git Example:**
```bash
git diff --stat ${BASE}...HEAD
git diff --name-only ${BASE}...HEAD
```

**Generic Application:** For meeting notes, list topics covered. For sprint work, list tickets completed/in-progress. For logs, identify unique event types.

Skip generated artifacts and focus on material changes.

## Step 3: Extract Insights (`catchup:insights-extracted`)
For each significant item, extract the essential understanding:

**Per-Item Analysis (2-3 sentences max each):**
- **What**: Factual description of the change
- **Why**: Likely motivation (feature, fix, refactor, requirement)
- **Implications**: Tests needed, risks introduced, dependencies created

**Efficient Inspection:**
- Open only necessary sections (use targeted searches, not full reads)
- If deeper analysis needed, defer to specialized skills rather than bloating catchup

**Git Example:**
```bash
rg -n "pattern" file  # targeted search
sed -n 'start,endp' file  # specific lines only
```

**Rollup:** Synthesize individual insights into themes (e.g., "authentication overhaul", "performance optimization phase 1", "documentation refresh").

## Step 4: Record Follow-ups (`catchup:followups-recorded`)
Capture actionable next steps:

**Follow-up Categories:**
- **Tests**: Verification needed for changes
- **Documentation**: Docs requiring updates
- **Reviews**: Items needing stakeholder attention
- **Blockers**: Issues discovered that impede progress
- **Questions**: Clarifications needed from others

If no follow-ups identified, explicitly state "No follow-ups identified."

**Output Format:**
```
## Summary
[2-3 sentence theme + risk overview]

## Key Changes
- [Item 1]: [what/why/implication]
- [Item 2]: [what/why/implication]

## Follow-ups
- [ ] [Concrete action with owner if known]
- [ ] [Concrete action]

## Blockers/Questions
- [Item requiring resolution]
```

## Integration Notes
- Use `imbue:diff-analysis` when semantic categorization and risk assessment are needed
- Use `imbue:evidence-logging` to capture commands/sources for reproducibility
- In git contexts, `sanctum:git-workspace-review` provides the raw data
- Feed insights to `brainstorming` if solution exploration is needed
- Feed insights to `writing-plans` only after catchup reveals concrete work

## Token Conservation
- Reference file paths + line numbers instead of reproducing content
- Summarize rather than paste large outputs
- Defer deep analysis to specialized skills

## Exit Criteria
- All four TodoWrite items created and checked off
- Context boundaries clear, delta enumerated, insights extracted, follow-ups captured
- Stakeholders can understand current state from your summary without re-reading sources
