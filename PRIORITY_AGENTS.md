# Priority Agents Reference (Enhanced with Skills)

This document provides quick access to the most frequently used agents for your development workflows. Each agent is listed with its purpose, key capabilities, **available skills**, and installed location in the Claude Code plugin system.

**Updated:** All agents now reference their actual installed locations in the Claude Code plugin marketplace.

**New:** Each agent now shows which skills automatically activate from installed plugins when you use them!

---

## 1. Agent Selector ⭐ CRITICAL

**Plugin**: `claude-code-expert` (Custom Marketplace)
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\my-claude-plugins\claude-code-expert\agents\agent-selector.md`
**Model**: Opus
**Use Case**: Intelligent task routing and multi-agent workflow orchestration

### What It Does
Intelligent agent routing specialist that analyzes user requests and determines optimal agent(s), workflow sequence, and multi-agent coordination. This is the **FIRST agent** that should be considered for any complex task requiring agent selection or orchestration.

### Key Capabilities
- **Intent Classification**: Extract keywords, assess complexity, identify ambiguity
- **Agent Matching**: Select primary agents, identify support agents, consider skill auto-activation
- **Workflow Orchestration**: Define sequences (sequential/parallel), plan handoff points, optimize performance
- **Decision Trees**: Single vs multi-agent decisions, model selection (Opus/Sonnet/Haiku)
- **Agent Selection Matrix**: Complete knowledge of all agent specializations (backend, frontend, database, security, testing, payment, DevOps, mobile, AI, debugging, documentation)
- **Multi-Agent Patterns**: Architecture→Implementation→Review, TDD cycles, Security-first, Full-stack features, Performance optimization, Debugging investigations

### 🎯 Available Skills (Auto-Activate)
From `claude-code-expert` plugin:
- **intent-classifier** - Agent routing logic, quick routing matrix, workflow patterns (WORKS HAND-IN-HAND WITH THIS AGENT)

### When to Use
- **PROACTIVELY for ANY complex task** - Before any actual implementation begins
- User request is ambiguous (could match multiple agents)
- Task complexity suggests multi-agent workflow might be better
- Unclear which agent specialization fits best
- Need to plan agent sequence for complex tasks
- Optimizing agent usage for performance
- **Whenever anything requiring agents is detected** - This agent ensures optimal routing

### Why It's #1 Priority
This agent operates at a **meta-level** above all execution agents. It ensures:
1. **Right agent, right time**: Prevents token waste and suboptimal results from poor routing
2. **Progressive complexity**: Starts simple, only escalates when truly needed
3. **Token efficiency**: Avoids redundant invocations, preloads relevant skills
4. **Workflow optimization**: Plans parallel execution, identifies handoff points

Without proper routing, even the best agents can produce suboptimal results. **agent-selector + intent-classifier** work together to ensure every task gets the optimal agent treatment.

---

## 2. Claude Code Expert

**Plugin**: `claude-code-expert` (Custom Marketplace)
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\my-claude-plugins\claude-code-expert\agents\claude-code-expert.md`
**Model**: Sonnet
**Use Case**: Claude Code setup, optimization, and CLAUDE.md creation

### What It Does
Expert in Claude Code usage, setup, optimization, and best practices. Masters agent selection, plugin architecture, CLAUDE.md creation, and system configuration. Teaches users how to maximize their Claude Code experience.

### Key Capabilities
- **System Knowledge**: Plugin system, agent selection, skills auto-activation, progressive disclosure, 65 installed plugins catalog
- **CLAUDE.md Creation**: Generate project-specific configurations (minimal/standard/comprehensive templates)
- **User Onboarding**: Progressive learning paths, common pitfalls, use case mapping
- **Troubleshooting**: Agent selection issues, performance optimization, integration problems, workflow optimization
- **MCP Servers**: Filesystem, GitHub, Brave Search, PostgreSQL, Puppeteer integrations
- **Template Library**: Minimal (simple projects), Standard (most projects), Comprehensive (complex/team projects)

