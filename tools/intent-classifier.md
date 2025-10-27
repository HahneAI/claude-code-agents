# Intent Classifier Tool

**Purpose:** Routes user requests to the appropriate agent(s) based on keywords, context, and task complexity.

**Location:** `C:\Users\antho\.claude\agents\tools\intent-classifier.md`

**Usage:** Reference this tool when unclear which agent should handle a request.

---

## Core Purpose

Analyze user requests and determine:
1. **Primary Agent:** Who should lead this task
2. **Support Agents:** Who should assist or review
3. **Sequence:** What order agents should work in
4. **Complexity:** Single-agent or multi-agent workflow

---

## Classification Categories

### Backend & API Development

**Trigger Keywords:**
- API, endpoint, REST, GraphQL, microservice
- Authentication, authorization, JWT, OAuth
- Server, backend, service layer
- Integration, webhook, third-party API

**Primary Agents:**
- `backend-architect` → API design, architecture patterns, service boundaries
- `typescript-pro` → Implementation with type safety
- `nodejs-specialist` → Node.js specific patterns (if available)

**Consider Adding:**
- `security-auditor` → If mentions: auth, permissions, sensitive data
- `database-optimizer` → If mentions: queries, performance, data access
- `test-automator` → Always for backend logic

**Example Routing:**
```
User: "Design a REST API for multi-tenant quote management"
→ Primary: backend-architect (API design)
→ Support: security-auditor (multi-tenant security)
→ Support: database-optimizer (data modeling)
```

---

### Database & Data Layer

**Trigger Keywords:**
- Database, schema, table, query, SQL, PostgreSQL
- Index, performance, slow query
- Migration, RLS, row-level security
- ORM, Prisma, TypeORM, data model

**Primary Agents:**
- `database-optimizer` → Schema design, query optimization, indexing
- `sql-pro` → Complex SQL queries (if available)

**Consider Adding:**
- `backend-architect` → For data access layer patterns
- `security-auditor` → For RLS policies, data access control
- `test-automator` → For data layer tests

**Example Routing:**
```
User: "Optimize the quotes query that's taking 3 seconds"
→ Primary: database-optimizer (query optimization)
→ Support: backend-architect (may need caching strategy)
```

---

### Type-Safe Business Logic

**Trigger Keywords:**
- Pricing, calculation, validation, business rules
- TypeScript, type safety, Zod, validation
- Complex logic, algorithm, formula

**Primary Agents:**
- `typescript-pro` → Type-safe implementation
- `backend-architect` → If patterns/architecture involved

**Consider Adding:**
- `test-automator` → ALWAYS add for business logic
- `code-reviewer` → For complex calculations

**Example Routing:**
```
User: "Implement pricing calculator with bundling discounts"
→ Primary: typescript-pro (type-safe calculations)
→ Support: test-automator (comprehensive tests)
→ Support: code-reviewer (verify logic correctness)
```

---

### Frontend & UI

**Trigger Keywords:**
- React, component, UI, interface, design
- Form, button, modal, layout, responsive
- Styling, CSS, Tailwind, design system
- User experience, UX, interaction

**Primary Agents:**
- `frontend-developer` → React components, client-side logic
- `ui-ux-designer` → Design patterns, user experience

**Consider Adding:**
- `typescript-pro` → For complex client-side logic
- `test-automator` → For component tests

**Example Routing:**
```
User: "Build a quote builder form with validation"
→ Primary: frontend-developer (React component)
→ Support: typescript-pro (validation logic)
→ Support: test-automator (component tests)
```

---

### Payment Integration

**Trigger Keywords:**
- Stripe, payment, checkout, subscription
- Webhook, payment method, invoice
- PCI compliance, payment security

**Primary Agents:**
- `payment-integration` → Stripe expertise, payment workflows

**ALWAYS Add:**
- `security-auditor` → Payment systems are security-critical

**Consider Adding:**
- `backend-architect` → For integration patterns
- `test-automator` → For payment flow tests

**Example Routing:**
```
User: "Implement Stripe checkout with webhook handling"
→ Primary: payment-integration (Stripe expertise)
→ Support: security-auditor (security review - CRITICAL)
→ Support: backend-architect (webhook architecture)
→ Support: test-automator (payment flow tests)
```

---

### Testing & Quality

**Trigger Keywords:**
- Test, testing, unit test, integration test
- Coverage, TDD, test-driven development
- Jest, Vitest, Playwright, E2E

**Primary Agents:**
- `test-automator` → Test generation and execution
- `tdd-orchestrator` → TDD workflow guidance

**Consider Adding:**
- Domain specialist → For domain-specific test logic
- `code-reviewer` → For test quality review

**Example Routing:**
```
User: "Write tests for the pricing calculator"
→ Primary: test-automator (test generation)
→ Support: typescript-pro (domain expertise for test scenarios)
```

