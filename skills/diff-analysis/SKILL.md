---
name: diff-analysis
description: A methodology for categorizing changes, assessing risks, and creating summaries from any changeset.
category: analysis-methods
tags: [changes, semantic-analysis, risk-assessment, categorization, summaries]
dependencies: []
tools: [git, diff-tools]
usage_patterns:
  - change-analysis
  - risk-assessment
  - release-preparation
complexity: intermediate
estimated_tokens: 1800
---

# Diff Analysis Methodology

## Overview

This document outlines a structured method for analyzing changesets. Instead of just listing changes, it provides a way to categorize them, assess their risks, and generate insights. This method can be used for git diffs, but also for configuration changes, API migrations, schema updates, or document revisions.

## When to Use
- After gathering raw change data to extract meaningful insights
- Before code reviews to categorize and prioritize changes
- When preparing release notes or changelogs requiring semantic understanding
- During migration planning to assess scope and risk
- Any context requiring structured analysis of "what changed and why it matters"

## Activation Patterns
**Trigger Keywords**: diff, changes, what's new, release notes, changelog, migration, impact, risk assessment
**Contextual Cues**:
- "what changed in this branch/PR"
- "analyze these changes" or "categorize the diffs"
- "assess the impact" or "what are the risks"
- "prepare release notes" or "summarize changes"
- "help me understand this migration"

**Auto-Load When**: Git diffs are present, change analysis is requested, or impact assessment is needed.

## Required TodoWrite Items
1. `diff-analysis:baseline-established`
2. `diff-analysis:changes-categorized`
3. `diff-analysis:risks-assessed`
4. `diff-analysis:summary-prepared`

Mark each item complete as you finish the corresponding step.

## Step 1: Establish Baseline (`diff-analysis:baseline-established`)
Define the comparison scope clearly:
- **What**: Identify the two states being compared (e.g., before/after, baseline/current, v1/v2).
- **Where**: Note the boundary of analysis (e.g., a repository, a service, a set of configuration files, a document).
- **Scale**: Capture metrics on the scope of the changes (e.g., number of files changed, lines modified, items affected).

**Git Example:**
These commands help establish a baseline for comparison in a git repository:
```bash
git log --oneline -1 HEAD                   # Show the latest commit
git merge-base HEAD main                    # Find the common ancestor between HEAD and main
git diff --stat <baseline>..HEAD | tail -1  # Show summary of changes between baseline and HEAD
```

**Generic Application:** For API changes, compare the OpenAPI specification files. For configuration changes, diff the YAML or JSON files. For database schema changes, compare the DDL or migration files.

## Step 2: Categorize Changes (`diff-analysis:changes-categorized`)
Group changes by semantic type, not just file type:

**Change Categories:**
- **Additions**: New capabilities, files, or entities
- **Modifications**: Changes to existing behavior or structure
- **Deletions**: Removed capabilities or deprecated items
- **Renames/Moves**: Reorganization without functional change

**Semantic Categories:**
- **Features**: New user-facing capabilities
- **Fixes**: Corrections to existing behavior
- **Refactors**: Structural improvements without behavior change
- **Tests**: Test coverage additions or modifications
- **Documentation**: Explanatory content changes
- **Configuration**: Settings, environment, or infrastructure changes

**Git Example:**
```bash
git diff --name-only --diff-filter=A <baseline>  # Added
git diff --name-only --diff-filter=M <baseline>  # Modified
git diff --name-only --diff-filter=D <baseline>  # Deleted
git diff --name-only --diff-filter=R <baseline>  # Renamed
```

Note cross-cutting changes that span multiple categories or subsystems.

## Step 3: Assess Risks (`diff-analysis:risks-assessed`)
Evaluate each change category for potential impact:

**Risk Indicators:**
- **Breaking changes**: Public API modifications, schema changes, contract alterations
- **Security-sensitive**: Authentication, authorization, cryptography, input validation
- **Data integrity**: Database operations, state management, persistence logic
- **External dependencies**: Third-party services, library updates, version changes
- **Performance-critical**: Hot paths, caching, resource allocation

**Risk Levels:**
- **Low**: Internal refactors, documentation, test additions
- **Medium**: Feature additions with tests, non-breaking API extensions
- **High**: Breaking changes, security modifications, schema migrations

Flag changes lacking corresponding test coverage or documentation.

## Step 4: Prepare Summary (`diff-analysis:summary-prepared`)
Synthesize findings into actionable output:

**Summary Structure:**
1. **Theme**: Primary purpose of the changeset (1-2 sentences)
2. **Scope**: Categories with counts (features: N, fixes: M, refactors: K)
3. **Risk Assessment**: Overall level with justification
4. **Review Focus**: Specific areas requiring careful attention
5. **Dependencies**: Prerequisites or follow-up work identified

Format for downstream consumption (PR descriptions, release notes, review checklists, stakeholder updates).

## Integration Notes
- Use `imbue:evidence-logging` to capture analysis artifacts
- Use `imbue:structured-output` to format final deliverables
- In git contexts, use `sanctum:git-workspace-review` first for raw data

## Exit Criteria
- All TodoWrite items completed with categorized changes and risk assessment
- Downstream workflows have semantic understanding of the changeset
- Summary ready for appropriate consumption (review, release notes, planning)
