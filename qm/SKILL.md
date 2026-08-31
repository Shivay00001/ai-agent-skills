---
name: qm
description: Integrates QM, a multiplayer agent harness for work (https://github.com/yc-software/qm). Use this skill when asked to scaffold, design, or apply the QM agent harness for Slack and the web, providing collaborative and personal agent workspaces.
---

# QM (Multiplayer Agent Harness)

QM is a multiplayer agent harness designed for startups. It provides isolated workspaces for employees to work independently while allowing collaboration with the agent in channels, group messages, and projects.

## Core Concepts
- **Isolated Workspaces:** Each person/room has a scoped memory, files, keychain view, permissions, crons, web apps, and a durable sandbox.
- **Model Agnostic:** Built with open source in mind. You can pick your own harness and model (Pi, OpenCode, Codex, Claude Code).
- **Core Architecture:** Central core using Fastify/Node, with a Postgres persistence layer. The agent uses tools (like `execute` for sandbox commands).
- **Plugins:** Includes plugins for Web UI (Vite/Lit), Admin Panel, Public Portal, and Slack (Bolt).
- **Deployments:** Company-specific configurations, skills, and tools live in a deployment directory validated by the `qm` CLI.

## Agent Instructions

When tasked with building or configuring a QM instance in an upcoming project:

1. **Repository Reference:**
   - Base your implementation on the QM open-source repository: [https://github.com/yc-software/qm](https://github.com/yc-software/qm).

2. **Deployment Directory Structure:**
   - Configure org-level settings, custom tools, shared skills, sandbox images, and infrastructure in the project's **deployment directory**.
   - Ensure the deployment file wires the specific substrate (harness, session store, sandbox, memory).

3. **Slack and Web App Integration:**
   - Keep in mind that identity and configuration carry between Slack and the Web UI.
   - Use the `qm` CLI for validating and deploying configurations.

4. **Background Work and Skills:**
   - Implement background tasks using QM's cron system.
   - Build custom internal web apps and share scope-owned skills by grant or promote them org-wide.
