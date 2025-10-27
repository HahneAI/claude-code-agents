# My Custom Claude Code Plugins

**Custom Marketplace Location:** `C:\Users\antho\my-claude-plugins\`

This is a custom Claude Code plugin marketplace containing personal plugins and workflows.

## Plugins

### claude-code-expert
**Version:** 1.0.0
**Description:** Claude Code expertise, routing help, and best practices

**Agents:**
- `claude-code-expert` - Helps users understand and optimize Claude Code usage
- `agent-selector` - Intelligent task routing specialist

**Skills:**
- `doc-template-minimal` - Token-efficient documentation standards (auto-activates)
- `intent-classifier` - Agent routing logic (auto-activates)

**Commands:**
- `/claude-code-expert:help` - Show available agents and commands
- `/claude-code-expert:explain-routing` - Explain why agents were chosen
- `/claude-code-expert:best-practices` - Optimization tips
- `/claude-code-expert:create-claude-md` - Generate project-specific CLAUDE.md

## Installation

This marketplace should be automatically discovered by Claude Code if located at:
`C:\Users\antho\my-claude-plugins\`

Claude Code will scan for marketplaces and load plugins from the `.claude-plugin/marketplace.json` manifest.

## Structure

```
my-claude-plugins/
├── .claude-plugin/
│   └── marketplace.json          # Marketplace manifest
├── claude-code-expert/
│   ├── .claude-plugin/
│   │   └── plugin.json           # Plugin manifest
│   ├── agents/
│   │   ├── claude-code-expert.md
│   │   └── agent-selector.md
│   ├── commands/
│   │   ├── help.md
│   │   ├── explain-routing.md
│   │   ├── best-practices.md
│   │   └── create-claude-md.md
│   └── skills/
│       ├── doc-template-minimal/
│       │   └── SKILL.md
│       └── intent-classifier/
│           └── SKILL.md
└── README.md                      # This file
```

## Adding More Plugins

To add more plugins to this marketplace:

1. Create a new plugin directory: `mkdir my-new-plugin`
2. Create plugin manifest: `my-new-plugin/.claude-plugin/plugin.json`
3. Add plugin content: `agents/`, `commands/`, `skills/` directories
4. Register in marketplace: Add to `.claude-plugin/marketplace.json` plugins array

## Version History

- **1.0.0** (2025-10-26): Initial release of claude-code-expert plugin
  - Created claude-code-expert and agent-selector agents
  - Added doc-template-minimal and intent-classifier skills
  - Created 4 slash commands for user assistance
