# Minimal Documentation Template Tool

---
name: doc-template-minimal
description: Token-efficient documentation format for functions, APIs, and systems. Maximizes clarity while minimizing token consumption.
category: documentation
version: 1.0.0
tags: [documentation, token-efficiency, standards, templates]
---

## Purpose
Provides standardized, token-efficient documentation formats that maintain clarity while minimizing token consumption.

## Core Principle
**Every character costs tokens. Maximize information density, minimize redundancy.**

Good documentation answers "what" and "why" quickly, then points to detailed resources. Bad documentation tries to explain everything inline and duplicates information available elsewhere.

---

## When to Use

- ✅ **DO use when:** Documenting public APIs consumed by other services
- ✅ **DO use when:** Complex algorithms with non-obvious business logic
- ✅ **DO use when:** Security-critical functions
- ✅ **DO use when:** External integrations (Stripe, APIs, etc.)

- ❌ **DON'T use for:** CRUD operations (they're self-explanatory)
- ❌ **DON'T use for:** Simple getters/setters
- ❌ **DON'T use for:** Test files (tests are the documentation)
- ❌ **DON'T use for:** Obvious utility functions

---

## Function Documentation Format

### Standard Template
```markdown
## functionName(param: Type): ReturnType
- **Purpose:** [What it does in one sentence]
- **Key behavior:** [Important logic or side effects]
- **Throws:** [Errors it may throw, if any]
```

**Maximum: 3 sentences. Period.**

### Example: GOOD ✅
```markdown
## calculateBundlePrice(services: Service[]): Quote
Calculates total price with automatic bundling discounts. Applies regional pricing adjustments and validates service compatibility. Returns detailed quote with line items.
```

**Token count:** ~25 tokens

### Example: BAD ❌
```markdown
## calculateBundlePrice(services: Service[]): Quote

### Overview
This function is responsible for calculating the total price when a customer requests multiple services together in a bundle. It's an important part of our pricing engine that helps us provide competitive quotes to customers.

### How It Works
First, the function receives an array of services. Then it iterates through each service to check if they're compatible with each other because some services can't be bundled together due to scheduling or equipment conflicts. After that, it looks up the base price for each service from our pricing matrix database table...

[...continues for 50+ lines]
```

**Token count:** 500+ tokens (20x overhead!)

---

## Parameter Documentation

### Rule: Let Types Do the Talking

**Only document non-obvious parameters.**

### Example: GOOD ✅
```typescript
/**
 * Calculates regional price with timezone-aware surge pricing.
 * @param basePrice - Price in USD cents (not dollars)
 * @param region - ISO region code for pricing tier lookup
 */
```

### Example: BAD ❌
```typescript
/**
 * Calculates the price for a region
 * @param basePrice - This is the base price that will be used as the starting point for the calculation
 * @param region - This is the region where the customer is located and will be used to determine regional pricing
 */
```

---

## Code Comment Standards

### Rule: Comment "Why" Not "What"

### Example: GOOD ✅
```typescript
// Postgres RLS policies require explicit tenant_id in WHERE clause
const query = `SELECT * FROM quotes WHERE tenant_id = $1 AND id = $2`;

// Cache for 5 minutes to reduce Stripe API calls (rate limit: 100/sec)
const cacheKey = `stripe_customer_${customerId}`;

// Use Promise.all instead of sequential to avoid 2s+ total delay
await Promise.all(customers.map(c => notifyCustomer(c)));
```

### Example: BAD ❌
```typescript
// Set the query variable to a SQL string
const query = `SELECT * FROM quotes WHERE tenant_id = $1 AND id = $2`;

// Increment the counter by 1
counter++;

// Loop through the array
for (const item of items) { ... }
```

---

## TODO Comments Format

### Standard Template
```typescript
// TODO(username): [Priority] Description with enough context
// Example:
// TODO(alex): [HIGH] Implement retry logic for Stripe API failures. See issue #234
// TODO(sarah): [LOW] Refactor to use new validator class when available
```

