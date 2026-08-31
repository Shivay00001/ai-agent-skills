---
name: open-seo
description: Use this skill for leveraging OpenSEO, an open-source alternative to Semrush and Ahrefs. OpenSEO exposes an MCP server and Agent Skills for SEO workflows like keyword research, rank tracking, competitor insights, backlinks, and site audits.
---

# OpenSEO

OpenSEO is an open-source alternative to Semrush and Ahrefs, designed to provide a pay-as-you-go SEO tool utilizing the DataForSEO API. 

## When to Use This Skill
Use this skill when the user requires:
- Keyword research
- Rank tracking
- Competitor Insights
- Backlinks analysis
- Site Audits
- AI Visibility
- Using SEO data directly with AI agents via MCP (Model Context Protocol).

## Capabilities and Integration
- **MCP Server & Agent Skills**: OpenSEO provides an MCP server so AI agents can natively query SEO data. You can guide agents through SEO tasks using these predefined skills.
- **Self-Hosting Options**: 
  - Simple (Docker for local usage)
  - Advanced (Cloudflare for internet-facing usage)
- **Data Source**: It requires a DataForSEO API key to fetch metrics.

## Important Links
- Repository: [every-app/open-seo](https://github.com/every-app/open-seo)
- Website: [openseo.so](https://openseo.so)
- Local setup docs (in repo): `docs/LOCAL_DEVELOPMENT.md`
- Self-hosting via Docker (in repo): `docs/SELF_HOSTING_DOCKER.md`
- DataForSEO API Key config: `docs/DATAFORSEO_API_KEY.md`
