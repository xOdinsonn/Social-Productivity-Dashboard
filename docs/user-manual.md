# User Manual

This manual outlines the basic day‑to‑day usage of the Social Productivity Dashboard.

## Dashboard Overview

The system centers around an Airtable base with multiple tables that feed custom interfaces. The default views include:

- **Inbox** – a chronological list of all new saves and tasks.
- **Kanban Board** – tasks organized by status (To‑Do, Doing, Done).
- **Timeline** – project schedules across weeks and months.
- **Notes** – linked documentation for each project or save.

Use these interfaces to keep track of incoming information and plan your work.

## Capturing New Saves

1. On mobile, run the **Social Capture** shortcut from the share menu of any app.
2. On desktop, use the browser extension to send the current page to the capture webhook.
3. The link is stored in the `saves` table and automatically tagged by the n8n workflow.
4. Open Airtable to review new entries in the **Inbox** view.

## Converting Saves to Tasks

1. In Airtable, select a save that requires follow‑up.
2. Trigger the **Generate Tasks** automation (from the `task-generation` workflow in n8n).
3. The workflow creates tasks linked back to the original save.
4. Drag tasks across the Kanban board as you work on them.

## Managing Projects

- Use the `projects` table to group tasks and notes under a common initiative.
- Each project can have a dedicated timeline view for scheduling milestones.
- Link saves and notes directly to projects for easy reference.

## Daily Workflow

1. **Morning Review** – check the **Inbox** for new saves and tasks.
2. **Plan Tasks** – move items into the appropriate status column on the Kanban board.
3. **Focus Logging** – create entries in the `focus_logs` table to track time spent.
4. **End‑of‑Day Digest** – review completed tasks and update project timelines.

## Customization Tips

- Modify field names or add new tables to suit your workflow.
- Clone and edit the n8n workflows to integrate additional services.
- Experiment with Airtable Interfaces to build custom dashboards for different projects.

With these basics you can start capturing ideas, turning them into actionable tasks, and tracking progress across your projects.
