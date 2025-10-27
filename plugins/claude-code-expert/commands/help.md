---
name: help
description: Show available Claude Code agents, plugins, and commands for current project
---

# Claude Code Help Command

You are being invoked via the `/claude-code-expert:help` slash command.

## Task

Provide the user with helpful information about the Claude Code system, tailored to their current project context.

## Steps

1. **Check for project CLAUDE.md**:
   - Read `.claude/CLAUDE.md` or `CLAUDE.md` if it exists in the project
   - If exists, show project-specific priority agents and configuration
   - If doesn't exist, show general Claude Code information

2. **Display available resources**:
   - Link to INSTALLED_PLUGINS_CATALOG.md (all 65 plugins)
   - Link to PRIORITY_AGENTS.md (14 most-used agents)
   - Link to WEBSITE-PRIORITY-AGENTS.md (18 website agents)
   - Link to CREATING-AGENTS-PLUGINS.md (how to create custom agents)

3. **Show quick examples**:
   - How to ask for specific agents (e.g., "Use backend-architect to design an API")
   - How to reference skills (e.g., "Follow payment integration best practices")
   - How to create CLAUDE.md for this project

4. **List common commands**:
   - `/claude-code-expert:help` - This command
   - `/claude-code-expert:explain-routing` - Why certain agents were chosen
   - `/claude-code-expert:best-practices` - Claude Code optimization tips
   - `/claude-code-expert:create-claude-md` - Generate CLAUDE.md for this project

## Output Format

```markdown
# Claude Code Help

## Your Current Project
[If CLAUDE.md exists: Show configured agents and workflows]
[If no CLAUDE.md: Explain how to create one]

## Quick Start
**Ask Claude to use specific agents:**
- "Use backend-architect to design a REST API"
- "Have payment-integration set up Stripe checkout"
- "Get security-auditor to review this auth code"

**Reference skills automatically:**
- Skills auto-activate based on keywords
- Example: Mentioning "Stripe" activates stripe-integration skill

## Available Resources
- [INSTALLED_PLUGINS_CATALOG.md](path) - All 65 installed plugins
- [PRIORITY_AGENTS.md](path) - 14 most-used agents
- [WEBSITE-PRIORITY_AGENTS.md](path) - 18 website-focused agents
- [CREATING-AGENTS-PLUGINS.md](path) - Create custom agents

## Common Commands
- `/claude-code-expert:help` - Show this help
- `/claude-code-expert:explain-routing` - Explain agent selection
- `/claude-code-expert:best-practices` - Optimization tips
- `/claude-code-expert:create-claude-md` - Generate project CLAUDE.md

## Project Setup Recommendation
[If no CLAUDE.md]: Run `/claude-code-expert:create-claude-md` to create project-specific configuration

## Need More Help?
Ask: "How do I [specific task]?" and I'll route you to the right agents.
```

## Important Notes

- Be concise but helpful
- Tailor response to whether project has CLAUDE.md or not
- Link to actual file paths in the user's system
- Encourage creating CLAUDE.md if it doesn't exist
