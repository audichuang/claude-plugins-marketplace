# audi-plugins

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
/plugin marketplace add audichuang/audi-plugins

# Install plugin
/plugin install debug-openclaw@audi-plugins
```

### OpenClaw

Add one line to your OpenClaw config — covers all plugins automatically:

```json5
{
  "skills": {
    "load": {
      "extraDirs": ["~/GoogleDrive/Github/skills/audi-plugins/skills"]
    }
  }
}
```

## Repository Structure

```
audi-plugins/
├── .claude-plugin/
│   └── marketplace.json
├── skills/                            # Symlinks for OpenClaw (extraDirs → here)
│   └── debug-openclaw -> ../plugins/debug-openclaw/skills/debug-openclaw
├── plugins/                           # Plugin packages (Claude Code reads here)
│   └── debug-openclaw/
│       ├── .claude-plugin/plugin.json
│       └── skills/debug-openclaw/     # Actual skill files (source of truth)
│           ├── SKILL.md
│           └── references/
├── CLAUDE.md
├── GEMINI.md
└── AGENTS.md
```

## Adding a New Plugin

1. Create `plugins/<name>/skills/<name>/SKILL.md`
2. Create `plugins/<name>/.claude-plugin/plugin.json` with `skills: ["./skills/<name>"]`
3. Add symlink: `cd skills && ln -s ../plugins/<name>/skills/<name> <name>`
4. Add entry to `.claude-plugin/marketplace.json`

OpenClaw picks up new skills automatically via the symlink — no config change needed.

## License

MIT
