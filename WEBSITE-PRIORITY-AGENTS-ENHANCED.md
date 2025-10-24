# Website Priority Agents Reference (Enhanced with Skills)

This document provides quick access to the **essential agents for Tradesphere SaaS website development** with **available skills** that auto-activate when you use them.

**Purpose**: Streamlined reference for the most critical website development agents with explicit skill mapping.

**New:** Each agent now shows which skills automatically activate!

---

## 🎯 Frontend Stack

### 1. Frontend Developer
**File**: [`agents/frontend-developer.md`](agents/frontend-developer.md) | **Model**: Sonnet

Build React components, implement responsive layouts, and handle client-side state management. Masters React 19, Next.js 15, and modern frontend architecture.

**Key Capabilities**: React 19, Next.js 15, State Management (Zustand, React Query), Tailwind CSS, Core Web Vitals optimization

**🎯 Available Skills (Auto-Activate)**:
- **react-modernization** - Upgrade React apps, hooks, concurrent features
- **modern-javascript-patterns** - ES6+, async/await, functional programming
- **typescript-advanced-types** - Advanced TypeScript patterns
- **nodejs-backend-patterns** - Node.js patterns for full-stack work

**When to Use**: Building UI components, implementing TypeScript frontend, responsive layouts, performance optimization

---

### 2. UI/UX Designer
**File**: [`agents/ui-ux-designer.md`](agents/ui-ux-designer.md) | **Model**: Sonnet

Create interface designs, wireframes, and design systems. Masters user research, accessibility standards, and modern design tools.

**Key Capabilities**: Design systems, Figma, user research, WCAG 2.1/2.2 accessibility, component libraries

**🎯 Available Skills (Auto-Activate)**:
- **react-modernization** - Modern React component patterns
- **modern-javascript-patterns** - JavaScript for interactive prototypes

**When to Use**: Designing interfaces, creating design systems, usability testing, accessibility compliance, wireframes

---

### 3. Mobile Developer
**File**: [`agents/mobile-developer.md`](agents/mobile-developer.md) | **Model**: Sonnet

Expert mobile developer specializing in PWA optimization and mobile-first design. Masters cross-platform development.

**Key Capabilities**: PWA (service workers, offline, install prompts), mobile optimization, responsive design, touch interfaces

**🎯 Available Skills (Auto-Activate)**:
- **react-modernization** - Modern React patterns for mobile
- **typescript-advanced-types** - Type-safe mobile development
- **modern-javascript-patterns** - JavaScript patterns for mobile apps

**When to Use**: PWA features, mobile browser optimization, responsive testing, future native app preparation

**⚠️ Tradesphere Context**: Currently building PWA. Add comments for future iOS/Android native app adaptations. Document migration points.

---

## 🔧 Backend Stack

### 4. Backend Architect
**File**: [`agents/backend-architect.md`](agents/backend-architect.md) | **Model**: Opus

Expert backend architect specializing in scalable API design, microservices architecture, and distributed systems.

**Key Capabilities**: REST/GraphQL/gRPC APIs, microservices, event-driven architecture, OAuth 2.0/JWT, resilience patterns

**🎯 Available Skills (Auto-Activate)**:
- **api-design-principles** - REST/GraphQL best practices
- **architecture-patterns** - Clean Architecture, Hexagonal, DDD
- **microservices-patterns** - Service boundaries, event-driven communication
- **fastapi-templates** - Production-ready FastAPI patterns

**When to Use**: API design, multi-tenant architecture, pricing engine logic, authentication systems, microservices

---

### 5. Database Architect
**File**: [`agents/database-architect.md`](agents/database-architect.md) | **Model**: Opus

Expert database architect with **direct access to Tradesphere production database via PostgreSQL MCP**.

**Key Capabilities**: Schema design, normalization, multi-tenant patterns, indexing strategy, migration planning, Supabase

**🎯 Available Skills (Auto-Activate)**:
- **database-migration** - Zero-downtime migration strategies
- **terraform-module-library** - Terraform modules for RDS/database infrastructure

**When to Use**: Schema design, data modeling, migrations, selecting database technologies, creating ERDs

**⚠️ CRITICAL**: PostgreSQL MCP connected to production Supabase. **Always query live database FIRST** before any architecture work.

---

### 6. Database Optimizer
**File**: [`agents/database-optimizer.md`](agents/database-optimizer.md) | **Model**: Opus

Expert database optimizer specializing in performance tuning, query optimization, and scalable architectures.

**Key Capabilities**: Query optimization, advanced indexing, N+1 resolution, multi-tier caching, partitioning, sharding

**🎯 Available Skills (Auto-Activate)**:
- **cost-optimization** - Cloud cost optimization, rightsizing
- **database-migration** - Migration performance strategies
- **prometheus-configuration** - Database performance monitoring

