# Swarm Agent Kit

**Production-ready agent skills for autonomous finance, swarm orchestration, and DeFi research.**

Built for the 0x-wzw multi-agent swarm. Each skill is self-contained, transferable, and designed to work with [OpenClaw](https://github.com/openclawai/openclaw).

---

## What's Inside

| Skill | Description |
|-------|-------------|
| `swarm-workflow-protocol` | Multi-agent orchestration, spawn logic, relay communication |
| `defi-analyst` | DeFi research via Tavily + GeckoTerminal + DeFiLlama |
| `agent-identity` | ERC-8004 agent identity management |
| `x-interact` | X.com content via Tavily MCP |
| `moltbook-interact` | Moltbook social network engagement |
| `find-skills` | Discover skills on ClawHub |
| `weather` | Weather forecasts via wttr.in / Open-Meteo |
| `video-frames` | FFmpeg frame extraction |
| `healthcheck` | Host security hardening |
| `mcporter` | MCP server management |
| `clawhub` | ClawHub CLI skill management |
| `node-connect` | Device pairing diagnostics |
| `tmux` | Tmux session control |
| `skill-creator` | Author new skills |

---

## Prerequisites

- **OpenClaw** — [Install guide](https://docs.openclaw.ai/getting-started)
- **Node.js 18+** — For skill scripts
- **API Keys** (per skill — see individual SKILL.md)
- **Git** — For clone/push operations

---

## Quick Start

### Install All Skills

```bash
git clone https://github.com/0x-wzw/swarm-agent-kit.git ~/swarm-agent-kit
cd ~/swarm-agent-kit
bash scripts/install-all.sh
```

### Install One Skill

```bash
# Clone the kit
git clone https://github.com/0x-wzw/swarm-agent-kit.git ~/swarm-agent-kit

# Copy a specific skill to your OpenClaw skills directory
cp -r ~/swarm-agent-kit/skills/defi-analyst ~/.openclaw/skills/
```

### Validate All Skills

```bash
bash scripts/validate.sh
```

---

## Skill Structure

Every skill follows the AgentSkills spec:

```
skill-name/
├── SKILL.md          # The skill definition (name, description, body)
├── scripts/          # Optional helper scripts
├── references/       # Optional docs, API refs, templates
└── _meta.json        # Optional metadata (version, author, tags)
```

---

## Architecture

See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) for deep dive.

Quick summary:
- **Master SKILL.md** — top-level orchestrator; delegates to sub-skills
- **Sub-skills** — each self-contained, can run independently
- **Scripts** — shared install/validate tooling
- **Docs** — user-facing guides

---

## Adding a New Skill

See `skills/skill-creator/SKILL.md` for the full authoring guide. Key steps:

1. Create `skills/your-skill/SKILL.md` — follow the AgentSkills spec
2. Add `scripts/your-skill.sh` if CLI tooling is needed
3. Document prerequisites and config in SKILL.md
4. Test: `bash scripts/validate.sh`
5. PR to this repo

---

## License

MIT — use freely, credit appreciated.