---

## API Endpoint Documentation Format

### Standard Template
```markdown
## [METHOD] /api/endpoint
- **Purpose:** [What it does]
- **Auth:** [Required auth level]
- **Input:** [Key params]
- **Output:** [Response format]
- **Errors:** [Common error codes]
```

**Maximum: 200 tokens (~150 words)**

### Example: GOOD ✅
```markdown
## POST /api/quotes
- **Purpose:** Creates new service quote with bundling
- **Auth:** Requires valid API key
- **Input:** `{ services: string[], region: string }`
- **Output:** `{ quoteId: string, total: number, lineItems: [] }`
- **Errors:** 400 (invalid services), 401 (unauthorized), 422 (incompatible combo)
```

### Example: BAD ❌
```markdown
## POST /api/quotes

### Overview
This endpoint is used to create a new quote for customers who want to purchase multiple services together...

### Authentication
You will need to provide a valid API key in the Authorization header...

[...continues for 50+ lines explaining standard REST conventions]
```

---

## Class Documentation Format

### Standard Template
```markdown
## ClassName
[One sentence describing what this class represents/does]
[Optional: One sentence about key behavior or usage patterns]

**Key Methods:**
- `methodName()` - [One sentence]
- `methodName()` - [One sentence]
```

### Example: GOOD ✅
```markdown
## BundlePricingCalculator
Calculates quotes for multi-service bundles with automatic discounting. Handles regional pricing adjustments and service compatibility validation.

**Key Methods:**
- `calculate(services)` - Generates complete quote with line items
- `validateCompatibility(services)` - Throws error if services conflict
```

---

## README Documentation Format

### Standard Structure (Max 150 lines)
```markdown
# Project Name

[One-sentence description]

## Quick Start
[Minimal commands to get running]

## Key Features
- [Feature 1]
- [Feature 2]
- [Feature 3]

## Documentation
- [Link to detailed docs]
- [Link to API reference]
- [Link to architecture]

## Tech Stack
- [Key technologies only]

## License
[License type]
```

### Example: GOOD ✅
```markdown
# TradesphereApp

AI-powered CRM for American trades companies with intelligent pricing.

## Quick Start
```bash
npm install
npm run dev
```

## Key Features
- Multi-tenant quote management with RLS
- AI-powered pricing intelligence
- Stripe payment integration

## Documentation
- [Architecture](docs/architecture.md)
- [API Reference](docs/api/)
- [Database Schema](docs/schema.md)

## Tech Stack
- Next.js 14, TypeScript, tRPC
- PostgreSQL with Prisma
- Stripe for payments

## License
MIT
```

---

## Architecture Decision Records (ADR)

### Standard Template
```markdown
# ADR-[NUMBER]: [Decision Title]

## Status
[Proposed | Accepted | Deprecated | Superseded]

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
- [Option A]: [Why rejected in 1 sentence]
- [Option B]: [Why rejected in 1 sentence]
```

**Maximum: 300 tokens (~225 words)**

### Example: GOOD ✅
```markdown
# ADR-001: Use PostgreSQL RLS for Multi-Tenancy

## Status
Accepted

## Context
Need to isolate customer data at the database level. Must prevent cross-tenant data leaks while maintaining query performance.

## Decision
Use PostgreSQL Row Level Security (RLS) with tenant_id policies on all tables.

## Consequences

**Positive:**
- Database-enforced tenant isolation (cannot be bypassed)
- No application-level tenant filtering needed
- Works with all ORM queries automatically

**Negative:**
- Must include tenant_id in all WHERE clauses explicitly
- Slight query performance overhead (~5-10ms per query)
- More complex database migrations

## Alternatives Considered
- Application-level filtering: Too easy to forget, security risk
- Separate databases per tenant: Expensive, migration complexity
```

---

## Token Budget Guidelines

