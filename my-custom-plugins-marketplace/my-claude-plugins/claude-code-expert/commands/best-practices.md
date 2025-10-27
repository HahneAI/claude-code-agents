---
name: best-practices
description: Show Claude Code optimization tips and best practices
---

# Claude Code Best Practices Command

You are being invoked via the `/claude-code-expert:best-practices` slash command.

## Task

Provide actionable best practices for optimizing Claude Code usage in the user's current project.

## Steps

1. **Assess current setup**:
   - Check if project has CLAUDE.md
   - Look at recent conversation for usage patterns
   - Identify potential optimizations

2. **Provide tailored recommendations**:
   - Project-specific suggestions based on tech stack
   - Common optimizations for their type of work
   - Tips for their team size (solo vs team)

3. **Reference resources**:
   - Link to relevant documentation
   - Show examples from priority agents
   - Point to skills that could help

## Output Format

```markdown
# Claude Code Best Practices

## Quick Wins

### 1. Create Project CLAUDE.md
[If doesn't exist]
**Impact:** High | **Effort:** 15 minutes

A project-specific CLAUDE.md file:
- Documents your tech stack and architecture
- Defines priority agents for your project
- Adds custom triggers for better routing
- Helps team members understand configuration

**Action:** Run `/claude-code-expert:create-claude-md`

### 2. Use Specific Agent Requests
**Impact:** Medium | **Effort:** Immediate

Instead of: "Create an API endpoint"
Better: "Use backend-architect to design a REST API for quotes"

Why: Explicit agent selection ensures optimal routing

### 3. Leverage Skills Auto-Activation
**Impact:** Medium | **Effort:** None (automatic)

Skills activate based on keywords:
- Mention "Stripe" → stripe-integration skill loads
- Mention "TypeScript" → typescript-advanced-types activates
- Mention "test" → testing-pattern skills activate

**Tip:** Know which skills exist (see INSTALLED_PLUGINS_CATALOG.md)

### 4. Always Include Test Automation
**Impact:** High | **Effort:** Mention in request

For business logic, always add:
"...and have test-automator generate comprehensive tests"

Critical for:
- Pricing calculations
- Payment processing
- Authentication logic
- Data validation

### 5. Security Reviews for Critical Code
**Impact:** Critical | **Effort:** Mention in request

Always include security-auditor for:
- Payment integrations
- Authentication/authorization
- RLS policies
- Sensitive data handling

**Pattern:** "...then have security-auditor review for vulnerabilities"

## Project-Specific Recommendations

[Analyze project context and provide 2-3 tailored suggestions]

## Token Optimization

### Use doc-template-minimal Standards
When documenting code, follow token-efficient patterns:
- Functions: Max 3 sentences
- API endpoints: Max 200 tokens
- README files: Max 500 tokens

**Benefit:** Reduces token usage by 50-90%

### Prefer Specialized Agents
- payment-integration (not backend-architect) for Stripe
- database-optimizer (not backend-architect) for query performance
- typescript-pro (not frontend-developer) for complex types

**Benefit:** Specialized agents have relevant skills pre-loaded

## Multi-Agent Workflows

### When to Use Multi-Agent
- Cross-domain tasks (frontend + backend)
- Security-critical features (threat model → implement → review)
- Complex architecture (design → implement → test → review)

### When to Stick to Single Agent
- Simple components
- Straightforward bug fixes
- Single-domain tasks

**Guideline:** Don't over-engineer simple requests

## Team Collaboration

### Version Control CLAUDE.md
If working in a team:
- Commit CLAUDE.md to repository
- Document team conventions
- Share custom agent triggers
- Keep priority agents updated

### Document Agent Decisions
In pull requests, mention:
- Which agents were used
- Why specific agents were chosen
- Any custom workflows followed

## Resources

- [INSTALLED_PLUGINS_CATALOG.md] - All 65 plugins
- [PRIORITY_AGENTS.md] - 14 most-used agents
- [CREATING-AGENTS-PLUGINS.md] - Create custom agents
- [doc-template-minimal skill] - Documentation standards
- [intent-classifier skill] - Routing logic

## Common Mistakes to Avoid

1. ❌ Not creating project CLAUDE.md
2. ❌ Using general agents when specialists exist
3. ❌ Forgetting to include test-automator for business logic
4. ❌ Skipping security-auditor for payment/auth code
5. ❌ Over-verbose documentation (wastes tokens)
6. ❌ Unclear agent requests ("do something" vs "use X to do Y")

## Next Steps

1. Run `/claude-code-expert:create-claude-md` if you haven't
2. Review [PRIORITY_AGENTS.md] for your tech stack
3. Ask specific questions: "How do I optimize [specific scenario]?"
```

## Important Notes

- Tailor recommendations to their actual project
- Be specific and actionable
- Provide examples they can use immediately
- Reference skills and documentation
- Encourage best practices without overwhelming