### 🎯 Available Skills (Auto-Activate)
From `claude-code-expert` plugin:
- **doc-template-minimal** - Token-efficient documentation standards (activates on: documentation, docs, README, comment, explain code)
- **intent-classifier** - Agent routing logic for task classification

### When to Use
- **PROACTIVELY when starting new projects** - Set up optimal Claude Code configuration
- User asks: "How do I use Claude Code?", "What can Claude Code do?", "Why isn't X working?"
- Creating CLAUDE.md files for new projects
- Optimizing Claude Code setup for specific tech stacks
- Troubleshooting agent selection or plugin issues
- Teaching users about multi-agent workflows
- Explaining plugin/agent/skill architecture

### Available Commands
- `/claude-code-expert:help` - Show available agents and commands for current project
- `/claude-code-expert:explain-routing` - Explain why specific agents were chosen
- `/claude-code-expert:best-practices` - Show Claude Code optimization tips
- `/claude-code-expert:create-claude-md` - Generate project-specific CLAUDE.md file

---

## 3. Backend Architect

**Plugin**: `backend-development`
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\claude-code-workflows\plugins\backend-development\agents\backend-architect.md`
**Model**: Opus
**Use Case**: API design, multi-tenant architecture, pricing engine logic

### What It Does
Expert backend architect specializing in scalable API design, microservices architecture, and distributed systems. Masters REST/GraphQL/gRPC APIs, event-driven architectures, service mesh patterns, and modern backend frameworks.

### Key Capabilities
- **API Design**: RESTful APIs, GraphQL, gRPC, WebSocket, versioning strategies
- **Microservices**: Service boundaries, communication patterns, service discovery, API Gateway
- **Event-Driven**: Message queues, Kafka, event sourcing, pub/sub patterns
- **Security**: OAuth 2.0, JWT, RBAC, ABAC, rate limiting, input validation
- **Resilience**: Circuit breaker, retry patterns, timeout management, graceful degradation
- **Observability**: Structured logging, metrics, distributed tracing, APM integration

### 🎯 Available Skills (Auto-Activate)
- **api-design-principles** - REST/GraphQL best practices, API design checklist
- **architecture-patterns** - Clean Architecture, Hexagonal Architecture, DDD
- **microservices-patterns** - Service boundaries, event-driven communication, resilience
- **fastapi-templates** - Production-ready FastAPI patterns (when using Python)

### When to Use
- Designing new backend services or APIs from scratch
- Planning microservices architecture and service boundaries
- Implementing authentication/authorization systems
- Creating event-driven architectures
- Building resilient, observable backend systems

---

## 4. Security Auditor

**Plugin**: `comprehensive-review` / `security-compliance` / `security-scanning`
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\claude-code-workflows\plugins\comprehensive-review\agents\security-auditor.md`
**Model**: Opus
**Use Case**: Security reviews, RLS policy validation, permission enforcement

### What It Does
Expert security auditor specializing in DevSecOps, comprehensive cybersecurity, and compliance frameworks. Masters vulnerability assessment, threat modeling, secure authentication (OAuth2/OIDC), OWASP standards, cloud security, and security automation.

### Key Capabilities
- **DevSecOps**: SAST, DAST, IAST, dependency scanning in CI/CD pipelines
- **Authentication**: OAuth 2.0/2.1, OpenID Connect, SAML, WebAuthn, zero-trust architecture
- **OWASP**: Top 10 vulnerabilities, ASVS, SAMM, threat modeling (STRIDE, PASTA)
- **Testing**: Static analysis (SonarQube, CodeQL), dynamic analysis (OWASP ZAP, Burp Suite)
- **Cloud Security**: AWS Security Hub, Azure Security Center, GCP Security Command Center
- **Compliance**: GDPR, HIPAA, PCI-DSS, SOC 2, ISO 27001, NIST Cybersecurity Framework

### 🎯 Available Skills (Auto-Activate)
From `security-scanning` plugin:
- **sast-configuration** - Configure SAST tools for vulnerability detection

