---
name: loop-engineering
description: >
  Design autonomous agent loops instead of hand-writing prompts. Covers /goal,
  /loop, Dynamic Workflows (ultracode), 5+1 building blocks, L0-L3 readiness,
  and production patterns. Supersedes autonomous-loops and continuous-agent-loop.
---

# Loop Engineering

**You shouldn't be prompting coding agents anymore. You should be designing loops that prompt your agents.** — Peter Steinberger

Loop engineering is replacing yourself as the person who prompts the agent. You design the system that does it instead. A loop is a recursive goal: define a purpose and the AI iterates until complete.

The leverage point moved from crafting individual prompts to designing control systems that orchestrate agents over time.

## The 5+1 Building Blocks

Every loop needs five things and one place to remember stuff:

| # | Building Block | Claude Code Primitive | Purpose |
|---|---------------|----------------------|---------|
| 1 | **Automations** | `/loop`, cron, hooks, GitHub Actions | Discovery + triage on a cadence |
| 2 | **Worktrees** | `git worktree`, `--worktree`, `isolation: worktree` | Safe parallel execution |
| 3 | **Skills** | `SKILL.md` in `.claude/skills/` | Persistent project knowledge |
| 4 | **Plugins & Connectors** | MCP servers + plugins | Reach into real tools |
| 5 | **Sub-agents** | Task subagents, agent teams | Maker/checker split |
| 6 | **Memory** | `STATE.md`, `LOOP.md`, `AGENTS.md`, Linear | Survive context resets |

Memory is the sixth piece — the model forgets everything between runs, so state must live on disk, not in context.

## Core Primitives

### `/goal` — Run until done
Keeps working across turns until a verifiable stopping condition holds. After every turn a separate small model (Haiku-class) checks whether you are done. Maker/checker split applied to the stop condition itself.

```
/goal All tests in test/auth pass and lint is clean
```

### `/loop` — Run on cadence
Re-runs a prompt or command on an interval.

```
/loop 1d Run $loop-triage. Read STATE.md. Append findings. Update Last run.
/loop 30m /slack-feedback
```

### Dynamic Workflows (`/effort ultracode`)
Claude writes a JavaScript orchestration script that spawns tens to hundreds of parallel subagents. The runtime executes the script deterministically — it does not interpret it through a model.

```
/effort ultracode
```

Then Claude plans a workflow for every substantive task. Key API:

| Function | Purpose |
|----------|---------|
| `agent(prompt, opts)` | Spawn a subagent. Returns string or parsed object if `schema` provided |
| `parallel(thunks)` | Execute array of functions concurrently, barrier after all resolve |
| `pipeline(items, stages)` | Run each item through stages in order, no barrier between stages |
| `phase(title)` | Mark start of a named phase (UI grouping only) |
| `resumeFromRunId` | Cached results from completed agents on re-invocation |

Options: `label`, `phase`, `model`, `agentType`, `schema` (JSON Schema validation).

Constraints:
- Up to 16 concurrent agents
- 1,000 agents total per run
- No mid-run user input
- Resumable within same session

### Bundled Workflow
```
/deep-research <question>
```
Fans out web searches, cross-checks sources, votes on claims, returns a cited report.

## Patterns (L0-L3 Maturity)

| Pattern | Cadence | Risk | Readiness |
|---------|---------|------|-----------|
| Daily Triage | 1d-2h | Low | L1 report-only |
| Issue Triage | 2h-1d | Low | L1 |
| CI Sweeper | 5-15m | Medium | L2 assisted |
| PR Babysitter | 5-15m | Medium | L2 |
| Dependency Sweeper | 6h-1d | Medium | L2 |
| Post-Merge Cleanup | 1d-6h | Low | L1 |
| Changelog Drafter | 1d | Low | L1 |

### Readiness Levels
| Level | Description | What's checked |
|-------|-------------|----------------|
| **L0 — Draft** | Documented intent only | §1 Purpose & Scope |
| **L1 — Report** | Triage → state, no auto-action | §1-3, §5 |
| **L2 — Assisted** | Small auto-fixes with verifier | §1-7 |
| **L3 — Unattended** | Runs without you watching | All sections |

## Loop Design Checklist (abbreviated)

- [ ] Single clear goal — one sentence
- [ ] Maker/checker split — implementer != verifier
- [ ] State file survives context resets
- [ ] Escalation triggers defined
- [ ] Denylist paths (auth, payments, secrets)
- [ ] Token budget estimated
- [ ] Report-only first (L1) before enabling fixes (L2+)

## Relationship to Existing Central Skills

| Existing Skill | Status | Notes |
|---------------|--------|-------|
| `continuous-agent-loop` | **Superseded** | Pre-loop-engineering paradigm. Replace with this skill |
| `autonomous-loops` | **Superseded** | Deprecated in v1.8.0, retained for compat |
| `verification-loop` | **Complementary** | Verification patterns still valid within L2+ loops |
| `autopilot` (Citadel) | **Complementary** | Citadel's autonomous dispatch, narrower scope |
| `auto-run` (corps) | **Complementary** | Dispatch-reconcile loop, overlaps with L2 patterns |
| `agentic-orchestrator` (Sean) | **Complementary** | Task decomposition + done gate, usable inside L2 loops |
| `experiment` | **Complementary** | Optimization loop with fitness function, specific use case |
| `do` (Citadel) | **Updated** | Already routes `/loop`, `/goal`, `/daemon` commands |

## Quick Start

1. Pick a pattern from the table above
2. Start in L1 report-only mode
3. Create `STATE.md` as the memory spine
4. Run the loop: `/loop 1d Run $loop-triage`
5. Read state daily for 1-2 weeks
6. Tune the triage skill before enabling auto-fixes
7. Graduate to L2 with verifier sub-agent + worktree isolation

## Reference

- Addy Osmani: [Loop Engineering](https://addyosmani.com/blog/loop-engineering/)
- Claude Docs: [Dynamic Workflows](https://code.claude.com/docs/en/workflows.md)
- Claude Docs: [/goal](https://code.claude.com/docs/en/goal)
- Claude Docs: [/loop & scheduled tasks](https://code.claude.com/docs/en/scheduled-tasks)
- cobusgreyling/loop-engineering: [GitHub](https://github.com/cobusgreyling/loop-engineering) — starters, audit CLI, patterns
- Audit your project: `npx @cobusgreyling/loop-audit . --suggest`
- Scaffold a starter: `npx @cobusgreyling/loop-init . --pattern daily-triage --tool claude-code`
