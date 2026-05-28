---
title: "Morning Planning Ritual"
type: note
status: ready
created_date: 2026-05-18
tags: ["ritual", "protocol", "cos", "morning"]
---

# Morning Planning Ritual

> COS protocol for daily planning. Invoked by Principal saying "morning planning" or similar.

---

## Protocol Steps

### 1. Read Today's State

```
ACTION: {{TASK_MANAGER}} → Get today's tasks
ACTION: {{TASK_MANAGER}} → Get today's calendar events
ACTION: {{TASK_MANAGER}} → Get total planned time for today
ACTION: Read weekly log (last entry)
```

### 2. Assess Load

- Calculate total planned time vs. max hours (configurable, e.g., 8-10h)
- Identify overcommitted tasks (those beyond capacity)
- Flag tasks with no time estimate (need estimation)
- Check for tasks aligned to weekly objectives vs. orphan tasks

### 3. Check Weekly Objectives

```
ACTION: {{TASK_MANAGER}} → Get current week's objectives
```

- Are today's tasks advancing any objective?
- Are any objectives at risk of not being met this week?

### 4. Review Backlog for Pulls

```
ACTION: {{TASK_MANAGER}} → Get backlog tasks (first page)
```

- Suggest 0-2 backlog items to pull if capacity exists
- Prioritize: urgent > near-term horizon > objective-aligned

### 5. Recommend Prioritization

Present to Principal:
- **Must do today** (hard deadlines, meetings, commitments)
- **Should do** (objective-aligned, high-value)
- **Could defer** (no deadline, low alignment, overcommitment overflow)
- Suggest reordering if needed

### 6. Capture to Weekly Log

```
ACTION: Append to weekly log file
```

Format:
```markdown
### Morning Planning
- Planned: {X} tasks, {Y}h estimated
- Capacity: {max_hours}h — {"on track" | "overcommitted by Zh"}
- Objectives active: {list}
- Recommended deferrals: {list or "none"}
- Pulled from backlog: {list or "none"}
- Principal directives: {any live input}
```

---

## Trigger Phrases

- "Morning planning"
- "Let's plan today"
- "What's on my plate?"
- "COS, start the day"

---

## Dependencies

- Task manager integration connected (Sunsama, Todoist, Things, etc.)
- Weekly log file exists for current week
- Weekly objectives ideally set (via weekly review)