From `kubernetes-operations` plugin:
- **k8s-security-policies** - Kubernetes NetworkPolicy, PodSecurityPolicy, RBAC

From `blockchain-web3` plugin (when working with blockchain):
- **solidity-security** - Smart contract security auditing

### When to Use
- Conducting comprehensive security audits
- Implementing authentication and authorization systems
- Validating Row-Level Security (RLS) policies
- Setting up DevSecOps pipelines
- Ensuring compliance with regulatory frameworks
- Reviewing security-critical code changes

---

## 5. Database Optimizer

**Plugin**: `database-cloud-optimization` / `database-migrations` / `observability-monitoring`
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\claude-code-workflows\plugins\database-cloud-optimization\agents\database-optimizer.md`
**Model**: Opus
**Use Case**: Query performance, indexing, multi-tenant data isolation

### What It Does
Expert database optimizer specializing in modern performance tuning, query optimization, and scalable architectures. Masters advanced indexing, N+1 resolution, multi-tier caching, partitioning strategies, and cloud database optimization.

### Key Capabilities
- **Query Optimization**: Execution plan analysis, query rewriting, complex query patterns
- **Advanced Indexing**: B-tree, Hash, GiST, GIN, BRIN, covering indexes, composite indexes
- **Performance Monitoring**: pg_stat_statements, Performance Schema, real-time monitoring
- **N+1 Resolution**: ORM optimization, eager loading, batch queries, DataLoader patterns
- **Caching**: Multi-tier caching (L1/L2/L3), Redis Cluster, cache invalidation strategies
- **Scaling**: Horizontal partitioning, sharding, read replicas, write optimization

### 🎯 Available Skills (Auto-Activate)
From `cloud-infrastructure` plugin:
- **cost-optimization** - Cloud cost optimization, rightsizing, reserved instances

From `framework-migration` plugin:
- **database-migration** - Zero-downtime migration strategies

From `observability-monitoring` plugin:
- **prometheus-configuration** - Setup Prometheus for database monitoring

### When to Use
- Optimizing slow queries and database performance
- Designing indexing strategies for high-traffic applications
- Eliminating N+1 query problems in ORMs
- Implementing multi-tier caching architectures
- Planning database sharding and scaling strategies
- Ensuring multi-tenant data isolation and performance

---

## 6. Test Automator

**Plugin**: `unit-testing` / `full-stack-orchestration` / `performance-testing-review`
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\claude-code-workflows\plugins\unit-testing\agents\test-automator.md`
**Model**: Sonnet
**Use Case**: Test generation for pricing calculations and RLS policies

### What It Does
Master AI-powered test automation with modern frameworks, self-healing tests, and comprehensive quality engineering. Build scalable testing strategies with advanced CI/CD integration.

### Key Capabilities
- **TDD Excellence**: Red-green-refactor cycle automation, Chicago School & London School TDD
- **AI-Powered Testing**: Self-healing test automation, AI-driven test generation, visual AI testing
- **Modern Frameworks**: Playwright, Selenium, Appium, Postman, K6, Pact
- **CI/CD Integration**: Parallel execution, dynamic test selection, containerized environments
- **Performance Testing**: Load testing, stress testing, API performance, SLA validation
- **Quality Engineering**: Test pyramid, risk-based testing, shift-left practices

### 🎯 Available Skills (Auto-Activate)
From `python-development` plugin:
- **python-testing-patterns** - Pytest patterns, fixtures, mocking, parametrization

From `javascript-typescript` plugin:
- **javascript-testing-patterns** - Jest/Vitest patterns, Testing Library, mocks

From `blockchain-web3` plugin (blockchain projects):
- **web3-testing** - Smart contract testing with Hardhat/Foundry

From `shell-scripting` plugin (shell scripts):
- **bats-testing-patterns** - Bash testing patterns

### When to Use
- Generating comprehensive test suites for new features
- Testing pricing calculations and business logic
- Validating RLS policies and multi-tenant isolation
- Setting up test automation frameworks
- Implementing TDD workflows
- Creating performance and load tests

