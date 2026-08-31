---
name: claude-mem
description: An open-source persistent memory plugin (thedotmack/claude-mem) to maintain context across agent sessions.
---

# Claude-Mem

**Repository:** [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem)

`claude-mem` is an open-source, persistent memory plugin designed primarily for AI coding agents. It solves the "amnesia" problem where AI agents forget previous sessions, automatically capturing activity, compressing the information using AI, and storing it for future recall.

## Key Features
- **Persistent Context**: Uses local storage (SQLite) and vector search (Chroma) to automatically track and recall project details, decisions, and user preferences.
- **Context Injection**: Automatically injects relevant past observations into new sessions.
- **Cross-Agent Compatibility**: Works with Claude Code, OpenClaw, Codex, Gemini, and others.

## When to Use
Use this skill when the user wants the AI agent to remember context from past interactions, establish long-term memory for a codebase, or recall specific project architectures and preferences without re-prompting.
