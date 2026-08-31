---
name: agent-reach
description: Give your AI agent eyes to see the entire internet. Read & search Twitter, Reddit, YouTube, GitHub, Bilibili, XiaoHongShu — one CLI, zero API fees.
---

# Agent-Reach

Agent-Reach is a capability layer that gives AI Agents the ability to read and search across various internet platforms (Twitter, Reddit, YouTube, GitHub, Bilibili, XiaoHongShu, LinkedIn, RSS, web pages) seamlessly without requiring paid APIs. It handles tool selection, installation, and routing automatically.

## When to Use This Skill
Use this skill when the user requires the AI agent to:
- Read or search content on Twitter, Reddit, Facebook, Instagram, XiaoHongShu.
- Fetch and summarize YouTube videos (using subtitles) or Bilibili videos.
- Access GitHub issues, repositories, and discussions.
- Read general web pages (HTML to readable format) or search the web.
- Manage and read RSS feeds.

## Capabilities and Integration
- **Zero API Fees**: Routes to free or existing CLI tools, avoiding paid API endpoints.
- **Platform Support**:
  - Web: Jina Reader
  - Twitter: twitter-cli / OpenCLI / bird
  - YouTube: yt-dlp
  - GitHub: gh CLI
  - Bilibili: bili-cli
  - Reddit, Facebook, Instagram, XiaoHongShu: OpenCLI / MCP / specialized CLIs
  - Search: Exa search via MCP
- **CLI Commands**:
  - `agent-reach doctor`: Checks the health and configuration of all channels.
  - `agent-reach configure <platform>`: Configures a platform (e.g., cookies for XiaoHongShu, Twitter).

## Important Links
- Repository: [Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach)
- Installation Command (for Agents):
  ```bash
  pip install agent-reach
  ```
- Documentation (Install): `https://raw.githubusercontent.com/Panniantong/agent-reach/main/docs/install.md`

## Note for AI Agents
To install this for an agent, simply run the installation script or follow the docs. For some agents like OpenClaw, ensure `exec` permissions are granted (`tools.profile = "coding"`).