---

## 7. Frontend Developer

**Plugin**: `frontend-mobile-development` / `multi-platform-apps` / `application-performance`
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\claude-code-workflows\plugins\frontend-mobile-development\agents\frontend-developer.md`
**Model**: Sonnet
**Use Case**: React components, TypeScript implementation, state management

### What It Does
Build React components, implement responsive layouts, and handle client-side state management. Masters React 19, Next.js 15, and modern frontend architecture. Optimizes performance and ensures accessibility.

### Key Capabilities
- **React 19**: Server Components, Actions, async transitions, concurrent rendering
- **Next.js 15**: App Router, Server Actions, streaming patterns, Edge runtime
- **State Management**: Zustand, Jotai, React Query, SWR, Context API optimization
- **Styling**: Tailwind CSS, CSS-in-JS, design systems, responsive design
- **Performance**: Core Web Vitals, code splitting, image optimization, lazy loading
- **Testing**: React Testing Library, Jest, Playwright, Storybook, visual regression

### 🎯 Available Skills (Auto-Activate)
From `framework-migration` plugin:
- **react-modernization** - Upgrade React apps, migrate to hooks, concurrent features

From `javascript-typescript` plugin:
- **modern-javascript-patterns** - ES6+ features, async/await, functional programming
- **typescript-advanced-types** - Advanced TypeScript patterns and generics
- **nodejs-backend-patterns** - Node.js backend patterns (for full-stack work)

### When to Use
- Building React components and user interfaces
- Implementing TypeScript-based frontend applications
- Creating responsive layouts and design systems
- Optimizing frontend performance and Core Web Vitals
- Setting up state management and data fetching
- Ensuring accessibility compliance

---

## 8. UI/UX Designer

**Plugin**: `multi-platform-apps`
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\claude-code-workflows\plugins\multi-platform-apps\agents\ui-ux-designer.md`
**Model**: Sonnet
**Use Case**: Interface design, wireframes, extravagant user experience

### What It Does
Create interface designs, wireframes, and design systems. Masters user research, accessibility standards, and modern design tools. Specializes in design tokens, component libraries, and inclusive design.

### Key Capabilities
- **Design Systems**: Atomic design, design tokens, component libraries, multi-brand architecture
- **Modern Tools**: Figma advanced features (Auto Layout, Variants, Variables), Storybook integration
- **User Research**: Qualitative/quantitative research, usability testing, journey mapping, personas
- **Accessibility**: WCAG 2.1/2.2 compliance, inclusive design, screen reader optimization
- **Information Architecture**: Site mapping, navigation hierarchy, content strategy
- **Visual Design**: Typography systems, color theory, layout principles, iconography

### 🎯 Available Skills (Auto-Activate)
From `framework-migration` plugin:
- **react-modernization** - Modern React component patterns for design systems

From `javascript-typescript` plugin:
- **modern-javascript-patterns** - JavaScript patterns for interactive prototypes

### When to Use
- Designing user interfaces and experiences
- Creating design systems and component libraries
- Conducting user research and usability testing
- Ensuring accessibility and inclusive design
- Building wireframes and prototypes
- Establishing brand identity and visual consistency

---

## 9. Payment Integration

