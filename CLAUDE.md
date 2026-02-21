# Claude Plugins Marketplace

## 項目結構

這是一個 Claude Code plugin marketplace repo，同時相容 OpenClaw。

```
audi-plugins/
├── .claude-plugin/marketplace.json    # Marketplace 註冊表
├── skills/                            # 所有 skill 的唯一真相來源（共享）
│   └── <skill-name>/
│       ├── SKILL.md                   # Skill 定義（frontmatter + 內容）
│       └── references/                # 參考文件（可選）
└── plugins/                           # Plugin 薄殼（只引用 skills/）
    └── <plugin-name>/
        └── .claude-plugin/
            └── plugin.json            # skills: ["../../skills/<name>"]
```

## 設計原則

1. **`skills/` 是唯一真相來源** — 所有 SKILL.md 只存在這裡，不重複
2. **`plugins/` 只是引用殼** — 透過 `../../skills/<name>` 相對路徑引用
3. **雙平台相容**：
   * Claude Code：走 plugin 系統（`.claude-plugin/plugin.json`）
   * OpenClaw：走 `extraDirs` 指向 `skills/` 目錄

## 新增 Plugin 的步驟

1. 在 `skills/<name>/` 放入 `SKILL.md`（含標準 `---` frontmatter）
2. 建立 `plugins/<name>/.claude-plugin/plugin.json`，`skills` 欄位用 `["../../skills/<name>"]`
3. 在 `.claude-plugin/marketplace.json` 的 `plugins` 陣列加入新 entry
4. Commit & push

## SKILL.md 格式

```markdown
---
name: skill-name
description: 觸發描述，讓 AI 知道何時使用此 skill
---

# Skill 標題

Skill 內容...
```

* `name`：小寫 + 數字 + 連字號，≤64 字元
* `description`：≤1024 字元
* 檔案大小：≤256KB
