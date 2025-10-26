# CLAUDE.md - Global Agent Configuration & Safety Guide

## ⚠️ CRITICAL SAFETY NOTICE

**This folder is at the GLOBAL DEVICE LEVEL** - Changes here affect:
- Claude Code CLI behavior for ALL projects
- VS Code extension behavior for ALL projects  
- Every agent, tool, and workflow across your entire system

**Location:** `C:\Users\antho\.claude\agents\` (synced to GitHub for version control)

---

## 📍 What This Folder Contains

```
.claude/agents/
├── .claude-plugin/           # Plugin marketplace configuration
├── plugins/                  # 64 domain-focused plugin directories
│   ├── backend-development/
│   │   ├── agents/          # Domain-specific agents (backend-architect, graphql-architect, etc.)
│   │   ├── commands/        # Slash commands and workflows
│   │   └── skills/          # Auto-activating skills (api-design-principles, etc.)
│   ├── python-development/
│   │   ├── agents/          # Python-specific agents
│   │   ├── commands/        # Python tooling commands
│   │   └── skills/          # 5 Python skills (async-patterns, testing, packaging, etc.)
│   └── [62 more plugins...]
├── docs/                     # Documentation
│   ├── agent-skills.md      # Complete skills catalog (47 skills)
│   ├── agents.md            # Agent reference
│   ├── architecture.md      # System design principles
│   ├── plugins.md           # Plugin catalog
│   └── usage.md             # Usage guide
├── PRIORITY_AGENTS.md        # Quick reference: 14 priority agents with skill mappings
├── WEBSITE-PRIORITY-AGENTS.md # Quick reference: 18 website agents with skill mappings
├── CLAUDE.md                 # This file - your safety guide
└── README.md                 # Public documentation
```

**Key Numbers:**
- 🔌 **64 plugins** organized by domain (backend, frontend, security, DevOps, languages, etc.)
- 🤖 **146 specialized agents** distributed across plugins
- 🎯 **47 auto-activating skills** in 15 plugins (progressive disclosure for token efficiency)
- 📋 **44+ slash commands** for direct workflow invocation

**Primary Edit Zones:**
- ✅ `plugins/*/agents/` - Safe to add new agents within appropriate domain plugin
- ✅ `plugins/*/commands/` - Safe to add/modify slash commands and workflows
- ✅ `plugins/*/skills/` - Safe to add skills (follow Agent Skills Specification)
- ⚠️ `PRIORITY_AGENTS.md` / `WEBSITE-PRIORITY-AGENTS.md` - Update when adding priority agents
- ⚠️ `CLAUDE.md` - This file - be thoughtful about changes
- ⚠️ `.claude-plugin/marketplace.json` - Plugin registry - modify carefully
- 🚫 `docs/` - Generated documentation - modify only when structure changes

---

## 🔒 Safety & Version Control

### GitHub Backup
**Repository:** `https://github.com/HahneAI/claude-code-agents`
- All changes are synced to GitHub automatically
- Use git history for rollback if something breaks
- **ALWAYS** commit before major changes

### Recovery Commands
```bash
# View what changed
git status
git diff

# Undo uncommitted changes
git restore <file>

# Go back to previous commit
git log --oneline  # Find the commit hash
git reset --hard <commit-hash>

# Emergency: Reset to last known good state
git reset --hard origin/main-base
```

---

## 🛠️ Available MCP Servers

**Filesystem:**
- Read/write files
- Search directories
- Move/rename files

**GitHub:**  
- Repository operations
- Commit management
- Branch operations

**Brave Search:**
- Web search capabilities
- Current information lookup

---

## 📋 Workflow Guidelines

### Before Making Changes
1. ✅ **Read files first** - Understand what you're changing
2. ✅ **Check git status** - Know your current state
3. ✅ **Create backup branch** (for major changes) - `git checkout -b backup-YYYY-MM-DD`
4. ✅ **Commit current state** - `git add -A && git commit -m "Before changes"`

### During Edits
1. ✅ **Make atomic commits** - One logical change per commit
2. ✅ **Test incrementally** - Don't batch unrelated changes
3. ✅ **Document decisions** - Clear commit messages
4. ✅ **Ask before destructive ops** - When in doubt, ask the user

### After Changes
1. ✅ **Test in real project** - Verify changes work as expected
2. ✅ **Commit with clear message** - Document what and why
3. ✅ **Push to GitHub** - `git push origin main-base`
4. ✅ **Monitor for issues** - Watch next few sessions for problems

---

## 🧪 Testing Strategy

### For Tool Changes
1. Create test file in `/examples/`
2. Test with simple case first
3. Test with edge cases
4. Verify in actual project

### For Agent Changes
1. Test agent activation
2. Verify agent selection logic
3. Check agent behavior in context
4. Validate output quality

### For Workflow Changes
1. Test each step individually
2. Test full workflow end-to-end
3. Verify handoffs between agents
4. Check error handling

---

## 🚨 Common Pitfalls - DON'T DO THIS

1. **Don't create new files unnecessarily** - Edit existing ones
2. **Don't skip reading files first** - Always Read before Edit
3. **Don't batch unrelated changes** - Keep commits atomic
4. **Don't ignore git status** - Know what you're changing
5. **Don't edit without understanding** - Ask questions first
6. **Don't push directly to main** - Use feature branches when appropriate
7. **Don't test in production** - This IS production for your CLI

---

## 🎓 Key Principles

1. **Safety First** - This affects your entire Claude Code setup
2. **Git is Your Friend** - Commit early, commit often
3. **Test Small Changes** - Don't break everything at once
4. **Document Decisions** - Future you will thank present you
5. **Ask Before Destructive Ops** - When in doubt, ask the user
6. **Focus on tools/workflows/agents** - That's your main job here

---

## 📝 Documentation Standards (Token Efficiency)

### Critical Philosophy
**Every character in documentation costs tokens. Be ruthlessly concise while maintaining clarity.**

Good documentation answers "what" and "why" quickly, then points to detailed resources. Bad documentation tries to explain everything inline and duplicates information available elsewhere.

### Markdown Documentation Rules

#### Function/Class Summaries
**Maximum 3 sentences. Period.**

✅ **GOOD:**
```markdown
## calculateBundlePrice(services: Service[]): Quote
Calculates total price with automatic bundling discounts. Applies regional pricing adjustments and validates service compatibility. Returns detailed quote with line items.
```

❌ **BAD:**
```markdown
## calculateBundlePrice(services: Service[]): Quote

### Overview
This function is responsible for calculating the total price when a customer requests multiple services together in a bundle. It's an important part of our pricing engine that helps us provide competitive quotes to customers.

### How It Works
First, the function receives an array of services. Then it iterates through each service to check if they're compatible with each other because some services can't be bundled together due to scheduling or equipment conflicts. After that, it looks up the base price for each service from our pricing matrix database table...

[...continues for 50+ lines]
```

#### Parameter Documentation
**Let types do the talking. Only document non-obvious params.**

✅ **GOOD:**
```typescript
// No comment needed - type is clear
function getCustomer(customerId: string): Promise<Customer>

// Comment only for non-obvious requirement
function calculatePrice(
  services: Service[],
  zipCode: string  // Must be 5-digit US zip code
): Quote
```

❌ **BAD:**
```typescript
/**
 * Gets a customer from the database
 * @param customerId - The unique identifier for the customer
 * @returns Promise that resolves to the Customer object
 */
