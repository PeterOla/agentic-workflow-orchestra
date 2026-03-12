# Agentic Workflow Orchestra

![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)
![Agent: GitHub Copilot](https://img.shields.io/badge/agent-GitHub%20Copilot-black.svg)
![Category: Workflow Orchestration](https://img.shields.io/badge/category-workflow%20orchestration-4f46e5.svg)

Agentic Workflow Orchestra is a project-agnostic orchestration framework for AI coding agents.

It gives agents a disciplined operating model for planning, sequencing, handoffs, verification gates, and parallel-safe execution across real software projects.

## One-Line Pitch

Use this when one agent is not enough, but chaos is unacceptable.

## What It Solves

Most multi-agent work fails in the same ways:

- planning and implementation get mixed together
- multiple agents touch the same files without coordination
- shared contracts drift across frontend, backend, and pipeline work
- verification happens too late
- session context disappears between handoffs

This skill fixes that with explicit phases, gates, logs, and startup rules.

## Who It Is For

Good fit:

- full-stack applications with distinct workstreams
- projects with shared interfaces or schemas
- repositories where quality gates matter
- teams using GitHub Copilot or similar agent workflows

Poor fit:

- one-file scripts
- tiny fixes with no coordination cost
- projects with no real handoff or verification needs

## Install

After publishing this repository, install it with:

```bash
npx skills add PeterOla/agentic-workflow-orchestra --agent github-copilot --copy -y
```

If you publish under a different owner or repo name, update the install command accordingly.

## What The Skill Provides

- a default phase model for planning through release
- handoff logging conventions
- startup and verification checklists
- rules for parallel-safe vs sequential work
- a minimal workflow template for new projects

The package defines how agents collaborate. Each consuming repository defines what gets built through its own `orchestra/` files.

## Recommended Project Layout

```text
your-project/
├── .agents/
│   └── skills/
│       └── agentic-workflow-orchestra/
│           └── SKILL.md
├── agents/
│   └── logs/
├── orchestra/
│   ├── README.md
│   ├── lessons.md
│   └── workflows/
│       ├── 01-planning.md
│       ├── 02-core.md
│       └── 03-qa.md
└── optional project instructions file
```

The project instructions file can be named however your team prefers, for example `CLAUDE.md`, `AGENTS.md`, or `.instructions.md`.

## Quick Start

1. Install the skill.
2. Create `agents/logs/` for handoff summaries.
3. Create `orchestra/README.md` with your project-specific roles, phases, and gates.
4. Create `orchestra/lessons.md` for durable rules and corrections.
5. Add numbered workflow files under `orchestra/workflows/`.
6. Define shared contracts before implementation starts.

## Default Phase Model

```text
Phase 0: Plan       -> design, contracts, decisions
Phase 1: Skeleton   -> parallel-safe scaffolding by domain
					   CONTRACT GATE
Phase 2: Core Flow  -> critical path features in dependency order
					   INTEGRATION GATE
Phase 3: Expand     -> independent features and polish
					   PRODUCTION GATE
Phase 4: Ship       -> deployment and operational readiness
```

Projects may rename phases, but the sequencing intent should remain stable.

## Minimal Workflow Template

```markdown
# Workflow 01: Planning

> Agent Role: Planner
> Phase: Plan
> Depends on: project instructions
> Produces: design docs, contracts, implementation plan

## Purpose

Describe what this workflow owns and what it must not do.

## Deliverables

- files or documents to create
- contracts to define
- decisions to lock before downstream work begins

## Build Order

1. gather context
2. define contracts
3. write artifacts
4. verify completeness

## Verification Checklist

- required artifact exists
- downstream teams can consume it
- open questions are documented

## Handoff

Write a completion log to `agents/logs/` with built files, contracts, issues, and next steps.
```

## Why The Name Is Spelled This Way

The public package name is `agentic-workflow-orchestra`.

The earlier `orchastra` variants are incorrect and should not be published.

## First Public Push Checklist

Before the first GitHub push for the public skill repository:

- confirm the repository name is exactly `agentic-workflow-orchestra`
- keep `README.md`, `SKILL.md`, and `LICENSE` at the repo root
- verify the install command matches the final owner and repo path
- confirm `SKILL.md` reads coherently in a clean repository with no GameIQ context
- remove or avoid any project-specific references that imply hidden prerequisites
- check that the examples are generic and adaptable across stacks
- verify the MIT license copyright line uses the exact public author name you want
- test the installation flow from a separate clean project after publishing

## Release Sanity Check

This package is ready to publish when:

- the install command points to the real public repo
- setup instructions create every required directory
- the skill works as a standalone artifact without private project history
- the compatibility alias is not presented as the primary package
- an external user can understand the quick start without additional explanation