---
name: awesome-design-md
description: Instructs the agent to leverage the awesome-design-md repository (https://github.com/VoltAgent/awesome-design-md) and the DESIGN.md concept for UI generation in web applications.
---

# Awesome DESIGN.md

This skill integrates the `awesome-design-md` repository as a core reference for building high-quality, visually consistent user interfaces in all future projects.

## Overview
A `DESIGN.md` file is a plain-text design system document that AI agents read to generate consistent UI. It defines the project's look and feel, including tokens, patterns, and design rules, ensuring high-quality UI generation instead of surface-level outputs.

## Agent Instructions

When tasked with building or designing UIs in any upcoming project, you MUST follow these guidelines:

1. **Check for or Create DESIGN.md:**
   - Look for a `DESIGN.md` file in the root of the project.
   - If one doesn't exist and you are starting a new project, propose creating one or fetch a suitable one from the `awesome-design-md` repository based on the user's desired aesthetic (e.g., Vercel, Claude, Linear, etc.).

2. **Reference the Repository:**
   - You can explore the available `DESIGN.md` files from real websites in the curated collection: [https://github.com/VoltAgent/awesome-design-md/tree/main](https://github.com/VoltAgent/awesome-design-md/tree/main).
   - Use these files as a baseline to instruct your UI generation. You can use tools like `read_url_content` to fetch specific markdown files from the repository's main branch if needed.

3. **Strict Adherence:**
   - When writing HTML/CSS or using frameworks, strictly adhere to the styling, typography, color palettes, spacing tokens, and component patterns defined in the active `DESIGN.md`.

4. **Design Quality:**
   - Always prioritize modern, premium designs with proper micro-animations, rich typography, and curated color palettes as guided by the design document.