**Plugin**: `payment-processing`
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\claude-code-workflows\plugins\payment-processing\agents\payment-integration.md`
**Model**: Sonnet
**Use Case**: Payment gateway integration, company creation flow

### What It Does
Integrate Stripe, PayPal, and payment processors. Handles checkout flows, subscriptions, webhooks, and PCI compliance.

### Key Capabilities
- **Payment Processors**: Stripe, PayPal, Square API integration
- **Checkout Flows**: Payment forms, one-click checkout, saved payment methods
- **Subscriptions**: Recurring billing, plan management, prorated upgrades/downgrades
- **Webhooks**: Event handling, retry logic, idempotency
- **Security**: PCI compliance, tokenization, secure data handling
- **Error Handling**: Failed payments, disputes, refunds, retry strategies

### 🎯 Available Skills (Auto-Activate)
From `payment-processing` plugin:
- **stripe-integration** - Stripe checkout, subscriptions, webhooks, payment intents
- **paypal-integration** - PayPal express checkout, subscriptions, dispute handling
- **pci-compliance** - PCI DSS compliance for secure payment handling
- **billing-automation** - Automated billing systems, recurring payments, invoicing

### When to Use
- Integrating payment gateways (Stripe, PayPal, Square)
- Building checkout and payment flows
- Implementing subscription billing systems
- Setting up webhook handlers for payment events
- Ensuring PCI compliance and payment security
- Handling payment errors and edge cases

---

## 10. TypeScript Pro

**Plugin**: `javascript-typescript`
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\claude-code-workflows\plugins\javascript-typescript\agents\typescript-pro.md`
**Model**: Sonnet
**Use Case**: Type-safe code, pricing calculation functions, validation logic

### What It Does
Master TypeScript with advanced types, generics, and strict type safety. Handles complex type systems, decorators, and enterprise-grade patterns.

### Key Capabilities
- **Advanced Types**: Generics, conditional types, mapped types, template literal types
- **Strict Configuration**: Compiler options, type checking, error prevention
- **Type Inference**: Utility types, type guards, discriminated unions
- **Decorators**: Metadata programming, class decorators, method decorators
- **Module Systems**: ES modules, namespace organization, declaration files
- **Framework Integration**: React, Node.js, Express type-safe patterns

### 🎯 Available Skills (Auto-Activate)
From `javascript-typescript` plugin:
- **typescript-advanced-types** - Generics, conditional types, mapped types, utility types
- **modern-javascript-patterns** - ES6+ patterns that complement TypeScript
- **nodejs-backend-patterns** - Type-safe Node.js backend patterns

### When to Use
- Writing type-safe TypeScript code
- Creating complex pricing calculation functions
- Building validation logic with type guarantees
- Designing advanced type systems and generics
- Optimizing TypeScript configuration
- Creating type declaration files for libraries

---

## 11. TDD Orchestrator

**Plugin**: `tdd-workflows` / `backend-development`
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\claude-code-workflows\plugins\tdd-workflows\agents\tdd-orchestrator.md`
**Model**: Opus
**Use Case**: Test-driven development workflows, test-first approach

### What It Does
Master TDD orchestrator specializing in red-green-refactor discipline, multi-agent workflow coordination, and comprehensive test-driven development practices. Enforces TDD best practices across teams with AI-assisted testing.

### Key Capabilities
- **TDD Discipline**: Red-green-refactor cycle enforcement, test-first verification
- **Multi-Agent Coordination**: Specialized testing agent orchestration, parallel test development
- **Modern TDD**: Chicago School (state-based), London School (mockist), ATDD, BDD
- **AI-Assisted Testing**: Intelligent test generation, test data creation, predictive failure analysis
- **Test Architecture**: Test pyramid optimization, test categorization, isolation verification
- **Metrics**: Cycle time tracking, coverage analysis, quality assessment through mutation testing

### 🎯 Available Skills (Auto-Activate)
From `python-development` plugin:
- **python-testing-patterns** - Python TDD patterns, pytest, fixtures

From `javascript-typescript` plugin:
- **javascript-testing-patterns** - JavaScript TDD patterns, Jest, mocking

### When to Use
- Implementing test-driven development workflows
- Coordinating multiple testing agents
- Establishing TDD discipline across teams
- Generating AI-assisted tests
- Tracking TDD metrics and compliance
- Refactoring legacy code with test safety nets

---

## 12. Code Reviewer

**Plugin**: `comprehensive-review` / `code-documentation` / `codebase-cleanup`
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\claude-code-workflows\plugins\comprehensive-review\agents\code-reviewer.md`
**Model**: Opus
**Use Case**: Security-focused code reviews, best practices analysis