| Documentation Type | Max Tokens | ~Words | Example |
|-------------------|------------|--------|---------|
| Function doc | 50 | 40 | Three sentences max |
| API endpoint doc | 200 | 150 | Five bullet points |
| Class overview | 100 | 75 | Two sentences + method list |
| README | 500 | 375 | Quick reference only |
| Architecture doc | 1000 | 750 | Use diagrams liberally |
| ADR | 300 | 225 | Be decisive, not exhaustive |

---

## Warning Signs (Too Verbose)

- ⚠️ Using words like "basically", "essentially", "obviously"
- ⚠️ Repeating information from the code or type signatures
- ⚠️ Explaining standard library usage
- ⚠️ Writing multi-paragraph overviews
- ⚠️ Documenting every parameter in detail when types are clear
- ⚠️ Describing what code does line-by-line
- ⚠️ Adding "helpful" context that's not essential

---

## Quality Checklist

Before committing documentation, verify:
- [ ] Could I cut this in half and keep the meaning?
- [ ] Is this information available elsewhere? (Link instead)
- [ ] Would a new developer understand this in 30 seconds?
- [ ] Am I documenting "what" instead of "why"? (Remove the "what")
- [ ] Is this staying under the token budget?
- [ ] Have I removed all filler words?
- [ ] Are all sentences essential?

---

## Common Phrases to Avoid

These are usually unnecessary filler:

- "This function is responsible for..."
- "Basically, ..."
- "Essentially, ..."
- "Obviously, ..."
- "As you can see, ..."
- "It's worth noting that..."
- "In other words, ..."
- "Simply put, ..."
- "At the end of the day, ..."

**Just state facts directly.**

---

## Before/After Examples

### Example 1: Function Documentation

#### BEFORE (Token Waste) ❌
```markdown
## Overview
The `calculateRegionalPrice` function is a core component of our pricing system that handles the calculation of prices based on the customer's geographic location. This is important because different regions have different costs of living, labor rates, and material costs that need to be factored into our pricing.

## Parameters
- `basePrice`: This is the starting price before any regional adjustments are applied. It should be a number representing dollars.
- `zipCode`: The customer's zip code, which we use to look up their region in our database.

## Returns
Returns an object containing the adjusted price and the region information.

## Example
```typescript
const result = calculateRegionalPrice(100, "90210");
console.log(result.adjustedPrice); // 115 (15% adjustment for Beverly Hills)
```

**Token count:** ~180 tokens

#### AFTER (Minimal) ✅
```markdown
## calculateRegionalPrice(basePrice: number, zipCode: string): PriceResult
Applies regional cost adjustments based on zip code lookup. Returns adjusted price and region metadata.
```

**Token count:** ~20 tokens (90% reduction)

---

### Example 2: API Documentation

#### BEFORE (Token Waste) ❌
```markdown
## POST /api/customers

### Description
This endpoint allows you to create a new customer in the system. It's important to note that each customer must have a unique email address, and you'll need to provide at least a name and email to create the customer successfully.

### Authentication
This endpoint requires authentication. You should include your API key in the Authorization header using the Bearer token format.

### Request Body
The request body should be a JSON object with the following fields:
- `name` (required): The customer's full name as a string
- `email` (required): The customer's email address as a string. Must be a valid email format.
- `phone` (optional): The customer's phone number as a string

### Response
Upon successful creation, you'll receive a 201 Created status code along with a JSON object containing the newly created customer's information, including their auto-generated ID.

### Error Responses
If something goes wrong, you might receive one of these error codes:
- 400 Bad Request: If the request body is malformed or missing required fields
- 401 Unauthorized: If you didn't provide a valid API key
- 409 Conflict: If a customer with that email already exists

**Token count:** ~250 tokens

#### AFTER (Minimal) ✅
```markdown
## POST /api/customers
- **Purpose:** Creates new customer
- **Auth:** API key required
- **Input:** `{ name: string, email: string, phone?: string }`
- **Output:** `{ id: string, name: string, email: string, phone?: string }`
- **Errors:** 400 (invalid data), 401 (unauthorized), 409 (duplicate email)
```

