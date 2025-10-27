---
name: create-claude-md
description: Generate a project-specific CLAUDE.md file based on project context
---

# Create CLAUDE.md Command

You are being invoked via the `/claude-code-expert:create-claude-md` slash command.

## Task

Generate a tailored CLAUDE.md file for the user's current project.

## Steps

1. **Gather project information**:
   - Ask about project type (web app, API, mobile, data pipeline, etc.)
   - Identify tech stack (React, Python, Rust, PostgreSQL, etc.)
   - Understand team context (solo dev, small team, enterprise)
   - Determine key concerns (security, performance, documentation, testing)

2. **Analyze existing files** (if available):
   - Check package.json, requirements.txt, Cargo.toml, etc.
   - Look at project structure
   - Identify frameworks and dependencies

3. **Select appropriate template**:
   - **Minimal**: Solo dev, simple project, getting started
   - **Standard**: Most projects, balanced detail
   - **Comprehensive**: Team project, complex system, enterprise needs

4. **Generate CLAUDE.md** with sections:
   - ⚠️ Safety notice (project-level scope)
   - 📍 Project context (description, tech stack, architecture)
   - 🎯 Priority agents (tailored to their tech stack)
   - 🛠️ Available MCP servers (if configured)
   - 📋 Workflow guidelines (project-specific conventions)
   - 📝 Documentation standards (reference doc-template-minimal)
   - 🔗 Resources (design systems, APIs, docs)

5. **Explain the file**:
   - Why each section matters
   - How Claude uses it
   - How to customize further

## Template Selection Logic

### Minimal Template (Solo Dev / Simple Project)
```markdown
# CLAUDE.md - Project Configuration

## ⚠️ Project-Level Configuration
This CLAUDE.md affects only this project, not global Claude Code behavior.

## 📍 Project Context
**Project**: [Name] - [One sentence description]
**Tech Stack**: [Key technologies]
**Architecture**: [High-level architecture]

## 🎯 Priority Agents
1. **[agent-name]** (`[plugin]`) - [when to use]
2. **[agent-name]** (`[plugin]`) - [when to use]
3. **[agent-name]** (`[plugin]`) - [when to use]

## 📋 Quick Workflow Guide
- [Key convention 1]
- [Key convention 2]

## 📝 Documentation
Follow token-efficient standards (see doc-template-minimal skill).

## 🔗 Resources
- [Link to key resource]
```

### Standard Template (Most Projects)
```markdown
# CLAUDE.md - [Project Name] Configuration

## ⚠️ Project-Level Configuration
This CLAUDE.md affects only this project, not global Claude Code behavior.

## 📍 Project Context
**Project**: [Detailed description]
**Tech Stack**: [Comprehensive list]
**Architecture**: [Architecture patterns in use]
**Key Concerns**: [Security, Performance, etc.]

## 🎯 Priority Agents for This Project

### Backend
- **backend-architect** (`backend-development`) - API design, service architecture
- **[tech-specific agent]** - Implementation

### Frontend
- **frontend-developer** (`frontend-mobile-development`) - React components, UI
- **ui-ux-designer** (`multi-platform-apps`) - Design patterns

### Database
- **database-optimizer** (`database-cloud-optimization`) - Query performance, schema

### Testing & Quality
- **test-automator** (`unit-testing`) - Test generation
- **code-reviewer** (`comprehensive-review`) - Code quality

### [Project-Specific Category]
- **[specialized agent]** - [when to use]

## 🎨 Project-Specific Triggers

### Payment Processing
Auto-invoke **payment-integration** when:
- Working with Stripe/PayPal integration
- Implementing checkout flows
- Handling webhooks or subscriptions

**ALWAYS include:** security-auditor for payment code review

### [Other Custom Triggers]
[Define project-specific agent triggers]

## 🛠️ Available MCP Servers
[If applicable, list configured MCP servers]

**PostgreSQL** (Supabase):
- Direct read-only access to production database
- Use database-optimizer to query and analyze schema
- All database work should query live DB first

## 📋 Workflow Guidelines

### Before Making Changes
1. Read existing code first
2. Check git status to know current state
3. Understand the impact area

### During Development
- **Testing**: Always include test-automator for business logic
- **Security**: Include security-auditor for auth/payment/sensitive data
- **Documentation**: Follow doc-template-minimal standards (token-efficient)

### Git Workflow
- Commit frequently with clear messages
- Reference related issues/PRs
- Include agent names in commits when relevant

## 📝 Documentation Standards
Follow **doc-template-minimal** skill guidelines:
- Functions: Max 3 sentences
- API endpoints: Max 200 tokens
- README: Max 500 tokens
- Focus on "why" not "what"

## 🔐 Security Guidelines
[If applicable: project-specific security requirements]

## 🧪 Testing Strategy
- **Unit Tests**: For all business logic
- **Integration Tests**: For API endpoints
- **E2E Tests**: For critical user flows
- **Performance Tests**: For high-traffic endpoints

## 🔗 Resources
- [Design system URL]
- [API documentation]
- [Architecture docs]
- [Team conventions]
```

### Comprehensive Template (Team / Enterprise)
[Include everything from Standard, plus:]
- Team collaboration guidelines
- Custom slash command definitions
- Detailed agent workflow orchestration
- Compliance and audit requirements
- Multi-environment considerations

## Output Format

After generating CLAUDE.md:

```markdown
# CLAUDE.md Created Successfully!

I've created a [Minimal/Standard/Comprehensive] CLAUDE.md file for your [project type] project.

## What I Included

✅ **Project Context**: [Summary of what was documented]
✅ **Priority Agents**: [List of key agents configured]
✅ **Workflow Guidelines**: [Key conventions]
✅ **[Other sections]**

## Key Sections Explained

### 🎯 Priority Agents
These are the agents most relevant to your [tech stack]. They'll be referenced first when Claude analyzes tasks.

### 🎨 Project-Specific Triggers
Custom rules for when specific agents should activate. You can add more as patterns emerge.

### 📋 Workflow Guidelines
Project-specific conventions that all agents should follow.

## Next Steps

1. **Review the file**: Make sure it matches your project needs
2. **Customize**: Add project-specific details, resources, conventions
3. **Commit to git**: Share with your team (if applicable)
4. **Update as needed**: Keep priority agents current as project evolves

## Customization Ideas

- Add more project-specific agent triggers
- Document team coding standards
- Link to your design system or style guide
- Add MCP server configurations
- Define multi-agent workflows for common tasks

## How Claude Uses This

- **Agent Selection**: Consults priority agents when routing tasks
- **Behavior**: Follows workflow guidelines and documentation standards
- **Context**: Uses project description to understand domain
- **Resources**: References links you've provided

## Questions?

Ask me: "How do I [customize specific aspect]?" for guidance.
```

## Important Notes

- **Safety**: Always include warning about project-level vs global scope
- **Tailoring**: Match template complexity to project needs
- **Tech Stack**: Select agents that match their actual technologies
- **Actionable**: Make it immediately useful, not just documentation
- **Extensible**: Explain how to customize further
- **Examples**: Use their actual project name and technologies