### What It Does
Elite code review expert specializing in modern AI-powered code analysis, security vulnerabilities, performance optimization, and production reliability. Masters static analysis tools, security scanning, and configuration review.

### Key Capabilities
- **AI-Powered Analysis**: Integration with modern AI review tools (GitHub Copilot, Codiga)
- **Static Analysis**: SonarQube, CodeQL, Semgrep, security-focused scanning
- **Security Review**: OWASP Top 10, input validation, authentication/authorization
- **Performance Analysis**: Database query optimization, N+1 detection, memory leak analysis
- **Configuration Review**: Production configs, database settings, infrastructure as code
- **Modern Practices**: TDD compliance, BDD scenarios, contract testing, feature flags

### 🎯 Available Skills (Auto-Activate)
From `security-scanning` plugin:
- **sast-configuration** - Static analysis tool configuration

From `backend-development` plugin:
- **api-design-principles** - API design best practices review
- **architecture-patterns** - Architectural pattern compliance

### When to Use
- Conducting comprehensive code reviews
- Analyzing security vulnerabilities
- Reviewing performance implications
- Validating configuration changes
- Ensuring production reliability
- Enforcing coding standards and best practices

---

## 13. Debugger

**Plugin**: `debugging-toolkit` / `error-debugging` / `unit-testing`
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\claude-code-workflows\plugins\debugging-toolkit\agents\debugger.md`
**Model**: Sonnet
**Use Case**: Error resolution and root cause analysis

### What It Does
Debugging specialist for errors, test failures, and unexpected behavior. Focuses on root cause analysis and minimal fixes.

### Key Capabilities
- **Error Analysis**: Stack trace interpretation, error message analysis
- **Root Cause**: Hypothesis formation and testing, isolation techniques
- **Strategic Logging**: Debug logging placement, variable state inspection
- **Fix Implementation**: Minimal code fixes, symptom vs. cause distinction
- **Verification**: Solution testing, regression prevention
- **Documentation**: Root cause explanation, prevention recommendations

### 🎯 Available Skills (Auto-Activate)
From `observability-monitoring` plugin:
- **distributed-tracing** - Distributed system debugging with Jaeger/Tempo

### When to Use
- Debugging errors and test failures
- Analyzing stack traces and error messages
- Finding root causes of unexpected behavior
- Implementing fixes for production issues
- Verifying solutions and preventing regressions

---

## 14. Error Detective

**Plugin**: `distributed-debugging` / `error-debugging` / `error-diagnostics`
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\claude-code-workflows\plugins\distributed-debugging\agents\error-detective.md`
**Model**: Sonnet
**Use Case**: Stack trace investigation and bug hunting

### What It Does
Search logs and codebases for error patterns, stack traces, and anomalies. Correlates errors across systems and identifies root causes.

### Key Capabilities
- **Log Analysis**: Parsing, regex patterns, error extraction across log formats
- **Pattern Recognition**: Error correlation, time-based analysis, deployment correlation
- **Distributed Systems**: Cross-service error correlation, cascading failure detection
- **Anomaly Detection**: Error rate changes, spike detection, baseline comparison
- **Query Building**: Elasticsearch, Splunk, log aggregation queries
- **Monitoring**: Prevention strategies, recurrence detection queries

### 🎯 Available Skills (Auto-Activate)
From `observability-monitoring` plugin:
- **distributed-tracing** - Trace requests across distributed systems
- **grafana-dashboards** - Create dashboards for error monitoring

### When to Use
- Investigating production errors and failures
- Analyzing logs across distributed systems
- Detecting error patterns and anomalies
- Correlating errors with deployments
- Building monitoring queries for error detection
- Hunting bugs across multiple services

---

## 15. Prompt Engineer

