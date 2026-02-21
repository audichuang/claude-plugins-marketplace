# claude-plugins-marketplace

Claude Code marketplace containing OpenClaw debugging tools and productivity plugins.

## Available Plugins

| Plugin | Description | Type |
|--------|-------------|------|
| [debug-openclaw](#debug-openclaw) | Debug OpenClaw session, gateway, skill, auth, and browser issues | Skill |

***

### debug-openclaw

Systematic guide for investigating OpenClaw issues. Covers session analysis, gateway startup, skill loading, model/auth errors, browser automation, and config system.

| Info | Value |
|------|-------|
| Path | [`plugins/debug-openclaw/`](plugins/debug-openclaw/) |
| Version | 1.0.0 |

***

## Installation

### Claude Code

```bash
# Add marketplace
/plugin marketplace add audichuang/claude-plugins-marketplace

# Install plugin
/plugin install debug-openclaw@audi-plugins
```

### OpenClaw

Add one line to `~/.openclaw/openclaw.json` — covers all plugins automatically:

```json5
{
  "skills": {
    "load": {
      "extraDirs": ["~/GoogleDrive/Github/skills/claude-plugins-marketplace/skills"]
    }
  }
}
```

## Repository Structure

```
claude-plugins-marketplace/
├── .claude-plugin/
│   └── marketplace.json
├── skills/                            # Shared skills (single source of truth)
│   └── debug-openclaw/
│       ├── SKILL.md
│       └── references/
└── plugins/                           # Plugin wrappers (reference shared skills)
    └── debug-openclaw/
        └── .claude-plugin/
            └── plugin.json            # skills: ["../../skills/debug-openclaw"]
```

## Adding a New Plugin

1. Add skill to `skills/<name>/SKILL.md`
2. Create `plugins/<name>/.claude-plugin/plugin.json` with `skills: ["../../skills/<name>"]`
3. Add entry to `.claude-plugin/marketplace.json`

OpenClaw picks up new skills automatically (no config change needed).

## License

MIT
