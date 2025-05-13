# 🧠 Model Context Protocol for Linear (Python)

This project defines a **Model Context Protocol (MCP)** that integrates with the [Linear GraphQL API](https://developers.linear.app/docs/graphql/overview) to provide structured, actionable context for Large Language Models (LLMs). The goal is to enable advanced roadmap generation, gap analysis, issue creation, and visualization — all driven by your team's real-time Linear data.

---

## 🚀 Purpose

This protocol enables LLMs to:
- Ingest and understand the current state of work (issues, projects, cycles)
- Identify gaps, tech debt, and emergent themes
- Propose or create new issues and initiatives
- Visualize progress and plan future work

Ideal for product, platform, and strategy teams using Linear + LLMs.

---

## 📦 Functional Scope

### ✅ Read Operations (Context Ingestion)
| Function | Description |
|----------|-------------|
| `get_assigned_issues(user_id=None)` | Fetches issues assigned to a user |
| `get_all_issues(filters=None)` | Retrieves all issues (with optional filters) |
| `get_issue_details(issue_id)` | Full detail view of an issue |
| `get_all_projects()` | Lists all projects |
| `get_project_details(project_id)` | Metadata and progress of a project |
| `get_current_user()` | Fetches authenticated user info |
| `get_team_members(team_id)` | For capacity and team-based planning |
| `get_all_cycles()` | For sprint/iteration analysis |
| `get_roadmaps()` | (Optional) Linear roadmap integration |

---

### ✍️ Write Operations (LLM Actions)
| Function | Description |
|----------|-------------|
| `create_issue(data)` | Create new issues |
| `update_issue(issue_id, updates)` | Modify issue content/state |
| `assign_issue(issue_id, user_id)` | Set ownership |
| `move_issue_to_cycle(issue_id, cycle_id)` | Schedule issue |
| `create_project(data)` | Initiate LLM-suggested projects |

---

### 📊 Analytical Functions
| Function | Description |
|----------|-------------|
| `group_issues_by_project()` | Roll-up view of work per initiative |
| `get_unassigned_issues()` | Surface work needing triage |
| `get_stale_issues(days_old=30)` | Identify neglected issues |
| `get_backlog_items()` | Low-priority or unscheduled work |
| `get_issues_by_label(label)` | For theme-based grouping |
| `get_dependencies(issue_id)` | Trace upstream/downstream work |

---

## 🧠 LLM Context Format

LLMs receive structured summaries like:

```json
{
  "team_goals": "...",
  "current_projects": [...],
  "issues_by_theme": {
    "AI Enablement": [...],
    "Tech Debt": [...]
  },
  "gaps_identified": [...],
  "suggested_initiatives": [...]
}
