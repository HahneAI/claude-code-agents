---
name: intent-classifier
description: Agent routing logic for intelligent task classification. Auto-activates when analyzing user requests to determine optimal agent selection.
tier: instructions
keywords: [which agent, route, classify, task routing, agent selection, multi-agent, workflow]
---

# Agent Routing & Intent Classification

**Auto-activates when**: Determining which agent(s) should handle a user request, or planning multi-agent workflows.

## Core Purpose

Analyze user requests and determine:
1. **Primary Agent**: Who leads the task
2. **Support Agents**: Who assists or reviews
3. **Sequence**: Work order (sequential vs parallel)
4. **Complexity**: Single-agent or multi-agent workflow

---

## Quick Routing Matrix

### Backend & API → `backend-architect` (Opus)
**Keywords**: API, endpoint, REST, GraphQL, microservice, authentication, webhook
**Add**: security-auditor (if auth/sensitive), database-optimizer (if data-heavy), test-automator

### Database → `database-optimizer` (Opus)
**Keywords**: database, query, SQL, schema, index, migration, RLS, performance
**Add**: backend-architect (access patterns), security-auditor (RLS policies)

### Type-Safe Logic → `typescript-pro` (Sonnet)
**Keywords**: TypeScript, pricing, calculation, validation, business rules, Zod
**Add**: test-automator (ALWAYS for business logic), code-reviewer (complex calculations)

### Frontend/UI → `frontend-developer` (Sonnet)
**Keywords**: React, component, UI, form, styling, Tailwind, responsive
**Add**: ui-ux-designer (design patterns), typescript-pro (complex logic), test-automator

### Payments → `payment-integration` (Sonnet)
**Keywords**: Stripe, PayPal, payment, checkout, subscription, webhook, invoice
**Add**: security-auditor (CRITICAL - always for payments), backend-architect (integration), test-automator

### Testing → `test-automator` (Sonnet)
**Keywords**: test, unit test, integration test, coverage, TDD, Jest, Vitest
**Add**: [domain specialist] (for domain-specific test logic)

### Security → `security-auditor` (Opus)
**Keywords**: security, vulnerability, audit, compliance, OWASP, auth, permissions
**Add**: [domain specialist] (to implement fixes), code-reviewer (verify fixes)

### Debugging → `debugger` (Sonnet)
**Keywords**: error, bug, debug, fix, broken, not working, exception
**Add**: error-detective (complex/distributed errors), test-automator (regression tests)

### Documentation → `docs-architect` (Sonnet)
**Keywords**: documentation, docs, README, API docs, explain, tutorial
**Add**: [domain specialist] (for technical accuracy)

### Mobile/PWA → `mobile-developer` (Sonnet)
**Keywords**: mobile, PWA, React Native, responsive, iOS, Android, app store
**Add**: frontend-developer (web components), ui-ux-designer (mobile UX)

### AI/LLM → `prompt-engineer` (Opus)
**Keywords**: AI, LLM, prompt, Claude, GPT, LangChain, RAG, embedding
**Add**: ai-engineer (implementation), backend-architect (integration)

---

## Multi-Agent Workflow Patterns

### Pattern 1: Architecture → Implementation → Review
**When**: Building new features/systems
**Flow**:
1. backend-architect (design)
2. [implementation agent]
3. test-automator
4. code-reviewer

### Pattern 2: TDD Cycle
**When**: Test-driven development
**Flow**:
1. tdd-orchestrator (define tests)
2. [implementation agent]
3. test-automator (edge cases)
4. tdd-orchestrator (refactor)

### Pattern 3: Security-First
**When**: Security-critical features (auth, payments, data)
**Flow**:
1. security-auditor (threat model)
2. [implementation agent]
3. test-automator (security tests)
4. security-auditor (final review)

### Pattern 4: Full-Stack Feature
**When**: Features spanning frontend + backend
**Flow** (parallel):
- backend-architect → [backend agent] → test-automator
- frontend-developer → ui-ux-designer → test-automator
Then: code-reviewer (review both)

### Pattern 5: Debugging Investigation
**When**: Complex bugs, production issues
**Flow**:
1. error-detective (analyze logs, patterns)
2. debugger (reproduce and fix)
3. test-automator (regression tests)
4. code-reviewer (review fix)

---

## Decision Tree: Single vs Multi-Agent

```
Is task confined to single domain with clear execution?
├─ YES → Single agent
└─ NO → Cross-domain OR requires planning first?
    ├─ YES → Multi-agent (architect → implementation)
    └─ NO → Unclear requirements?
        ├─ YES → Start with claude-code-expert or architect
        └─ NO → Multi-agent (parallel execution possible)
```

---

## Model Selection

- **Opus**: Complex architecture, strategy, critical decisions, multi-step reasoning
- **Sonnet**: Implementation, code generation, standard workflows, balanced tasks
- **Haiku**: Simple deterministic tasks, fast execution

---

## Special Rules

### ALWAYS Include test-automator For:
- Business logic (pricing, calculations, validation)
- Backend API endpoints
- Payment processing
- Security-critical functions

### ALWAYS Include security-auditor For:
- Payment systems (Stripe, PayPal, etc.)
- Authentication/authorization
- Data privacy (PII, sensitive data)
- RLS policies
- API security

### Prefer Specialized Agents Over General:
- payment-integration > backend-architect (for Stripe work)
- database-optimizer > backend-architect (for query performance)
- typescript-pro > frontend-developer (for complex type logic)
- mobile-developer > frontend-developer (for mobile-specific work)

---

## Example Routing Decisions

**Request**: "Add Stripe checkout to the pricing page"
```
Primary: payment-integration
  Skills: stripe-integration, pci-compliance

Support:
  - frontend-developer (checkout UI)
  - security-auditor (CRITICAL - payment security)
  - test-automator (payment flow tests)

Workflow:
1. payment-integration (Stripe backend setup)
2. frontend-developer (checkout component)
3. test-automator (end-to-end payment tests)
4. security-auditor (final security review)
```

**Request**: "Optimize slow database query"
```
Primary: database-optimizer
  Skills: cost-optimization, prometheus-configuration

Workflow:
1. database-optimizer (analyze, add indexes, fix N+1)
2. test-automator (performance tests)
3. observability-engineer (optional - monitoring)
```

**Request**: "Build React component for displaying quotes"
```
Single Agent: frontend-developer
  Skills: react-modernization, typescript-advanced-types

Reasoning: Simple component, no multi-agent complexity needed
```

---

## When to Invoke agent-selector

Use the agent-selector agent when:
- Request is ambiguous (multiple agent matches)
- Task suggests multi-agent workflow
- Unclear which specialization fits
- Need to plan complex agent sequence
- Optimizing agent usage for performance

---

**This skill auto-activates when analyzing tasks for agent routing.**
**Reference**: Full classifier available in `tools/intent-classifier.md` and `agent-selector.md`
