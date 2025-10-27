---
name: explain-routing
description: Explain why specific agents were chosen for the last task
---

# Explain Agent Routing Command

You are being invoked via the `/claude-code-expert:explain-routing` slash command.

## Task

Explain the agent routing decision for the user's most recent request or a specific task they mention.

## Steps

1. **Identify the task**:
   - Look at the user's most recent request
   - Or ask them to specify which task they want explained

2. **Analyze routing decision**:
   - Which agent(s) handled the task?
   - Why were those agents chosen?
   - What keywords/context triggered the selection?
   - Which skills auto-activated?

3. **Show the reasoning**:
   - Primary agent and why it was selected
   - Support agents (if any) and their roles
   - Workflow sequence (if multi-agent)
   - Alternative agents that could have been used

4. **Suggest optimizations** (if applicable):
   - Could different agents have been better?
   - Should project CLAUDE.md add custom triggers?
   - Are there skills that could help?

## Output Format

```markdown
# Agent Routing Explanation

## Task Analyzed
[Restate the user's request]

## Routing Decision
**Primary Agent:** [agent-name] ([plugin-name])
**Model:** [Opus/Sonnet/Haiku]

**Why this agent:**
- [Reason 1: keyword match]
- [Reason 2: specialization fit]
- [Reason 3: skills available]

**Skills Auto-Activated:**
- [skill-name]: [what it provides]
- [skill-name]: [what it provides]

[If multi-agent:]
**Support Agents:**
1. [agent-name]: [their role in the workflow]
2. [agent-name]: [their role]

**Workflow Sequence:**
[Step-by-step of how agents worked together]

## Alternative Approaches
[If applicable: other agents that could have handled this]
[Why the chosen approach was preferred]

## Optimization Suggestions
[If project could benefit from CLAUDE.md customization]
[If different agent would be better in the future]

## Questions?
Ask: "Why didn't you use [agent-name] instead?" for deeper explanation.
```

## Important Notes

- Reference the intent-classifier skill for routing logic
- Be transparent about reasoning
- Suggest improvements when relevant
- Help users understand the decision-making process