**When to Use**: Slow queries, indexing strategies, N+1 problems, caching, multi-tenant data isolation

---

## 🔒 Security Stack

### 7. Security Auditor
**File**: [`agents/security-auditor.md`](agents/security-auditor.md) | **Model**: Opus

Expert security auditor specializing in DevSecOps, cybersecurity, and compliance frameworks.

**Key Capabilities**: DevSecOps (SAST/DAST), OAuth 2.0/OIDC, OWASP Top 10, static/dynamic analysis, compliance (GDPR, SOC 2)

**🎯 Available Skills (Auto-Activate)**:
- **sast-configuration** - Configure SAST tools for vulnerability detection
- **k8s-security-policies** - Kubernetes security policies (if using K8s)
- **pci-compliance** - PCI DSS compliance (for payment processing)

**When to Use**: Security audits, RLS policy validation, authentication systems, DevSecOps pipelines, compliance

---

### 8. Frontend Security Coder
**File**: [`agents/frontend-security-coder.md`](agents/frontend-security-coder.md) | **Model**: Sonnet

Expert in secure frontend coding practices specializing in XSS prevention and client-side security.

**Key Capabilities**: XSS prevention, Content Security Policy, secure storage, token handling, OAuth implementation

**🎯 Available Skills (Auto-Activate)**:
- **modern-javascript-patterns** - Secure JavaScript patterns
- **typescript-advanced-types** - Type-safe security implementations

**When to Use**: Secure frontend features, client-side security reviews, CSP setup, sensitive data handling

---

### 9. Backend Security Coder
**File**: [`agents/backend-security-coder.md`](agents/backend-security-coder.md) | **Model**: Sonnet

Expert in secure backend coding practices specializing in input validation and API security.

**Key Capabilities**: Input validation, JWT/OAuth, RBAC/ABAC, rate limiting, SQL injection prevention

**🎯 Available Skills (Auto-Activate)**:
- **api-design-principles** - Secure API design patterns
- **fastapi-templates** - Secure FastAPI patterns (when using Python)

**When to Use**: Secure backend APIs, authentication/authorization, input validation, multi-tenant security

---

## ⚡ Performance & Quality

### 10. Performance Engineer
**File**: [`agents/performance-engineer.md`](agents/performance-engineer.md) | **Model**: Opus

Expert performance engineer specializing in Core Web Vitals, load testing, and optimization.

**Key Capabilities**: Core Web Vitals (LCP, FID, CLS), load testing (k6, Gatling), multi-tier caching, OpenTelemetry

**🎯 Available Skills (Auto-Activate)**:
- **python-performance-optimization** - Python code profiling and optimization
- **distributed-tracing** - OpenTelemetry, Jaeger, Tempo tracing
- **prometheus-configuration** - Prometheus metrics collection
- **grafana-dashboards** - Performance visualization dashboards

**When to Use**: Core Web Vitals optimization, load testing, caching strategies, performance bottlenecks

---

### 11. Observability Engineer
**File**: [`agents/observability-engineer.md`](agents/observability-engineer.md) | **Model**: Opus

Build production-ready monitoring, logging, and tracing systems. SLI/SLO management and incident response.

**Key Capabilities**: Monitoring (Prometheus, Grafana), structured logging, distributed tracing, SLI/SLO, alerting

**🎯 Available Skills (Auto-Activate)**:
- **prometheus-configuration** - Setup Prometheus monitoring
- **grafana-dashboards** - Create production dashboards
- **distributed-tracing** - Implement distributed tracing
- **slo-implementation** - Define SLIs/SLOs with error budgets

**When to Use**: Monitoring infrastructure, dashboards, distributed tracing, SLIs/SLOs, incident response

---

## 🧪 Testing Stack

### 12. Code Reviewer
**File**: [`agents/code-reviewer.md`](agents/code-reviewer.md) | **Model**: Opus

Elite code review expert with **access to Tradesphere production database via PostgreSQL MCP**.

**Key Capabilities**: AI-powered analysis, static analysis (SonarQube, CodeQL), security review, performance analysis, TDD compliance

**🎯 Available Skills (Auto-Activate)**:
- **sast-configuration** - Static analysis tool configuration
- **api-design-principles** - API design review
- **architecture-patterns** - Architectural pattern compliance

**When to Use**: Code reviews, security analysis, performance implications, configuration validation

**⚠️ CRITICAL**: Can validate database-related code against actual production schema via PostgreSQL MCP.

---

### 13. Test Automator
**File**: [`agents/test-automator.md`](agents/test-automator.md) | **Model**: Sonnet

Master AI-powered test automation with modern frameworks and comprehensive quality engineering.

