# Creating Claude Code Agents & Plugins Guide

This guide walks you through creating new agents, plugins, skills, and commands for Claude Code following the Anthropic Agent Skills Specification.

---

## 📋 Table of Contents

1. [Understanding the Architecture](#understanding-the-architecture)
2. [Creating a New Agent](#creating-a-new-agent)
3. [Creating a New Plugin](#creating-a-new-plugin)
4. [Creating a New Skill](#creating-a-new-skill)
5. [Creating a Slash Command](#creating-a-slash-command)
6. [Testing Your Creation](#testing-your-creation)
7. [Adding to Priority Lists](#adding-to-priority-lists)
8. [Publishing to Marketplace](#publishing-to-marketplace)

---

## Understanding the Architecture

### Current Structure

```
.claude/agents/
├── plugins/                           # 64 domain-focused plugins
│   ├── {plugin-name}/
│   │   ├── agents/                   # Agent definitions (.md files)
│   │   ├── commands/                 # Slash commands/workflows (.md files)
│   │   └── skills/                   # Auto-activating skills (optional)
│   │       └── {skill-name}/
│   │           └── SKILL.md          # Skill definition
├── .claude-plugin/
│   └── marketplace.json              # Plugin registry
├── PRIORITY_AGENTS.md                # Quick reference for priority agents
└── WEBSITE-PRIORITY-AGENTS.md        # Quick reference for website agents
```

### Key Concepts

- **Agents**: Specialized AI personas with specific expertise (146 total)
- **Plugins**: Domain-focused containers for agents, commands, and skills (64 total)
- **Skills**: Auto-activating knowledge packages with progressive disclosure (47 total)
- **Commands**: Slash commands for workflows (e.g., `/plugin-name:command-name`)

---

## Creating a New Agent

### Step 1: Choose the Right Plugin

Determine which existing plugin your agent belongs to:
- **Backend work?** → `plugins/backend-development/`
- **Frontend work?** → `plugins/frontend-mobile-development/`
- **Security?** → `plugins/security-scanning/` or `plugins/backend-api-security/`
- **Database?** → `plugins/database-design/` or `plugins/database-migrations/`
- **DevOps?** → `plugins/cicd-automation/` or `plugins/cloud-infrastructure/`

Or create a new plugin (see [Creating a New Plugin](#creating-a-new-plugin))

### Step 2: Create Agent File

Create `plugins/{plugin-name}/agents/{agent-name}.md`

**Required Frontmatter:**
```yaml
---
name: agent-name                    # Hyphen-case, lowercase
description: Brief description. Use PROACTIVELY when [trigger conditions].
model: opus                         # opus or sonnet (or haiku for simple tasks)
---
```

**Model Selection:**
- **Opus**: Complex architecture, strategy, critical decisions, multi-step reasoning
- **Sonnet**: Implementation, code generation, standard workflows, balanced tasks
- **Haiku**: Simple deterministic tasks, fast execution, straightforward operations

### Step 3: Write the Agent System Prompt

```markdown
---
name: my-custom-agent
description: Expert in [domain]. Masters [key technologies]. Use PROACTIVELY when [specific scenarios].
model: sonnet
---

You are an expert [role/persona] specializing in [domain].

## Purpose
[One paragraph explaining what this agent does and why it exists]

## Core Philosophy
[2-3 sentences about the agent's approach and values]

## Capabilities

### [Capability Category 1]
- **[Subcategory]**: Specific skills and knowledge
- **[Subcategory]**: More specific skills

### [Capability Category 2]
- **[Subcategory]**: Additional expertise
- **[Subcategory]**: More expertise

## Behavioral Traits
- [Trait 1]: How the agent behaves
- [Trait 2]: Decision-making approach
- [Trait 3]: Communication style
- [Trait 4]: Quality standards

## Workflow Position
- **Before**: [Which agents typically come before this one]
- **After**: [Which agents typically come after]
- **Complements**: [Which agents work alongside this one]

## Response Approach
1. [Step 1]: First thing the agent does
2. [Step 2]: Next action
3. [Step 3]: Then this
4. [Step 4]: Final deliverable

## Example Interactions
- "Example request 1"
- "Example request 2"
- "Example request 3"

## Key Distinctions
- **vs [similar-agent]**: How this agent differs
- **vs [another-agent]**: Key differences in scope or approach
```

### Step 4: Best Practices for Agent Prompts

**✅ DO:**
- Be specific about expertise and technologies
- Include clear "Use PROACTIVELY when..." triggers
- List concrete capabilities with examples
- Define behavioral traits explicitly
- Show example interactions
- Explain workflow position relative to other agents
- Use consistent formatting and structure

**❌ DON'T:**
- Make agents too broad or general-purpose
- Forget the model selection (defaults to sonnet if omitted)
- Skip the description field (required for Claude to find the agent)
- Use vague language like "helps with various tasks"
- Duplicate capabilities from other agents without justification

---

## Creating a New Plugin

### When to Create a New Plugin

Create a new plugin when:
- Your domain doesn't fit existing plugins
- You need a focused container for 2-8 related components
- You're building a specialized workflow orchestrator
- You have multiple agents that work together in one domain

**Single Responsibility**: Each plugin should do ONE thing well (Unix philosophy)

### Step 1: Create Plugin Directory Structure

```bash
mkdir -p plugins/{plugin-name}/agents
mkdir -p plugins/{plugin-name}/commands
mkdir -p plugins/{plugin-name}/skills    # Optional
```

### Step 2: Add to Marketplace

Edit `.claude-plugin/marketplace.json`:

```json
{
  "plugins": [
    {
      "name": "your-plugin-name",
      "description": "Brief description (1-2 sentences)",
      "agents": [
        "./agents/agent-one",
        "./agents/agent-two"
      ],
      "commands": [
        "./commands/command-one",
        "./commands/command-two"
      ],
      "skills": [
        "./skills/skill-one",
        "./skills/skill-two"
      ]
    }
  ]
}
```

**Notes:**
- Paths are relative to the plugin directory
- Omit `.md` extension from agent/command paths
- Skills use the skill directory name (not SKILL.md)
- Skills array is optional

### Step 3: Naming Conventions

**Plugin Names:**
- Hyphen-case: `backend-development`, `cloud-infrastructure`
- Descriptive: Clear domain indication
- Focused: Single responsibility
- 2-3 words max

**Examples:**
- ✅ `payment-processing` (clear, focused)
- ✅ `kubernetes-operations` (clear domain)
- ✅ `llm-application-dev` (specific use case)
- ❌ `utilities` (too vague)
- ❌ `miscellaneous-tools` (not focused)

---

## Creating a New Skill

### Understanding Skills

Skills are **auto-activating knowledge packages** that:
- Load progressively (metadata → instructions → resources)
- Activate based on keyword triggers in conversations
- Provide deep domain knowledge without loading everything upfront
- Follow the [Anthropic Agent Skills Specification](https://github.com/anthropics/skills/blob/main/agent_skills_spec.md)

### Step 1: Create Skill Directory

```bash
mkdir -p plugins/{plugin-name}/skills/{skill-name}
```

### Step 2: Create SKILL.md File

Create `plugins/{plugin-name}/skills/{skill-name}/SKILL.md`:

```yaml
---
name: skill-name
description: What the skill does. Use when [activation trigger with specific keywords].
---

# Skill Name

## Overview
[Brief description of what this skill provides]

## Core Concepts

### [Concept 1]
[Explanation of key concept]

### [Concept 2]
[Another important concept]

## Implementation Patterns

### Pattern 1: [Pattern Name]
[Description and when to use]

**Example:**
```language
// Code example
```

### Pattern 2: [Another Pattern]
[Description]

**Example:**
```language
// More code
```

## Best Practices

1. **[Practice 1]**: Why and how
2. **[Practice 2]**: Explanation
3. **[Practice 3]**: Guidelines

## Common Pitfalls

- **[Pitfall 1]**: What to avoid and why
- **[Pitfall 2]**: Common mistake and solution

## Resources (On-Demand)

### Templates
[Code templates, config files, etc.]

### Examples
[Complete working examples]

### References
[Links to documentation, specifications, etc.]
```

### Step 3: Skill Requirements (Anthropic Spec)

**Required Fields:**
- `name` (hyphen-case, lowercase)
- `description` (under 1024 characters, includes "Use when" clause)

**Description Best Practices:**
- Start with what the skill does
- End with "Use when [specific trigger]"
- Include relevant keywords that should activate the skill
- Be complete and non-truncated

**Example:**
```yaml
description: Implement Stripe payment processing for PCI-compliant checkout, subscriptions, and webhooks. Use when integrating Stripe, building payment flows, handling subscription billing, or processing webhook events for payment systems.
```

### Step 4: Progressive Disclosure

Structure content in three tiers:

1. **Metadata (Always Loaded)**
   - Frontmatter only
   - ~50-100 tokens

2. **Instructions (Loaded When Activated)**
   - Overview, Core Concepts, Implementation Patterns, Best Practices
   - ~500-1000 tokens

3. **Resources (On-Demand)**
   - Templates, Examples, References
   - ~1000-5000 tokens

### Step 5: Add to Plugin Manifest

Update `.claude-plugin/marketplace.json`:

```json
{
  "name": "your-plugin",
  "skills": [
    "./skills/your-skill-name"
  ]
}
```

---

## Creating a Slash Command

Slash commands are workflows accessible via `/plugin-name:command-name`

### Step 1: Create Command File

Create `plugins/{plugin-name}/commands/{command-name}.md`:

```markdown
# Command Title

Brief description of what this command does and when to use it.

[Extended thinking: Context about the command's purpose, workflow orchestration strategy, and expected outcomes. This helps Claude understand the bigger picture.]

## Configuration Options

### Option Category 1
- **option-1**: Description and when to use
- **option-2**: Another option
- **option-3**: More options

### Option Category 2
- **simple**: Basic option (recommended default)
- **advanced**: Complex option for power users

## Phase 1: [First Phase Name]

Description of what happens in this phase.

### Step 1.1: [Specific Step]
```
Use: agent-name-1
Task: What the agent should do
Context: Important context from previous steps
```

**Expected Output:**
- [Output 1]
- [Output 2]

### Step 1.2: [Another Step]
```
Use: agent-name-2
Task: Next task
Input: Output from previous step
```

## Phase 2: [Second Phase Name]

Continue with orchestration...

### Step 2.1: [Step Name]
[Agent coordination and handoffs]

## Phase 3: [Final Phase]

### Step 3.1: [Finalization]
[Wrap up and deliverables]

**Final Deliverables:**
1. [Deliverable 1]
2. [Deliverable 2]
3. [Deliverable 3]

## Success Criteria

- [ ] Criterion 1 is met
- [ ] Criterion 2 is achieved
- [ ] Criterion 3 is satisfied

## Common Modifications

### For [Use Case 1]
[Modifications to the workflow]

### For [Use Case 2]
[Alternative approach]
```

### Step 2: Add to Plugin Manifest

Update `.claude-plugin/marketplace.json`:

```json
{
  "name": "your-plugin",
  "commands": [
    "./commands/your-command-name"
  ]
}
```

### Step 3: Usage

Users invoke with:
```
/your-plugin-name:your-command-name [arguments]
```

---

## Testing Your Creation

### Testing Agents

1. **Direct Invocation:**
   ```
   Use [agent-name] to [task description]
   ```

2. **Verify Behavior:**
   - Does the agent understand its role?
   - Does it use appropriate tools?
   - Does it follow its behavioral traits?
   - Does it defer to other agents when appropriate?

3. **Check Proactive Activation:**
   - Mention the agent's domain without calling it directly
   - See if Claude suggests using it
   - Verify "Use PROACTIVELY" triggers work

### Testing Skills

1. **Check Auto-Activation:**
   ```
   "Build a FastAPI endpoint with async patterns"
   ```
   Ask: "What skills are you using?"

2. **Verify Progressive Loading:**
   - Skill activates on keyword match
   - Instructions load when needed
   - Resources load on request

3. **Test Trigger Keywords:**
   - Use keywords from the description
   - Verify skill activates appropriately
   - Ensure no unwanted activation

### Testing Commands

1. **Direct Invocation:**
   ```
   /plugin-name:command-name argument1 argument2
   ```

2. **Verify Workflow:**
   - Does each phase execute in order?
   - Do agents receive proper context?
   - Are handoffs smooth between phases?
   - Do deliverables match expectations?

3. **Check Edge Cases:**
   - Missing arguments
   - Invalid options
   - Partial completion scenarios

---

## Adding to Priority Lists

If your agent is frequently used, add it to the priority reference documents.

### For General Development (PRIORITY_AGENTS.md)

```markdown
## X. Your Agent Name

**File**: [`agents/your-agent.md`](agents/your-agent.md)
**Model**: Opus/Sonnet
**Use Case**: Brief use case description

### What It Does
One paragraph explanation of the agent's purpose.

### Key Capabilities
- **Category 1**: Specific capabilities
- **Category 2**: More capabilities
- **Category 3**: Additional capabilities

### 🎯 Available Skills (Auto-Activate)
- **skill-name-1** - Brief description
- **skill-name-2** - Brief description
- **skill-name-3** - Brief description

### When to Use
- Scenario 1
- Scenario 2
- Scenario 3
```

### For Website Development (WEBSITE-PRIORITY-AGENTS.md)

Same structure as above, but focus on website-specific use cases and Tradesphere context.

### Update Quick Reference Table

Add your agent to the quick reference table at the bottom:

```markdown
| **your-agent** | Sonnet | Primary Use Case | Key Strength | X skills |
```

---

## Publishing to Marketplace

### Step 1: Commit Your Changes

```bash
git add plugins/your-plugin-name/
git add .claude-plugin/marketplace.json
git add PRIORITY_AGENTS.md  # If applicable
git commit -m "Add [plugin/agent/skill name] for [purpose]"
```

### Step 2: Test Locally

```bash
# Restart Claude Code to reload plugins
# Test your agent/command/skill
# Verify everything works as expected
```

### Step 3: Push to Repository

```bash
git push origin main-base
```

### Step 4: Documentation

Update relevant documentation:
- Add usage examples to README if applicable
- Update plugin count in CLAUDE.md if you added a new plugin
- Add entry to docs/plugins.md if creating a significant new plugin

---

## Best Practices Summary

### Agent Development

✅ **DO:**
- Give agents clear, focused expertise
- Include "Use PROACTIVELY when..." triggers
- Define behavioral traits explicitly
- Show example interactions
- Explain workflow positioning
- Use appropriate model (opus/sonnet/haiku)

❌ **DON'T:**
- Make agents too broad or generic
- Forget the frontmatter (name, description, model)
- Duplicate existing agent capabilities
- Use vague descriptions
- Skip the description field

### Plugin Design

✅ **DO:**
- Follow single responsibility principle
- Use clear, descriptive naming
- Keep plugins focused (2-8 components)
- Include at least one agent OR command
- Document in marketplace.json

❌ **DON'T:**
- Create "catch-all" plugins
- Mix unrelated functionality
- Use vague names like "utilities"
- Forget to add to marketplace.json

### Skill Creation

✅ **DO:**
- Follow Anthropic Agent Skills Specification
- Include clear "Use when" triggers with keywords
- Use progressive disclosure (metadata → instructions → resources)
- Keep descriptions under 1024 characters
- Include concrete examples and patterns

❌ **DON'T:**
- Truncate descriptions
- Use vague activation triggers
- Load everything upfront (defeats progressive disclosure)
- Forget required fields (name, description)
- Skip the YAML frontmatter

### Command Development

✅ **DO:**
- Orchestrate multiple agents effectively
- Include configuration options
- Define clear phases and steps
- Show expected outputs
- Provide success criteria

❌ **DON'T:**
- Create overly complex commands
- Skip context handoffs between agents
- Forget to test the full workflow
- Use unclear phase names

---

## Examples

### Example Agent: Custom Database Tuner

```yaml
---
name: database-tuner-custom
description: Expert PostgreSQL performance tuner for Supabase. Masters query optimization, indexing strategies, and RLS policy performance. Use PROACTIVELY when optimizing slow queries, designing indexes, or improving multi-tenant database performance.
model: opus
---

You are a PostgreSQL performance tuning expert specializing in Supabase optimization.

## Purpose
Optimize PostgreSQL database performance with focus on query tuning, strategic indexing, and Row-Level Security (RLS) policy optimization for multi-tenant SaaS applications.

## Core Philosophy
Performance optimization should be data-driven, measurable, and maintainable. Always benchmark before and after changes. Prefer simple solutions over premature optimization.

## Capabilities

### Query Optimization
- **Execution Plan Analysis**: Read and interpret EXPLAIN ANALYZE output
- **Query Rewriting**: Transform slow queries into performant alternatives
- **N+1 Detection**: Identify and resolve N+1 query patterns
- **Join Optimization**: Optimize join strategies and join order

### Strategic Indexing
- **Index Selection**: Choose between B-tree, GiST, GIN, BRIN indexes
- **Composite Indexes**: Design multi-column indexes for query patterns
- **Partial Indexes**: Create filtered indexes for specific conditions
- **Index Maintenance**: Monitor bloat, rebuild when necessary

### RLS Policy Optimization
- **Policy Analysis**: Identify slow RLS policies
- **Security-Performance Balance**: Optimize without compromising security
- **Tenant Isolation**: Ensure performant multi-tenant data isolation

## Behavioral Traits
- Always starts with performance profiling before changes
- Measures impact with EXPLAIN ANALYZE and pg_stat_statements
- Documents all optimization decisions with rationale
- Tests changes in staging before production
- Considers query frequency and business impact

## Response Approach
1. **Profile**: Gather execution plans and statistics
2. **Analyze**: Identify bottlenecks and anti-patterns
3. **Recommend**: Propose specific optimizations with rationale
4. **Implement**: Provide tested SQL and index definitions
5. **Verify**: Show before/after performance metrics

## Example Interactions
- "This query is slow - help me optimize it"
- "Design indexes for our user dashboard queries"
- "Our RLS policies are causing performance issues"
```

### Example Skill: Supabase RLS Patterns

```yaml
---
name: supabase-rls-patterns
description: Design and optimize Row-Level Security policies for Supabase multi-tenant applications. Use when implementing tenant isolation, designing RLS policies, or optimizing PostgreSQL security performance in Supabase.
---

# Supabase RLS Patterns

## Overview
Row-Level Security (RLS) in Supabase provides tenant isolation and data security at the database level. This skill covers performant RLS policy design for multi-tenant SaaS applications.

## Core Concepts

### RLS Policy Types
- **SELECT Policies**: Control read access
- **INSERT Policies**: Control data creation
- **UPDATE Policies**: Control data modification
- **DELETE Policies**: Control data removal

### Tenant Isolation Patterns
- **User-based**: Isolation by user ID
- **Organization-based**: Isolation by org/tenant ID
- **Role-based**: Isolation by user roles

## Implementation Patterns

### Pattern 1: Organization Tenant Isolation

**Use when**: Multi-tenant SaaS with organization hierarchy

```sql
-- Enable RLS
ALTER TABLE projects ENABLE ROW LEVEL SECURITY;

-- Policy: Users see only their organization's projects
CREATE POLICY "Users see own org projects"
  ON projects
  FOR SELECT
  USING (
    org_id IN (
      SELECT org_id
      FROM user_organizations
      WHERE user_id = auth.uid()
    )
  );

-- Performance optimization: Index on foreign key
CREATE INDEX idx_projects_org_id ON projects(org_id);
CREATE INDEX idx_user_orgs_user_id ON user_organizations(user_id);
```

### Pattern 2: Role-Based Access with RLS

**Use when**: Different permission levels per tenant

```sql
-- Policy: Admins see all, users see own
CREATE POLICY "Role-based project access"
  ON projects
  FOR SELECT
  USING (
    -- Admins see everything
    EXISTS (
      SELECT 1 FROM user_roles
      WHERE user_id = auth.uid()
      AND role = 'admin'
      AND org_id = projects.org_id
    )
    OR
    -- Users see assigned projects
    EXISTS (
      SELECT 1 FROM project_members
      WHERE user_id = auth.uid()
      AND project_id = projects.id
    )
  );
```

## Best Practices

1. **Index Foreign Keys**: Always index columns used in RLS policies
2. **Minimize Subqueries**: Use joins when possible, they're faster
3. **Test Performance**: Run EXPLAIN ANALYZE on queries with RLS
4. **Cache User Context**: Use security definer functions for expensive checks

## Common Pitfalls

- **Cartesian Products**: Avoid unindexed joins in policies
- **N+1 in Policies**: Don't create policies that cause N+1 queries
- **Missing Indexes**: Always index policy filter columns

## Resources (On-Demand)

### Complete Multi-Tenant Schema Example

```sql
-- Full example with optimized RLS policies
-- [Complete schema here]
```
```

### Example Command: Full-Stack Feature

```markdown
# Full-Stack Feature Development

Orchestrate end-to-end feature development from database schema to deployed frontend.

[Extended thinking: This workflow coordinates database-architect, backend-architect, frontend-developer, test-automator, and deployment-engineer to build complete features systematically.]

## Configuration Options

### Feature Type
- **crud**: Create, Read, Update, Delete operations
- **dashboard**: Data visualization feature
- **workflow**: Multi-step process feature

### Stack
- **nextjs-supabase**: Next.js frontend with Supabase backend
- **react-fastapi**: React with FastAPI backend

## Phase 1: Database Design

### Step 1.1: Schema Design
```
Use: database-architect
Task: Design database schema for [feature name]
Requirements: [Feature requirements]
```

**Expected Output:**
- Table definitions with relationships
- Indexes for query optimization
- RLS policies for security

## Phase 2: Backend Implementation

### Step 2.1: API Design
```
Use: backend-architect
Task: Design API endpoints
Context: Use schema from Phase 1
```

### Step 2.2: API Implementation
```
Use: fastapi-pro (or django-pro based on stack)
Task: Implement the API endpoints
Schema: [From Phase 1]
Endpoints: [From Step 2.1]
```

## Phase 3: Frontend Implementation

### Step 3.1: Component Design
```
Use: ui-ux-designer
Task: Design UI components for [feature]
```

### Step 3.2: Component Implementation
```
Use: frontend-developer
Task: Implement React components
Design: [From Step 3.1]
API: [From Phase 2]
```

## Phase 4: Testing

### Step 4.1: Generate Tests
```
Use: test-automator
Task: Generate comprehensive test suite
Coverage: Backend API + Frontend components
```

## Phase 5: Deployment

### Step 5.1: Setup CI/CD
```
Use: deployment-engineer
Task: Configure deployment pipeline
Stack: [Stack configuration]
```

**Final Deliverables:**
1. Database schema with migrations
2. Tested API endpoints
3. Frontend components
4. Test suite (unit + integration)
5. CI/CD pipeline
```

---

## Resources

### Official Documentation
- [Anthropic Agent Skills Specification](https://github.com/anthropics/skills/blob/main/agent_skills_spec.md)
- [Claude Code Documentation](https://docs.claude.com/en/docs/claude-code/)

### Internal Documentation
- [docs/architecture.md](docs/architecture.md) - System architecture principles
- [docs/agent-skills.md](docs/agent-skills.md) - Complete skills catalog
- [docs/plugins.md](docs/plugins.md) - Plugin catalog
- [docs/usage.md](docs/usage.md) - Usage guide
- [CLAUDE.md](CLAUDE.md) - Safety guide and configuration

### GitHub
- **Repository**: https://github.com/HahneAI/claude-code-agents
- **Upstream**: https://github.com/wshobson/agents

---

## Getting Help

1. **Check existing agents**: Browse `plugins/` for similar agents
2. **Read the docs**: `docs/` folder has comprehensive guides
3. **Test incrementally**: Build and test one component at a time
4. **Use version control**: Commit frequently, test before pushing
5. **Ask the community**: Open GitHub issues for questions

---

**Remember**: Great agents are focused, well-documented, and follow established patterns. Start simple, test thoroughly, and iterate based on real usage! 🚀
