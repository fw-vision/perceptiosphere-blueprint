---
title: "Evening Shutdown Ritual"
type: note
status: ready
created_date: 2026-05-18
tags: ["ritual", "protocol", "cos", "evening", "shutdown"]
---

# Evening Shutdown Ritual

> COS protocol for daily wrap-up. Invoked by Principal saying "evening shutdown", "wrap up", or "end of day".

---

## Protocol Steps

### 1. Review Today's Outcomes

```
ACTION: {{TASK_MANAGER}} → Get today's tasks (with completion status)
```

- Count: completed vs. incomplete
- Identify what got done vs. what didn't
- Note any tasks that were completed but not marked

### 2. Process Incomplete Tasks

For each incomplete task, recommend one of:
- **Defer to tomorrow** → move task to tomorrow
- **Defer to later this week** → move task to specific day
- **Return to backlog** → move task to backlog
- **Delete** (if no longer relevant) → remove task

Present recommendations; await Principal approval before executing.

### 3. Mark Completions

If Principal reports tasks done that aren't marked:
```
ACTION: {{TASK_MANAGER}} → Mark task as completed (today's date)
```

### 4. Capture Wins & Blockers

Ask Principal:
- "What went well today?"
- "What blocked you or took longer than expected?"
- "Any decisions made that should be recorded?"

### 5. Preview Tomorrow

```
ACTION: {{TASK_MANAGER}} → Get tomorrow's tasks
ACTION: {{TASK_MANAGER}} → Get tomorrow's calendar events
```

- Flag early meetings or hard commitments
- Note if tomorrow is already overcommitted

### 6. Set Shutdown Time (Optional)

```
ACTION: {{TASK_MANAGER}} → Record shutdown time (if supported)
```

### 7. Write to Weekly Log

```
ACTION: Append to weekly log file
```

Format:
```markdown
### Evening Shutdown
- Completed: {X}/{Y} tasks
- Deferred to tomorrow: {list}
- Returned to backlog: {list}
- Wins: {from Principal}
- Blockers: {from Principal}
- Decisions: {any strategic decisions captured}
- Tomorrow preview: {X tasks, first commitment at HH:MM}
```

---

## Trigger Phrases

- "Evening shutdown"
- "Wrap up the day"
- "End of day"
- "COS, close it out"
- "Shutdown"

---

## Principles

- Never mark tasks complete without Principal confirmation
- Always suggest deferrals rather than silently dropping tasks
- Keep the log entry concise — details live in task manager history
- If shutdown is late (>10 PM), suggest a lighter protocol (skip preview)
