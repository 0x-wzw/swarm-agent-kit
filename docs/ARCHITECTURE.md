# Architecture

## Overview

```
swarm-agent-kit/
├── SKILL.md              ← Master skill (this repo)
├── skills/               ← All sub-skills
│   ├── swarm-workflow-protocol/  ← Orchestration
│   ├── defi-analyst/              ← Finance
│   ├── agent-identity/             ← Finance (ERC-8004)
│   ├── x-interact/                ← Social
│   ├── moltbook-interact/          ← Social
│   └── [others]/                  ← Utilities
├── scripts/
│   ├── install-all.sh    ← One-command install
│   └── validate.sh        ← Skill validator
└── docs/
    ├── QUICKSTART.md
    └── ARCHITECTURE.md
```

## Design Principles

### 1. Each Skill is Self-Contained

A skill has everything it needs to function:
- `SKILL.md` — definition, usage, config
- `scripts/` — optional CLI helpers
- `references/` — optional docs/APIs

No shared state between skills. No hidden dependencies.

### 2. SKILL.md is the Contract

Every skill exposes its interface via SKILL.md:
- **name** — kebab-case identifier
- **description** — one-line when-to-use
- **body** — prerequisites, config, usage

Tools read SKILL.md to discover and use skills. Keep it accurate.

### 3. Scripts are Optional

A skill works without scripts — the SKILL.md is the source of truth. Scripts provide convenience but aren't required for core functionality.

### 4. Zero TODOs Policy

Skills are production-ready or they don't ship. No stubs, no placeholders, no TODOs in SKILL.md.

## Skill Dependencies

```
swarm-workflow-protocol
├── mcporter (for Tavily calls)
├── tmux (for session control)
└── relay server (port 18790)

defi-analyst
└── mcporter (Tavily MCP server)

x-interact
└── mcporter (Tavily MCP server)

moltbook-interact
└── moltbook.sh script

agent-identity
└── cast (for eth calls)
```

## Installation Flow

```
User runs: bash scripts/install-all.sh
    ↓
Copies each skill/ to ~/.openclaw/skills/
    ↓
User configures per-skill prerequisites (API keys)
    ↓
Skills discoverable by OpenClaw
```

## Validation Flow

```
scripts/validate.sh
    ↓
Checks each skills/*/ has SKILL.md
    ↓
Verifies name + description frontmatter
    ↓
Fixes script permissions
    ↓
Reports pass/fail per skill
```

## Adding a New Skill

1. Create `skills/new-skill/SKILL.md`
2. Follow AgentSkills spec (name, description, body)
3. Add `scripts/new-skill.sh` if CLI tooling needed
4. Add to `scripts/install-all.sh`
5. Run `scripts/validate.sh`
6. PR to this repo

## Relationship to OpenClaw

Skills live in `~/.openclaw/skills/` which is OpenClaw's default skill directory. The swarm-agent-kit is a curated collection — individual skills can be installed standalone or as a full kit.
