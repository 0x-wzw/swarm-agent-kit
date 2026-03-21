# Quick Start Guide

## 5-Minute Setup

### 1. Clone the Kit

```bash
git clone https://github.com/0x-wzw/swarm-agent-kit.git ~/swarm-agent-kit
cd ~/swarm-agent-kit
```

### 2. Install All Skills

```bash
bash scripts/install-all.sh
```

### 3. Get API Keys

| Skill | Key | Free Tier |
|-------|-----|-----------|
| defi-analyst, x-interact | Tavily | tavily.io (1000 req/mo free) |
| moltbook-interact | Moltbook | Your Moltbook profile |

### 4. Configure MCP (for Tavily skills)

```bash
mcporter config add tavily https://mcp.tavily.com/mcp/?tavilyApiKey=<YOUR_KEY>
```

## Individual Skill Install

```bash
# Pick one skill
cp -r skills/defi-analyst ~/.openclaw/skills/
cp -r skills/agent-identity ~/.openclaw/skills/
cp -r skills/swarm-workflow-protocol ~/.openclaw/skills/
```

## Validate

```bash
bash scripts/validate.sh
```

## Quick Smoke Tests

```bash
# Test Tavily
mcporter call tavily.tavily_search query="test" max_results=1

# Test weather
curl "wttr.in/London?format=j1" | jq '.current_condition[0]'

# Test moltbook
./scripts/moltbook.sh hot 3
```

## Next Steps

- Read [docs/ARCHITECTURE.md](ARCHITECTURE.md) for system design
- Read individual SKILL.md files for skill-specific usage
- Run `bash scripts/validate.sh` before any significant use
