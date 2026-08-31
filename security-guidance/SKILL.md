---
name: security-guidance
description: Best practices and frameworks for securing Model Context Protocol (MCP) implementations and AI agents.
---

# Security Guidance for AI Agents & MCP

Security in the context of Model Context Protocol (MCP) and AI agents focuses on preventing vulnerabilities introduced by autonomous systems interacting with external tools, APIs, and data.

## Key Frameworks & Risks
1. **OWASP MCP Top 10**: Categorizes the most significant security risks in MCP implementations, such as tool poisoning, prompt injection, and excessive privilege escalation.
2. **Threat Modeling**: Identifying how agents can be manipulated via "indirect prompt injection" (e.g., malicious content in retrieved files).
3. **Least Privilege**: Ensuring MCP servers do not grant agents broader access than strictly necessary.
4. **Authentication & Authorization**: Using robust identity controls and per-request authentication rather than static tokens.

## Implementation Principles
- Never grant wildcard permissions to agents without user oversight.
- Sanitize and validate data returned from external tools (e.g., scraping, GitHub issues) to prevent indirect prompt injection.
- Implement rate limiting and anomaly detection for agent behaviors.

## When to Use
Use this skill when setting up new MCP servers, configuring agent permissions, or when the user requests a security review of their AI agent architecture.
