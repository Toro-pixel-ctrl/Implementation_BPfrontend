# GitHub Issues & Project Tracking Guide

This guide defines the standard operating procedure for AI development agents to maintain project discipline and tracking using GitHub issues and milestones for the **Implementation_BPfrontend** project.

## 🎯 Global Objective
Every task, feature, or bug should be represented by a GitHub Issue. Progress must be visible to everyone on the team through real-time updates of issue states and milestone completions.

---

## 🛠 AI Agent Responsibilities

As an AI developer on this project, you **MUST**:
1.  **Check Status First**: At the start of every session, list all open issues to understand the current priorities.
2.  **Issue Creation**: Before starting any non-trivial task, ensure an issue exists for it. If not, create one with a clear title and description.
3.  **Atomic Tasks**: Break down large features into smaller, manageable issues linked to the same milestone.
4.  **Real-Time Lifecycle**: 
    -   Update an issue's status if its scope changes.
    -   Add meaningful comments summarizing progress or blockers.
    -   **Close** the issue immediately after the associated PR is merged or the task is confirmed complete.
5.  **Milestone Discipline**: 
    -   Always check if the current work belongs to an existing milestone.
    -   If a new milestone is needed for a major project phase, suggest its creation to the user.

---

## 📝 Issue Format Guidelines

### 📎 Titles
Use clear, prefix-based titles:
- `feat:` for new features (e.g., `feat: implement mobile responsive hero section`)
- `fix:` for bug fixes (e.g., `fix: navigation menu contrast in dark mode`)
- `refactor:` for code improvements without functional changes.
- `chore:` for maintenance, dependencies, or documentation.

### 📄 Description Template
When creating issues, include:
```markdown
### 🚀 Goal
Briefly describe what needs to be achieved.

### ✅ Acceptance Criteria
- [ ] List specific items...
- [ ] ...that define completion.

### 🔗 Context/Reference
(Optional) Mention related files or previous discussions.
```

---

## 🏗 Milestone Workflow

1.  **Phase Identification**: Organize work into logical phases (e.g., "MVP Landing Page", "Contact Page Integration", "Post-Launch Refinement").
2.  **Tracking Completion**: Every session should strive to move the milestone completion percentage forward.
3.  **End of Session Summary**: Before ending a chat, summarize which issues were closed and how much progress was made toward the current milestone.

---

> [!IMPORTANT]
> **Discipline is non-negotiable.** If a task isn't in an issue, it doesn't exist for project tracking. Always prioritize keeping the GitHub project state synchronized with your local work.