function getCustomer(customerId: string): Promise<Customer>
```

#### Complex Logic Documentation
**"Why" not "what" - and keep it short**

✅ **GOOD:**
```typescript
// Apply 15% discount for bundles to match competitor pricing
const discount = subtotal * 0.15;

// Stripe requires amounts in cents, not dollars
const amountInCents = Math.round(total * 100);
```

❌ **BAD:**
```typescript
// This line calculates the discount by multiplying the subtotal by 0.15,
// which represents 15%, to get the bundle discount amount that will be
// applied to the final price
const discount = subtotal * 0.15;
```

### When Agents Generate Documentation

#### Automatic Doc Generation Rules
When an agent is asked to document code:

1. **Use the minimal template** (see `tools/doc-template.md`)
2. **Front-load critical info:** Purpose first, details later
3. **Cross-reference, don't duplicate:** "See X for details" not inline explanation
4. **One example max:** Show usage, don't explain every edge case
5. **OpenAPI over markdown:** For APIs, generate Swagger/OpenAPI specs

#### Documentation Triggers
**Only generate docs for:**
- ✅ Public APIs (consumed by other services/developers)
- ✅ Complex algorithms (non-obvious business logic)
- ✅ Security-critical functions (auth, payments, permissions)
- ✅ External integrations (third-party APIs)
- ✅ Configuration files (deployment, environment)

**NEVER generate docs for:**
- ❌ CRUD operations (they're self-explanatory)
- ❌ Simple getters/setters
- ❌ Test files (tests ARE the documentation)
- ❌ Internal utilities (obvious from function name + types)
- ❌ Obvious wrappers around libraries

### Inline Comment Standards

#### Code Comments
**Assume the reader can read code. Comment the "why" not the "what".**

✅ **GOOD:**
```typescript
// Postgres RLS policies require explicit tenant_id in WHERE clause
const query = `SELECT * FROM quotes WHERE tenant_id = $1 AND id = $2`;

