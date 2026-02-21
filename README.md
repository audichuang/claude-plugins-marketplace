# claude-plugins-marketplace

Claude Code marketplace containing OpenClaw debugging tools and productivity plugins.

## Available Plugins

| Plugin | Description | Type |
|--------|-------------|------|
| [debug-openclaw](#debug-openclaw) | Debug OpenClaw session, gateway, skill, auth, and browser issues | Skill |

***

### debug-openclaw

Systematic guide for investigating OpenClaw issues. Covers session analysis, gateway startup, skill loading, model/auth errors, browser automation, and config system.

**Usage:**

Describe your OpenClaw problem — the skill triggers automatically. Or use the skill command:

```
/debug-openclaw:debug-openclaw
```

| Info | Value |
|------|-------|
| Path | [`plugins/debug-openclaw/`](plugins/debug-openclaw/) |
| Version | 1.0.0 |

***

## Installation

### Step 1: Add this marketplace

```
/plugin marketplace add audi/claude-plugins-marketplace
```

### Step 2: Install plugins

```
/plugin install debug-openclaw@audi-plugins
```

### Step 3: Restart Claude Code

## OpenClaw Compatibility

The skills in this marketplace are also compatible with OpenClaw. To use with OpenClaw, copy the skill folder to `~/.openclaw/skills/`:

```bash
cp -r plugins/debug-openclaw/skills/debug-openclaw ~/.openclaw/skills/
```

## Repository Structure

```
claude-plugins-marketplace/
├── .claude-plugin/
│   └── marketplace.json           # Marketplace metadata
├── README.md
└── plugins/
    └── debug-openclaw/            # OpenClaw debugging guide
        ├── .claude-plugin/
        │   └── plugin.json
        └── skills/debug-openclaw/
            ├── SKILL.md
            └── references/
                ├── architecture.md
                └── debug-checklist.md
```

## License

MIT
