---
name: strix-security-testing
description: Utilize Strix, an open-source AI penetration testing tool, to find and fix vulnerabilities in applications, perform bug bounty reconnaissance, and validate security using real proofs-of-concept.
---

# Strix Security Testing Skill

## Overview
This skill provides instructions for using Strix, an autonomous AI penetration testing agent that discovers and validates vulnerabilities just like a real hacker. Strix can be used for your own apps/projects and for bug bounty programs (e.g., HackerOne).

## Prerequisites
- **Docker** must be installed and running.
- An **LLM API Key** (e.g., OpenAI, Anthropic, Google Gemini).

## Installation
If Strix is not already installed on the system, run:
```bash
curl -sSL https://strix.ai/install | bash
```

## Configuration
Set up the necessary environment variables before running a scan:
```bash
export STRIX_LLM="openai/gpt-5.4" # Or another supported model like vertex_ai/gemini-3-pro-preview
export LLM_API_KEY="your-api-key"
```

*Optional Configuration:*
```bash
export STRIX_REASONING_EFFORT="high" # Control thinking effort
export PERPLEXITY_API_KEY="your-api-key" # For search capabilities
```

## Usage

### 1. Basic Scanning
To scan a local codebase:
```bash
strix --target ./app-directory
```

To perform a black-box web application assessment (Bug Bounty / Live App):
```bash
strix --target https://your-app.com
```

To review a GitHub repository:
```bash
strix --target https://github.com/org/repo
```

### 2. Advanced / Bug Bounty Scenarios
Grey-box authenticated testing (Useful for authenticated Bug Bounty scopes):
```bash
strix --target https://your-app.com --instruction "Perform authenticated testing using credentials: user:pass"
```

Multi-target testing (e.g., source code + deployed app):
```bash
strix -t https://github.com/org/app -t https://your-app.com
```

Focused testing (e.g., hunting for specific bug classes like IDOR or Business Logic Flaws):
```bash
strix --target api.your-app.com --instruction "Focus on business logic flaws and IDOR vulnerabilities"
```

Using a target list (e.g., from subdomain enumeration):
```bash
strix --target-list ./targets.txt
```

### 3. CI/CD Integration
To run headless tests in CI/CD or automated scripts without UI:
```bash
strix -n --target https://your-app.com
```

## Viewing Results
Every scan writes results to disk (in `strix_runs/<run-name>`). To view the detailed report, PoCs, and agent graphs in a local dashboard:
```bash
strix view
# OR
strix view <run-name>
```

## Best Practices & Rules of Engagement
- **Authorization:** ONLY test applications you own or have explicit permission to test (e.g., within the scope of a HackerOne bug bounty program).
- **Scope:** Always check the `scope` and `out of scope` sections of the bug bounty program before pointing Strix at a target. Use the `--instruction-file ./instruction.md` flag to define strict rules of engagement if needed.
- **Reporting:** Strix generates reproducible Proofs of Concept (PoCs). Use these PoCs to write high-quality vulnerability reports.
