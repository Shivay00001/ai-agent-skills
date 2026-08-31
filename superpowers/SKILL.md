---
name: superpowers
description: Implements the obra/superpowers methodology for disciplined AI development, enforcing planning and TDD.
---

# Superpowers Framework

**Repository:** [obra/superpowers](https://github.com/obra/superpowers)

The Superpowers framework is an open-source agentic skills framework created by Jesse Vincent (`obra`). It is designed to act as a "process layer" that guides AI coding agents to follow disciplined engineering habits rather than jumping directly into writing code.

## Key Principles
1. **No "Vibe Coding"**: Forces the agent to think and plan before modifying files.
2. **Test-Driven Development (TDD)**: Enforces writing failing tests before implementing features.
3. **Structured Workflow**:
   - Brainstorming (Clarifying requirements)
   - Git Worktrees (Isolating work)
   - Planning (Creating a roadmap)
   - Execution (Implementing tasks)
   - TDD (Writing tests first)
   - Code Review (Systematic verification)
   - Finishing (Wrapping up)

## When to Use
Use this skill when the user wants to ensure high-quality code generation, specifically emphasizing disciplined planning, test-driven development, and avoiding "AI slop" or regressions.