---

### Security & Compliance

**Trigger Keywords:**
- Security, vulnerability, audit, compliance
- Authentication, authorization, permissions
- OWASP, PCI, GDPR, data privacy
- Penetration test, security review

**Primary Agents:**
- `security-auditor` → Security assessment and guidance
- `incident-responder` → If active security issue

**Consider Adding:**
- Domain specialist → To implement fixes
- `code-reviewer` → Verify security improvements

**Example Routing:**
```
User: "Audit our API for security vulnerabilities"
→ Primary: security-auditor (comprehensive security review)
→ Support: backend-architect (architecture assessment)
→ Support: database-optimizer (data access security)
```

---

### Debugging & Troubleshooting

**Trigger Keywords:**
- Bug, error, broken, not working, failing
- Debug, troubleshoot, investigate, diagnose
- Stack trace, error message, exception

**Primary Agents:**
- `error-detective` → Log analysis, error investigation
- `debugger` → Root cause analysis

**Consider Adding:**
- Domain specialist → To implement fix
- `test-automator` → Add regression test

**Example Routing:**
```
User: "Users are getting 500 errors on checkout"
→ Primary: error-detective (analyze logs and error patterns)
→ Support: debugger (root cause analysis)
→ Support: payment-integration (if payment-related)
→ Follow-up: test-automator (regression tests after fix)
```

---

### Performance Optimization

**Trigger Keywords:**
- Slow, performance, optimization, latency
- Speed up, faster, improve performance
- Memory, CPU, load time

**Primary Agents:**
- `database-optimizer` → If database-related
- `performance-engineer` → General performance (if available)

**Consider Adding:**
- Domain specialist → To implement optimizations
- `test-automator` → Performance regression tests

**Example Routing:**
```
User: "Dashboard is loading slowly for large datasets"
→ Primary: database-optimizer (query optimization)
→ Support: backend-architect (caching strategy)
→ Support: frontend-developer (if UI rendering issue)
```

---

### Code Review & Refactoring

**Trigger Keywords:**
- Review, refactor, improve, clean up
- Code quality, best practices, maintainability
- Technical debt, legacy code

**Primary Agents:**
- `code-reviewer` → Comprehensive code review
- Domain specialist → For domain-specific improvements

**Consider Adding:**
- `security-auditor` → If security implications
- `test-automator` → Ensure tests exist

**Example Routing:**
```
User: "Review the payment processing code"
→ Primary: code-reviewer (code quality review)
→ Support: payment-integration (domain expertise)
→ Support: security-auditor (security review)
```

---

## Common Workflows

### Feature Development Flow
```
1. backend-architect → Design API
2. database-optimizer → Design schema
3. typescript-pro → Implement business logic
4. frontend-developer → Build UI
5. test-automator → Generate tests
6. security-auditor → Security review
7. code-reviewer → Final review
```

### Bug Fix Flow
```
1. error-detective → Identify issue
2. debugger → Root cause analysis
3. [Domain agent] → Implement fix
4. test-automator → Add regression test
5. code-reviewer → Ensure fix doesn't introduce new issues
```

### Security Hardening Flow
```
1. security-auditor → Security assessment
2. backend-architect → Architecture review
3. database-optimizer → Review data access patterns
4. [Implementation agent] → Apply fixes
5. test-automator → Security test suite
6. security-auditor → Re-verify
```

---

## Context-Based Routing

### User Experience Level

**Beginner/Unclear Request:**
- Start with clarifying questions
- Suggest appropriate agent
- Explain why that agent is best

**Expert/Clear Request:**
- Route immediately
- Activate multiple agents if needed
- Trust user knows what they want

### Project Phase

**Early Development:**
- Favor architects and designers
- More planning, less fixing
- Example: backend-architect, ui-ux-designer

**Active Development:**
- Favor implementation agents
- Example: typescript-pro, frontend-developer

**Production/Maintenance:**
- Favor debuggers and optimizers
- Example: error-detective, database-optimizer, security-auditor

### Request Ambiguity

**Clear Task:**
```
User: "Create a POST endpoint for /api/quotes"
→ Clear: backend-architect + typescript-pro
```

**Ambiguous Task:**
```
User: "The quotes feature isn't working"
→ Clarify: "I'll need more details. Are you seeing:
   - An error message? (debugger + error-detective)
   - Slow performance? (database-optimizer)
   - Security issues? (security-auditor)
   - Incorrect calculations? (typescript-pro + test-automator)"
```

---

## Special Cases

### When Multiple Agents Apply Equally
**Ask the user to choose OR pick based on:**
1. Project phase (architecture vs. implementation)
2. Current priority (feature delivery vs. technical debt)
3. User's stated goal

### When No Agent Fits Well
**Options:**
1. Use `prompt-engineer` to create a custom agent
2. Combine general-purpose agents
3. Suggest the user needs a new specialized agent

