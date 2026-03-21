---
name: swarm-agent-kit
description: Production-ready agent skills for autonomous finance, swarm orchestration, and DeFi research. This is the master skill that orchestrates all sub-skills. Install all or individual skills via the scripts/install-all.sh or by copying specific skill directories to your OpenClaw skills folder.
---

# Swarm Agent Kit

The master skill for the 0x-wzw agent swarm. Installs, manages, and coordinates all sub-skills.

## Sub-Skills

| Category | Skill | What It Does |
|----------|-------|-------------|
| **Orchestration** | `swarm-workflow-protocol` | Multi-agent spawn logic, relay communication, task routing |
| **Finance** | `defi-analyst` | DeFi research via Tavily + GeckoTerminal + DeFiLlama |
| **Finance** | `agent-identity` | ERC-8004 identity registration and reputation |
| **Social** | `x-interact` | X.com search and content via Tavily MCP |
| **Social** | `moltbook-interact` | Moltbook posts, replies, feed browsing |
| **Discovery** | `find-skills` | Search ClawHub for installable skills |
| **Utility** | `weather` | Current conditions + forecasts |
| **Utility** | `video-frames` | FFmpeg frame extraction and clip creation |
| **Security** | `healthcheck` | Host hardening and risk assessment |
| **Tooling** | `mcporter` | MCP server config and tool calling |
| **Tooling** | `clawhub` | ClawHub CLI for skill management |
| **Tooling** | `node-connect` | Device pairing diagnostics |
| **Tooling** | `tmux` | Tmux session control |
| **Tooling** | `skill-creator` | Author new skills from templates |

## Installation

### Full Kit

```bash
git clone https://github.com/0x-wzw/swarm-agent-kit.git ~/swarm-agent-kit
cd ~/swarm-agent-kit
bash scripts/install-all.sh
```

### Individual Skill

```bash
cp -r skills/defi-analyst ~/.openclaw/skills/
```

## Configuration

Each skill has its own prerequisites (API keys, tools). Check the skill's SKILL.md for details. Common keys needed:

| Key | Skill | Get It |
|-----|-------|--------|
| `TAVILY_API_KEY` | defi-analyst, x-interact | tavily.io (free tier) |
| `OPENAI_API_KEY` | mcporter (optional) | OpenAI platform |
| Moltbook credentials | moltbook-interact | Moltbook profile |

## Architecture

```
swarm-agent-kit/
├── SKILL.md              ← You are here (master)
├── skills/               ← All sub-skills
├── scripts/
│   ├── install-all.sh    ← One-command install
│   └── validate.sh        ← Validates all SKILL.md files
└── docs/
    ├── QUICKSTART.md
    └── ARCHITECTURE.md
```

## Validation

```bash
bash scripts/validate.sh
```

Checks every skill has a valid SKILL.md (name + description + body), scripts are executable, and docs are present.

## Adding Skills

1. Author a SKILL.md following the AgentSkills spec
2. Place it under `skills/your-skill/`
3. Add to `scripts/install-all.sh`
4. Run validation

See `skills/skill-creator/SKILL.md` for the authoring guide.