**Key Capabilities**: TDD automation, AI-powered testing, Playwright/Selenium, CI/CD integration, performance testing

**🎯 Available Skills (Auto-Activate)**:
- **python-testing-patterns** - Pytest patterns, fixtures, mocking
- **javascript-testing-patterns** - Jest/Vitest patterns, Testing Library

**When to Use**: Test generation for pricing calculations, RLS policies, test automation frameworks, load tests

---

### 14. Debugger
**File**: [`agents/debugger.md`](agents/debugger.md) | **Model**: Sonnet

Debugging specialist for errors, test failures, and unexpected behavior. Root cause analysis and minimal fixes.

**Key Capabilities**: Stack trace interpretation, root cause analysis, strategic logging, minimal fixes, regression prevention

**🎯 Available Skills (Auto-Activate)**:
- **distributed-tracing** - Distributed system debugging

**When to Use**: Debugging errors, analyzing stack traces, finding root causes, production issues

---

## 🔍 SEO Stack

### 15. SEO Structure Architect
**File**: [`agents/seo-structure-architect.md`](agents/seo-structure-architect.md) | **Model**: Sonnet

Analyzes and optimizes content structure including header hierarchy, schema markup, and internal linking.

**Key Capabilities**: H1-H6 optimization, schema markup (JSON-LD), internal linking, URL structure, XML sitemaps

**🎯 Available Skills (Auto-Activate)**:
- *No specific skills - uses core SEO knowledge*

**When to Use**: Structuring pages, implementing schema markup, internal linking strategy, technical SEO

---

### 16. SEO Meta Optimizer
**File**: [`agents/seo-meta-optimizer.md`](agents/seo-meta-optimizer.md) | **Model**: Sonnet

Creates optimized meta titles, descriptions, and URLs. Generates compelling, keyword-rich metadata.

**Key Capabilities**: Meta titles/descriptions, URL structure, Open Graph tags, Twitter cards, SERP preview

**🎯 Available Skills (Auto-Activate)**:
- *No specific skills - uses core SEO knowledge*

**When to Use**: Creating meta tags, optimizing metadata, improving CTR from search results, social media tags

---

### 17. SEO Content Writer
**File**: [`agents/seo-content-writer.md`](agents/seo-content-writer.md) | **Model**: Sonnet

Writes SEO-optimized content based on keywords and topic briefs. Creates engaging, comprehensive content.

**Key Capabilities**: Long-form content, natural keyword integration, compelling copy, optimal readability, E-E-A-T principles

**🎯 Available Skills (Auto-Activate)**:
- *No specific skills - uses core content writing knowledge*

**When to Use**: Writing blog posts, landing pages, product descriptions, SEO-friendly copy

---

### 18. SEO Content Auditor
**File**: [`agents/seo-content-auditor.md`](agents/seo-content-auditor.md) | **Model**: Sonnet

Analyzes content for quality, E-E-A-T signals, and SEO best practices. Scores content and provides recommendations.

**Key Capabilities**: Quality analysis, E-E-A-T signals, technical SEO, content scoring, actionable recommendations

**🎯 Available Skills (Auto-Activate)**:
- *No specific skills - uses core SEO auditing knowledge*

**When to Use**: Auditing content quality, identifying improvements, E-E-A-T compliance, pre-publication scoring

---

## Quick Reference Table

| # | Agent | Model | Primary Use | Skills Available |
|---|-------|-------|-------------|------------------|
| 1 | **frontend-developer** | Sonnet | React/Next.js components | 4 skills |
| 2 | **ui-ux-designer** | Sonnet | Design systems & wireframes | 2 skills |
| 3 | **mobile-developer** | Sonnet | PWA & mobile optimization | 3 skills |
| 4 | **backend-architect** | Opus | API design & microservices | 4 skills |
| 5 | **database-architect** | Opus | Schema design (live DB access) | 2 skills |
| 6 | **database-optimizer** | Opus | Query performance & caching | 3 skills |
| 7 | **security-auditor** | Opus | Security audits & compliance | 3 skills |
| 8 | **frontend-security-coder** | Sonnet | XSS prevention & client security | 2 skills |
| 9 | **backend-security-coder** | Sonnet | Input validation & API security | 2 skills |
| 10 | **performance-engineer** | Opus | Core Web Vitals & optimization | 4 skills |
| 11 | **observability-engineer** | Opus | Monitoring & distributed tracing | 4 skills |
| 12 | **code-reviewer** | Opus | Code reviews (live DB access) | 3 skills |
| 13 | **test-automator** | Sonnet | Test generation & automation | 2 skills |
| 14 | **debugger** | Sonnet | Error resolution & root cause | 1 skill |
| 15 | **seo-structure-architect** | Sonnet | Schema markup & structure | Core SEO |
| 16 | **seo-meta-optimizer** | Sonnet | Meta tags & URLs | Core SEO |
| 17 | **seo-content-writer** | Sonnet | SEO-optimized content | Core SEO |
| 18 | **seo-content-auditor** | Sonnet | Content quality & E-E-A-T | Core SEO |