**Plugin**: `llm-application-dev`
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\claude-code-workflows\plugins\llm-application-dev\agents\prompt-engineer.md`
**Model**: Opus
**Use Case**: AI prompt optimization, Claude/GPT API integration, agent configuration

### What It Does
Expert prompt engineer specializing in advanced prompting techniques, LLM optimization, and AI system design. Masters chain-of-thought, constitutional AI, and production prompt strategies.

### Key Capabilities
- **Advanced Techniques**: Chain-of-thought, constitutional AI, meta-prompting, self-improvement
- **Model Optimization**: OpenAI GPT-4o, Anthropic Claude, Llama, model-specific tuning
- **Production Systems**: Prompt templates, dynamic templating, version control, A/B testing
- **RAG Integration**: Retrieval-augmented generation, context compression, hallucination reduction
- **Agent Prompting**: Multi-agent systems, role definition, tool selection, collaboration protocols
- **Evaluation**: Performance metrics, testing methodologies, safety assessment

### 🎯 Available Skills (Auto-Activate)
From `llm-application-dev` plugin:
- **langchain-architecture** - LangChain agents, memory, tool integration
- **prompt-engineering-patterns** - Advanced prompting techniques, few-shot learning
- **rag-implementation** - RAG systems with vector databases, semantic search
- **llm-evaluation** - Comprehensive LLM evaluation strategies

### When to Use
- Building AI features and LLM integrations
- Optimizing prompts for Claude or GPT APIs
- Configuring agent systems and workflows
- Creating chain-of-thought reasoning systems
- Implementing constitutional AI patterns
- Designing multi-agent collaboration systems

---

## 16. Mobile Developer

**Plugin**: `frontend-mobile-development` / `multi-platform-apps`
**Installed Location**: `C:\Users\antho\.claude\plugins\marketplaces\claude-code-workflows\plugins\frontend-mobile-development\agents\mobile-developer.md`
**Model**: Sonnet
**Use Case**: PWA optimization, mobile-responsive implementation, app store preparation

### What It Does
Expert mobile developer specializing in cross-platform development, PWA optimization, and mobile-first design. Masters React Native, Flutter, and native iOS/Android development with modern architecture patterns.

### Key Capabilities
- **PWA Excellence**: Service workers, offline functionality, install prompts, responsive design
- **Mobile Optimization**: Touch interfaces, performance on mobile networks, battery efficiency
- **Cross-Platform**: React Native, Flutter, Ionic with Capacitor for web-to-mobile transitions
- **Responsive Design**: Mobile-first layouts, touch targets, viewport optimization, gesture handling
- **Performance**: Startup time optimization, lazy loading, image optimization, code splitting
- **Testing**: Mobile device testing, responsive testing, performance profiling on mobile

### 🎯 Available Skills (Auto-Activate)
From `framework-migration` plugin:
- **react-modernization** - Modern React patterns for mobile development

From `javascript-typescript` plugin:
- **typescript-advanced-types** - Type-safe mobile development
- **modern-javascript-patterns** - JavaScript patterns for mobile apps

### When to Use
- Optimizing Tradesphere web app for mobile browsers
- Implementing PWA features (offline mode, install prompts, push notifications)
- Ensuring responsive design works smoothly on all mobile devices
- Testing mobile performance and user experience
- Preparing codebase for future iOS/Android app store deployment
- Creating documentation for future native app conversion

### ⚠️ Tradesphere Context

**Current State**: Tradesphere is a web application with PWA functionality. Focus on ensuring all operations work smoothly on mobile browsers.

**Future State**: Will be adapted to full native apps for iOS App Store and Google Play Store.

**Agent Behavior**:
- **Implement mobile-optimized code** for current PWA functionality
- **Add code comments** when encountering code that will need iOS/Play Store specific adaptations
- **Create standalone documentation** noting future pivot points for native app conversion
- **Work with ui-ux-designer** for mobile-responsive design implementation
- **Tag technical debt** related to web-specific patterns that won't work in native apps

**Documentation Format**:
```
// TODO: [NATIVE-APP] This implementation uses web-specific APIs
// For iOS/Android: Replace with platform-specific alternative
// See: docs/native-app-migration.md
```

---

## Quick Reference Table

| Agent | Model | Primary Use Case | Key Strength | Skills Available |
|-------|-------|------------------|--------------|------------------|
| **agent-selector** ⭐ | Opus | Task Routing | Intelligent multi-agent orchestration | 1 skill |
| **claude-code-expert** | Sonnet | Claude Code Setup | System optimization & CLAUDE.md creation | 2 skills |
| **backend-architect** | Opus | API Design | Scalable microservices architecture | 4 skills |
| **security-auditor** | Opus | Security Reviews | OWASP compliance & DevSecOps | 3 skills |
| **database-optimizer** | Opus | Query Performance | Advanced indexing & caching | 3 skills |
| **test-automator** | Sonnet | Test Generation | AI-powered TDD automation | 4 skills |
| **frontend-developer** | Sonnet | React Components | Next.js 15 & React 19 expertise | 4 skills |
| **ui-ux-designer** | Sonnet | Interface Design | Accessibility-first design systems | 2 skills |
| **payment-integration** | Sonnet | Payment Processing | Stripe/PayPal integration | 4 skills |
| **typescript-pro** | Sonnet | Type Safety | Advanced TypeScript patterns | 3 skills |
| **tdd-orchestrator** | Opus | TDD Workflows | Red-green-refactor discipline | 2 skills |
| **code-reviewer** | Opus | Code Quality | Security & performance analysis | 3 skills |
| **debugger** | Sonnet | Error Resolution | Root cause analysis | 1 skill |
| **error-detective** | Sonnet | Log Analysis | Pattern recognition & correlation | 2 skills |
| **prompt-engineer** | Opus | AI Integration | Chain-of-thought & constitutional AI | 4 skills |
| **mobile-developer** | Sonnet | PWA & Mobile | Mobile-first optimization & native prep | 3 skills |

**Total: 16 agents with 46 auto-activating skills**

---

## How Skills Work

### Automatic Activation
Skills activate automatically when you use an agent and mention relevant keywords:

```
You: "Use backend-architect to design a FastAPI REST API"
→ Activates: api-design-principles, architecture-patterns, fastapi-templates skills

