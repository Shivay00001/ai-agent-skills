---
name: safe-coding-practices
description: Prevents breaking existing code when adding new features and enforces creating a brain.md project tracking file.
---

# Safe Coding Practices & Project Memory

This skill enforces two critical behaviors to ensure project stability and continuous memory:

## 1. Always Create and Maintain `brain.md`
Every time you work on a project, your FIRST step should be to check for or create a `brain.md` file in the root of the workspace.
This file must act as the "brain" or memory of the project and should contain:
- **Project Requirements:** What the project is supposed to do.
- **Current Architecture:** High-level overview of how the pieces fit together.
- **Current State/Progress:** What has been completed, what is pending, and known issues.
- **Important Decisions:** Why certain technical decisions were made.

**Rule:** Continuously update `brain.md` as you make changes so that the next time an agent opens the project, they have full context.

## 2. Never Break Existing Code
When writing new features, changing configurations, or refactoring:
- **Do not break existing functionality.** This is your primary directive.
- **Understand Before Modifying:** Thoroughly read and trace the existing code before changing it. Do not guess.
- **Isolated Changes:** Whenever possible, add new code in a way that minimizes changes to existing core logic.
- **Test Your Changes:** Verify that the existing features still work after your new additions.

If adding a new feature requires modifying existing functionality, do so with extreme caution, ensuring that all dependent parts are updated properly so nothing gets broken in the process.

**Summary:** Remember, building something new is pointless if it destroys what is already working. Create the `brain.md` to keep track of requirements, and code safely!