// Cache for 5 minutes to reduce Stripe API calls
const cacheKey = `stripe_customer_${customerId}`;
```

❌ **BAD:**
```typescript
// Set the query variable to a SQL string
const query = `SELECT * FROM quotes WHERE tenant_id = $1 AND id = $2`;

// Increment the counter by 1
counter++;
```

#### TODO Comments
**Format for easy searching and include context**

```typescript
// TODO(username): [Priority] Description with enough context
// Example:
// TODO(alex): [HIGH] Implement retry logic for Stripe API failures. See issue #234
```

### API Documentation

#### REST APIs
**Use OpenAPI/Swagger, not markdown. Generate with tools.**

When documenting REST APIs:
1. Generate OpenAPI 3.0 spec
2. Add to `/docs/api/openapi.yaml`
3. Serve with Swagger UI
4. Markdown docs only link to Swagger UI

#### Internal Functions
**JSDoc for exported functions, nothing for internal ones**

✅ **GOOD:**
```typescript
/**
 * Calculates bundle quote with regional pricing.
 * @throws {ValidationError} If services are incompatible
 */
export function calculateBundlePrice(services: Service[]): Quote {
  // implementation
}

// No JSDoc needed for internal helper
function validateServiceCompatibility(services: Service[]): boolean {
  // implementation
}
```

### README Files

#### Project README
**Maximum 150 lines. Use links for details.**

Structure:
```markdown
# Project Name

One-sentence description.

## Quick Start
npm install && npm run dev

## Documentation
- [Architecture](docs/architecture.md)
- [API Docs](docs/api/)
- [Contributing](CONTRIBUTING.md)

## Tech Stack
- [List key technologies]

## License
MIT
```

#### Feature READMEs
**Only if complex. Otherwise, code + tests are enough.**

### Architecture Documentation

#### Diagrams Over Text
**One diagram = 1000 words**

Use:
- Mermaid for sequence diagrams
- Excalidraw for system architecture
- ASCII for simple flows

Don't write paragraphs explaining what a diagram shows clearly.

#### Architecture Decision Records (ADRs)
**For major decisions only, use standard format**

Template:
```markdown
# ADR-001: Use PostgreSQL RLS for Multi-Tenancy

## Status
Accepted

## Context
[2-3 sentences on the problem]

## Decision
[1 sentence on what we chose]

## Consequences
**Positive:**
- [Benefit 1]
- [Benefit 2]

**Negative:**
- [Tradeoff 1]
- [Tradeoff 2]