You: "Use payment-integration to implement Stripe checkout"
→ Activates: stripe-integration, pci-compliance, billing-automation skills

You: "Use test-automator to generate pytest tests"
→ Activates: python-testing-patterns skill
```

### Progressive Disclosure
Skills load knowledge on-demand for token efficiency:
1. **Metadata** (always loaded): Name and activation criteria
2. **Instructions** (loaded when activated): Core patterns and guidance
3. **Resources** (loaded on request): Examples, templates, code snippets

### Verification
To confirm skills are active, ask:
```
"What skills are you using for this task?"
```

---

## Usage Tips

1. **Use PROACTIVELY**: These agents are designed to be invoked before issues arise
2. **Combine Agents**: Multiple agents can work together (e.g., backend-architect + security-auditor)
3. **Respect Agent Boundaries**: Each agent defers to others for specialized work
4. **Model Selection**: Opus for complex architecture/strategy, Sonnet for implementation
5. **Mention Technologies**: Explicitly mention FastAPI, Stripe, React, etc. to activate relevant skills
6. **File Paths**: All agents live in `agents/` directory with `.md` extension

---

## See Also

- [INSTALLED_PLUGINS_CATALOG.md](INSTALLED_PLUGINS_CATALOG.md) - Complete catalog of all 65 installed plugins with agents, skills, and commands
- [WEBSITE-PRIORITY-AGENTS.md](WEBSITE-PRIORITY-AGENTS.md) - Website-specific agents (18 agents)
- [docs/agent-skills.md](docs/agent-skills.md) - Complete skills documentation (47 skills)
- [docs/plugins.md](docs/plugins.md) - Plugin documentation
- [CLAUDE.md](CLAUDE.md) - Safety guide and configuration instructions
- [CREATING-AGENTS-PLUGINS.md](CREATING-AGENTS-PLUGINS.md) - Guide for creating custom agents and plugins