### When Request Spans Many Domains
**Example:** "Build a complete CRM from scratch"

**Strategy:**
1. Break into phases
2. Assign agent to each phase
3. Create a workflow (consider workflow templates)

---

## Decision Tree

```
START
  ↓
Is this about API/backend?
  YES → backend-architect
    ↓ mentions security? → + security-auditor
    ↓ mentions data? → + database-optimizer
  NO → continue
  ↓
Is this about database/queries?
  YES → database-optimizer
    ↓ mentions RLS? → + security-auditor
  NO → continue
  ↓
Is this about calculations/logic?
  YES → typescript-pro
    ↓ complex? → + backend-architect
    ↓ always → + test-automator
  NO → continue
  ↓
Is this about UI/frontend?
  YES → frontend-developer
    ↓ mentions design? → + ui-ux-designer
  NO → continue
  ↓
Is this about payments?
  YES → payment-integration
    ↓ always → + security-auditor
  NO → continue
  ↓
Is this about testing?
  YES → test-automator
    ↓ TDD workflow? → + tdd-orchestrator
  NO → continue
  ↓
Is this a bug/error?
  YES → error-detective
    ↓ need root cause? → + debugger
  NO → continue
  ↓
Is this about security/review?
  YES → security-auditor OR code-reviewer
  NO → Ask for clarification
```

---

## Output Format

When routing a request, provide:

```markdown
## Route Recommendation

**Primary Agent:** [agent-name]
**Reason:** [One sentence why]

**Support Agents:**
- [agent-name]: [Their specific role in this task]
- [agent-name]: [Their specific role in this task]

**Suggested Sequence:**
1. [agent] - [action]
2. [agent] - [action]
3. [agent] - [action]

**Estimated Complexity:** [Simple | Moderate | Complex]
```

---

## Practical Examples

### Example 1: Simple Frontend Task
**Request:** "Add a loading spinner to the quote form"

**Route Recommendation:**

**Primary Agent:** frontend-developer
**Reason:** Simple UI component addition

**Support Agents:** None needed

**Suggested Sequence:**
1. frontend-developer - Implement loading spinner component

**Estimated Complexity:** Simple

---

### Example 2: Complex Multi-Agent Task
**Request:** "Build an API for multi-tenant quote management with Stripe integration"

**Route Recommendation:**

**Primary Agent:** backend-architect
**Reason:** Complex system requiring architectural planning

**Support Agents:**
- database-optimizer: Multi-tenant schema design with RLS
- security-auditor: Multi-tenant security + PCI compliance
- payment-integration: Stripe implementation expertise
- typescript-pro: Business logic implementation
- test-automator: Comprehensive test suite

**Suggested Sequence:**
1. backend-architect - Design API architecture and multi-tenant strategy
2. database-optimizer - Design schema with RLS policies
3. security-auditor - Review security model and compliance requirements
4. typescript-pro - Implement business logic with type safety
5. payment-integration - Integrate Stripe API and webhooks
6. test-automator - Generate comprehensive test suite
7. security-auditor - Final security review before deployment

**Estimated Complexity:** Complex (full-stack, security-critical, multiple systems)

---

### Example 3: Debugging Task
**Request:** "Quotes are loading slowly for some customers"

**Route Recommendation:**

**Primary Agent:** error-detective
**Reason:** Need to analyze logs and identify patterns

**Support Agents:**
- database-optimizer: Likely a query performance issue
- debugger: Root cause analysis if not database-related

**Suggested Sequence:**
1. error-detective - Analyze logs to identify affected customers and queries
2. database-optimizer - Optimize slow queries and add indexes
3. test-automator - Add performance regression tests

**Estimated Complexity:** Moderate

---

### Example 4: Security Review
**Request:** "Audit the payment processing code for vulnerabilities"

**Route Recommendation:**

**Primary Agent:** security-auditor
**Reason:** Security-focused comprehensive review

**Support Agents:**
- payment-integration: Domain expertise for payment-specific security
- code-reviewer: Code quality assessment

**Suggested Sequence:**
1. security-auditor - Comprehensive security audit
2. payment-integration - Review payment-specific security patterns
3. code-reviewer - Assess overall code quality
4. [Implementation agent if issues found] - Apply security fixes
5. test-automator - Add security test suite
6. security-auditor - Re-verify after fixes

**Estimated Complexity:** Moderate to Complex

---

## Maintenance Notes

**Update this tool when:**
- New agents are added to the system
- New patterns emerge in routing decisions
- Users frequently need clarification on routing
- Project priorities shift (e.g., increased security focus)

**Review monthly:**
- Are routing decisions accurate?
- Do suggested sequences make sense?
- Are there missing agent combinations?
- Should any workflows be standardized?

---

**Last Updated:** 2025-10-26
**Version:** 1.0.0
**Maintainer:** System Administrator