## Alternatives Considered
- Option A: [Why rejected]
- Option B: [Why rejected]
```

### Token Usage Metrics

#### Documentation Token Budget
**Track and enforce:**
- **Per Function Doc:** Max 50 tokens (~40 words)
- **Per API Endpoint Doc:** Max 200 tokens (~150 words)
- **Per Architecture Doc:** Max 1000 tokens (~750 words)

#### Warning Signs You're Too Verbose
- ⚠️ Using words like "basically", "essentially", "obviously"
- ⚠️ Repeating information from the code
- ⚠️ Explaining standard library usage
- ⚠️ Writing multi-paragraph overviews
- ⚠️ Documenting every parameter in detail

### Quality Checklist

Before committing documentation, verify:
- [ ] Could I cut this in half and keep the meaning?
- [ ] Is this information available elsewhere? (Link instead)
- [ ] Would a new developer understand this in 30 seconds?
- [ ] Am I documenting "what" instead of "why"? (Remove the "what")
- [ ] Is this staying under the token budget?

### Examples: Before/After

#### Example 1: Function Documentation

**BEFORE (Token waste):**
```markdown
## Overview
The `calculateRegionalPrice` function is a core component of our pricing system that handles the calculation of prices based on the customer's geographic location. This is important because different regions have different costs of living, labor rates, and material costs that need to be factored into our pricing.

## Parameters
- `basePrice`: This is the starting price before any regional adjustments are applied. It should be a number representing dollars.
- `zipCode`: The customer's zip code, which we use to look up their region in our database.
- `serviceType`: What type of service they're requesting, like "mulch" or "patio installation"

## Return Value
Returns a number representing the adjusted price for that region

## Example Usage
```typescript
const price = calculateRegionalPrice(100, "12345", "mulch");
// This will return something like 115 if that zip code has a 1.15 multiplier
```

## Implementation Details
The function first validates the inputs to make sure they're the right type...
[continues for 30+ more lines]
```

**AFTER (Token efficient):**
```markdown
## calculateRegionalPrice(basePrice: number, zipCode: string, service: string): number
Applies regional cost-of-living multiplier to base price. Throws `ValidationError` if zip code not found.
```

#### Example 2: API Documentation

**BEFORE (Verbose markdown):**
```markdown
# Create Bundle Quote API

## Overview
This endpoint allows you to create a new bundle quote for a customer...

[15 paragraphs explaining everything]
```

**AFTER (OpenAPI spec):**
```yaml
# In openapi.yaml
paths:
  /api/quotes/bundle:
    post:
      summary: Create bundle quote
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/BundleQuoteRequest'
      responses:
        '200':
          description: Quote created
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Quote'
```

Then in markdown:
```markdown
## Bundle Quotes API
See [OpenAPI Spec](openapi.yaml#/paths/~1api~1quotes~1bundle)
```

---

## Enforcement

### Code Review Checklist
When reviewing documentation:
- [ ] Is every doc under token budget?
- [ ] Could any docs be deleted without loss?
- [ ] Are we using types/specs instead of prose?
- [ ] Are comments explaining "why" not "what"?

### Automated Checks
Consider adding linters:
- `eslint-plugin-jsdoc` with strict rules
- Custom script to count doc tokens
- Pre-commit hook to flag verbose docs

### Agent Behavior
When agents are asked to document:
1. They should confirm: "Should I create minimal or comprehensive docs?"
2. Default to minimal unless explicitly asked for comprehensive
3. Use templates from `tools/doc-template.md`
4. Provide token count with documentation output

---

## 🔗 Resources

- **Claude Code Docs**: https://docs.claude.com/en/docs/claude-code/
- **GitHub Repo**: https://github.com/HahneAI/claude-code-agents
- **Upstream Source**: https://github.com/wshobson/agents
- **Documentation Template**: See `tools/doc-template.md`
- **Intent Classifier**: See `tools/intent-classifier.md`

---

## 💡 Remember

**You are working in the global configuration folder that powers the entire Claude Code experience. Every change here has system-wide impact. Be thoughtful, be careful, and always maintain the ability to roll back.**

When in doubt: Read first, change small, test often, commit frequently.

**Documentation debt is real debt. Less documentation that's maintained is better than comprehensive documentation that becomes outdated. Trust your types, trust your tests, and write docs only where they add unique value.**