**Token count:** ~35 tokens (86% reduction)

---

## Integration Guidelines

### When Writing Code
Ask: "Does this need documentation or is the code self-explanatory?"
- **Public APIs** → YES, document with template
- **Internal functions** → ONLY if complex logic
- **Simple CRUD** → NO, code is clear
- **Complex algorithms** → YES, explain "why" not "what"

### When Reviewing Code
Check documentation against this template:
1. Is it minimal? (Under token budget)
2. Is it informative? (Provides value)
3. Does it follow templates? (Consistent format)
4. Could it be cut further? (No redundancy)

### When Generating Docs
Always reference this template and stick to token budgets.

**Agent Response Format:**
```markdown
## Documentation Generated

[Minimal documentation following template]

**Token Count:** X tokens (Target: Y tokens)
**Efficiency:** [% under budget]
```

---

## Tool Integration

### Use with Other Tools
- **Works well with:** code-reviewer (enforce standards)
- **Works well with:** intent-classifier (identify doc needs)
- **Prerequisite for:** Any documentation task

### Agent Recommendations
| Agent Type | Usage Pattern | Why |
|-----------|---------------|-----|
| typescript-pro | Reference when documenting code | Ensures accurate technical details |
| backend-architect | Reference for API docs | Maintains architectural consistency |
| code-reviewer | Enforce template standards | Checks doc quality and completeness |

---

## Examples for Agents

When agents are asked to document code, they should respond like this:

### Agent Example 1: Simple Function
**User:** "Document the getUserById function"

**Agent Response:**
```markdown
## getUserById(id: string): Promise<User>
Fetches user by ID from database. Throws `NotFoundError` if user doesn't exist.
```

**Note:** Simple function needs only 2 sentences. Type signature provides parameter details.

---

### Agent Example 2: Complex Function
**User:** "Document the calculateBundlePrice function"

**Agent Response:**
```markdown
## calculateBundlePrice(services: Service[], options?: PricingOptions): Quote
Calculates total with automatic bundling discounts (up to 30% for 3+ services). Applies regional pricing adjustments and validates service compatibility. Returns detailed quote with line items and discount breakdown.

See: /docs/pricing/bundle-logic.md for discount tier details.
```

**Note:** Complex function gets 3 sentences + link to detailed docs.

---

### Agent Example 3: API Endpoint
**User:** "Document the POST /api/quotes endpoint"

**Agent Response:**
```markdown
## POST /api/quotes
- **Purpose:** Creates new service quote with bundling
- **Auth:** Requires valid API key (X-API-Key header)
- **Input:** `{ services: string[], region: string, customerId?: string }`
- **Output:** `{ quoteId: string, total: number, lineItems: QuoteItem[], discount: number }`
- **Errors:** 400 (invalid services), 401 (unauthorized), 422 (incompatible services), 500 (pricing calculation failed)
```

**Note:** Stays under 200 token budget, provides all essential info.

---

## Troubleshooting

### Problem: Documentation still too verbose
**Solution:**
1. Check for filler words (basically, essentially, etc.)
2. Remove sentences that repeat type information
3. Link to external docs instead of explaining inline
4. Ask: "Would this make sense to an experienced developer?"

### Problem: Agent generates overly detailed docs
**Solution:**
1. Remind agent to reference this template
2. Specify token budget explicitly
3. Request revision: "Make this 50% shorter while keeping key info"

### Problem: Documentation is too terse
**Solution:**
1. Ensure "why" is included, not just "what"
2. Add one sentence about key behavior or constraints
3. Consider if this is complex enough to need docs at all

---

## Maintenance Notes

**Update this template when:**
- New documentation patterns emerge
- Token budgets need adjustment
- New file types need coverage
- Team feedback indicates confusion

**Review quarterly:**
- Are docs staying under token budgets?
- Are agents following the template?
- Do we need stricter or looser rules?
- Are there new best practices to include?

---

**Last Updated:** 2025-10-26
**Version:** 1.0.0
**Maintainer:** System Administrator
