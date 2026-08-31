---
name: code-review
description: Utilizes MCP servers and agent skills for automated, context-aware code reviews.
---

# Code Review MCP

**Key Repositories:** 
- [praneybehl/code-review-mcp](https://github.com/praneybehl/code-review-mcp)
- [crazyrabbitLTC/mcp-code-review-server](https://github.com/crazyrabbitLTC/mcp-code-review-server)

The `code-review` skill leverages Model Context Protocol (MCP) to enable AI assistants to perform, assist, or automate code reviews by connecting directly to codebases and GitHub repositories.

## Key Concepts
- **Context-Aware Reviews**: Instead of reviewing a raw diff, the AI uses MCP to access repo structure, documentation, and linked issues to provide accurate feedback.
- **Standardization**: Ensures the AI follows specific team coding standards and security policies consistently across pull requests.

## Implementation Examples
- **GitHub Copilot Code Review**: Configuring MCP servers within repo settings to pull in external context.
- **Custom MCP Servers**: Running local servers that analyze `git diffs` and send them to an LLM to generate feedback on quality, security vulnerabilities, and performance.

## When to Use
Use this skill when the user wants to automate code reviews, analyze pull requests for vulnerabilities or style violations, or integrate AI-driven quality checks into their CI/CD pipeline.