**Total: 18 agents with 39 auto-activating skills**

---

## How Skills Work for Tradesphere

### Automatic Activation Examples

```
You: "Use frontend-developer to build a React dashboard"
→ Activates: react-modernization, modern-javascript-patterns, typescript-advanced-types

You: "Use backend-architect to design the pricing API with FastAPI"
→ Activates: api-design-principles, architecture-patterns, fastapi-templates

You: "Use database-optimizer to fix slow queries in Supabase"
→ Activates: cost-optimization, prometheus-configuration

You: "Use performance-engineer to optimize Core Web Vitals"
→ Activates: python-performance-optimization, grafana-dashboards

You: "Use test-automator to generate pytest tests for pricing"
→ Activates: python-testing-patterns
```

### Progressive Disclosure (Token Efficient)
1. **Metadata** (always loaded): Skill name, activation criteria
2. **Instructions** (loaded when activated): Core patterns
3. **Resources** (on demand): Examples, templates, code

### Verification
Ask: `"What skills are you using for this task?"`

---

## Common Workflows

### 🎨 New Feature
1. **ui-ux-designer** → Design (react-modernization skill)
2. **frontend-developer** → Implement (4 skills activate)
3. **mobile-developer** → Optimize for mobile (3 skills activate)
4. **backend-architect** → Design APIs (4 skills activate)
5. **database-architect** → Schema changes (2 skills activate)
6. **test-automator** → Tests (2 skills activate)
7. **code-reviewer** → Review (3 skills activate)

### 🔒 Security
1. **security-auditor** → Audit (3 skills activate)
2. **backend-security-coder** → Backend implementation (2 skills activate)
3. **frontend-security-coder** → Frontend implementation (2 skills activate)
4. **code-reviewer** → Security review (3 skills activate)
5. **test-automator** → Security tests (2 skills activate)

### ⚡ Performance
1. **performance-engineer** → Identify bottlenecks (4 skills activate)
2. **database-optimizer** → Optimize queries (3 skills activate)
3. **frontend-developer** → Optimize frontend (4 skills activate)
4. **mobile-developer** → Mobile performance (3 skills activate)
5. **observability-engineer** → Monitoring (4 skills activate)

### 🔍 SEO
1. **seo-structure-architect** → Structure & schema
2. **seo-meta-optimizer** → Meta tags
3. **seo-content-writer** → Write content
4. **seo-content-auditor** → Audit & score

---

## Tradesphere-Specific Notes

### Database Access with Skills
- **database-architect** + **database-optimizer** have PostgreSQL MCP → production Supabase
- Skills provide migration patterns, optimization strategies, cost optimization
- Always query live database before schema work
- Use read-only queries to validate assumptions

### PWA Focus with Skills
- **mobile-developer** primary for PWA (activates 3 skills)
- **react-modernization** skill provides modern patterns
- **typescript-advanced-types** ensures type safety
- Document future native app migration points with comments

### Multi-Tenant Architecture with Skills
- **backend-architect** (4 skills for multi-tenant patterns)
- **database-optimizer** (3 skills for RLS policy performance)
- **security-auditor** (3 skills for tenant isolation)
- **architecture-patterns** skill provides DDD patterns

### Pricing Engine with Skills
- **typescript-pro** (3 skills for type-safe calculations)
- **test-automator** (2 skills for comprehensive pricing tests)
- **backend-architect** (4 skills for pricing API design)
- **python-testing-patterns** or **javascript-testing-patterns** activate based on language

---

## Usage Tips

1. **Mention Technologies Explicitly**: Say "FastAPI", "React", "Stripe" to activate relevant skills
2. **Skills Auto-Activate**: Just use the agent naturally - skills load based on context
3. **Progressive Loading**: Skills load incrementally to save tokens
4. **Combine Agents**: Multiple agents can work together, each bringing their skills
5. **Verify Skills**: Ask "What skills are active?" to see what's loaded

---

## See Also

- [PRIORITY_AGENTS-ENHANCED.md](PRIORITY_AGENTS-ENHANCED.md) - General development agents (14 agents, 43 skills)
- [docs/agent-skills.md](docs/agent-skills.md) - Complete skills documentation (47 total skills)
- [docs/plugins.md](docs/plugins.md) - All 63 plugins
- [CLAUDE.md](CLAUDE.md) - Safety guide and configuration instructions
- [agents/README.md](agents/README.md) - Complete agent documentation (all 84 agents)
