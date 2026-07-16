---
name: continuous-agent-loop
description: Patterns for continuous autonomous agent loops with quality gates, evals, and recovery controls.
origin: claude-fulcrum
---

# Continuous Agent Loop

> **Superseded (Jun 2026):** Loop Engineering (`loop-engineering` skill) is the new canonical paradigm. This skill is retained for backward compatibility with existing workflows.
>
> See `skills/loop-engineering/` for the complete Loop Engineering framework including `/goal`, `/loop`, Dynamic Workflows (ultracode), 5+1 building blocks, and L0-L3 readiness levels.

This is the v1.8+ canonical loop skill name. It supersedes `autonomous-loops` while keeping compatibility for one release.

## Loop Selection Flow

```text
Start
  |
  +-- Need strict CI/PR control? -- yes --> continuous-pr
  |                                    
  +-- Need RFC decomposition? -- yes --> rfc-dag
  |
  +-- Need exploratory parallel generation? -- yes --> infinite
  |
  +-- default --> sequential
```

## Combined Pattern

Recommended production stack:
1. RFC decomposition (`ralphinho-rfc-pipeline`)
2. quality gates (`plankton-code-quality` + `/quality-gate`)
3. eval loop (`eval-harness`)
4. session persistence (`nanoclaw-repl`)

## Failure Modes

- loop churn without measurable progress
- repeated retries with same root cause
- merge queue stalls
- cost drift from unbounded escalation

## Recovery

- freeze loop
- run `/harness-audit`
- reduce scope to failing unit
- replay with explicit acceptance criteria
