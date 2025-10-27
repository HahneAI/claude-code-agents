---
name: doc-template-minimal
description: Token-efficient documentation standards. Auto-activates when documenting code, APIs, or creating technical documentation.
tier: instructions
keywords: [documentation, docs, README, API docs, function docs, comment, explain code, document this, write docs]
---

# Token-Efficient Documentation Standards

**Auto-activates when**: Documenting functions, APIs, classes, or creating README/technical documentation.

## Core Principle
**Every character costs tokens. Maximize information density, minimize redundancy.**

---

## Function Documentation (Max 50 tokens / ~40 words)

### Template
```markdown
## functionName(param: Type): ReturnType
[One sentence: what it does]. [Optional: key behavior or constraint]. [Optional: errors thrown].
```

### Example ✅
```markdown
## calculateBundlePrice(services: Service[]): Quote
Calculates total price with automatic bundling discounts. Applies regional pricing adjustments and validates service compatibility. Returns detailed quote with line items.
```

### DON'T ❌
- Multi-paragraph overviews
- Explaining what types mean
- Repeating code logic
- Standard library documentation

---

## Parameter Documentation

**Rule**: Only document non-obvious parameters (units, formats, constraints)

### Example ✅
```typescript
/**
 * @param basePrice - Price in USD cents (not dollars)
 * @param zipCode - Must be 5-digit US zip code
 */
```

### DON'T ❌
```typescript
/**
 * @param customerId - The customer's ID
 * @param email - The customer's email address
 */
```

---

## Code Comments

**Rule**: Comment "why" not "what"

### Example ✅
```typescript
// Postgres RLS policies require explicit tenant_id in WHERE clause
const query = `SELECT * FROM quotes WHERE tenant_id = $1`;

// Cache for 5 minutes to reduce Stripe API calls (rate limit: 100/sec)
const cacheKey = `stripe_customer_${customerId}`;
```

### DON'T ❌
```typescript
// Set the query variable
const query = `SELECT * FROM quotes WHERE tenant_id = $1`;

// Increment counter
counter++;
```

---

## API Endpoint Documentation (Max 200 tokens / ~150 words)

### Template
```markdown
## [METHOD] /api/endpoint
- **Purpose:** [What it does]
- **Auth:** [Auth requirement]
- **Input:** [Request shape]
- **Output:** [Response shape]
- **Errors:** [Error codes and meanings]
```

### Example ✅
```markdown
## POST /api/quotes
- **Purpose:** Creates service quote with bundling
- **Auth:** Requires API key
- **Input:** `{ services: string[], region: string }`
- **Output:** `{ quoteId: string, total: number, lineItems: [] }`
- **Errors:** 400 (invalid), 401 (unauthorized), 422 (incompatible services)
```

---

## README Documentation (Max 500 tokens / ~375 words)

### Structure
```markdown
# Project Name
[One-sentence description]

## Quick Start
[Minimal commands to get running]

## Key Features
- [Feature 1]
- [Feature 2]

## Documentation
- [Link to detailed docs]
- [Link to API reference]

## Tech Stack
- [Key technologies]

## License
[License type]
```

---

## Architecture Decision Records (Max 300 tokens / ~225 words)

### Template
```markdown
# ADR-[NUMBER]: [Decision Title]

## Status
[Proposed | Accepted | Deprecated]

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
- [Option A]: [Why rejected - 1 sentence]
- [Option B]: [Why rejected - 1 sentence]
```

---

## Token Budget Guidelines

| Doc Type | Max Tokens | ~Words | Format |
|----------|------------|--------|---------|
| Function | 50 | 40 | 3 sentences max |
| API endpoint | 200 | 150 | 5 bullet points |
| Class overview | 100 | 75 | 2 sentences + methods |
| README | 500 | 375 | Quick reference |
| ADR | 300 | 225 | Decision record |

---

## Warning Signs (Too Verbose)

- ⚠️ "Basically", "essentially", "obviously"
- ⚠️ Repeating type information
- ⚠️ Explaining standard libraries
- ⚠️ Multi-paragraph overviews
- ⚠️ Line-by-line code explanations

---

## Quality Checklist

- [ ] Could I cut this in half?
- [ ] Is this info available elsewhere? (Link instead)
- [ ] Would a dev understand in 30 seconds?
- [ ] Am I documenting "what" not "why"?
- [ ] Under token budget?
- [ ] No filler words?

---

## When to Document

✅ **DO document**:
- Public APIs consumed by other services
- Complex algorithms (non-obvious logic)
- Security-critical functions
- External integrations (Stripe, etc.)

❌ **DON'T document**:
- CRUD operations (self-explanatory)
- Simple getters/setters
- Test files (tests ARE docs)
- Obvious utility functions

---

## Agent Usage Pattern

When agent is asked to document code:

1. **Check complexity**: Does this need docs or is code self-explanatory?
2. **Choose template**: Function? API? Class? README?
3. **Write minimal**: Use template, stay under token budget
4. **Review**: Apply quality checklist
5. **Report**: Show token count vs budget

**Example agent response**:
```markdown
## Documentation Generated

## calculateBundlePrice(services: Service[]): Quote
Calculates total with automatic bundling discounts. Applies regional pricing and validates service compatibility. Returns detailed quote with line items.

**Token Count:** 28 tokens (Target: 50 tokens)
**Efficiency:** 44% under budget ✅
```

---

## Common Phrases to Avoid

Just state facts directly:
- ~~"This function is responsible for..."~~
- ~~"Basically, ..."~~
- ~~"Essentially, ..."~~
- ~~"Obviously, ..."~~
- ~~"As you can see, ..."~~
- ~~"It's worth noting that..."~~

---

**This skill auto-activates when documentation tasks are detected.**
**Reference**: Full template available in `tools/doc-template-minimal.md`
