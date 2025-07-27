# API Reference

This section outlines the main endpoints and data structures used by the Social Productivity Dashboard. The platform primarily relies on Airtable's API and n8n webhook URLs.

## Airtable Tables

The following tables are used across the system. Each record corresponds to a JSON object when accessed via the Airtable REST API.

| Table | Purpose | Key Fields |
| ----- | ------- | ---------- |
| `saves` | Stores bookmarks and captured links. | `url`, `title`, `source`, `status` |
| `tasks` | Actionable items generated from saves or created manually. | `name`, `project`, `status`, `due_date` |
| `projects` | High‑level initiatives that group tasks. | `name`, `description`, `owner` |
| `notes` | Reference material linked to saves or projects. | `title`, `content`, `linked_record` |
| `focus_logs` | Time tracking entries. | `task`, `start`, `end` |

### Example Record
```json
{
  "id": "rec123456",
  "fields": {
    "name": "Draft launch email",
    "status": "To‑Do",
    "project": ["recProj001"],
    "due_date": "2025-08-15"
  }
}
```

## n8n Webhooks

Several n8n workflows expose webhook endpoints. They can be triggered by external services or shortcuts.

- **Social Capture** – accepts `POST` requests with `url` and `title` parameters. Adds a row to `saves`.
- **Task Generation** – triggered from Airtable automations, uses OpenAI to create tasks.
- **Calendar Sync** – runs on a schedule to pull events from Google Calendar.
- **Weekly Digest** – compiles activity from the week and sends an email summary.

Each webhook URL is available from the n8n editor after you activate the workflow.

## Authentication

Airtable API requests require an API key or personal access token. Store these credentials securely in n8n and do not commit them to the repository.

This reference will expand as additional endpoints and integrations are added.
