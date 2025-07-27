# Setup Guide

This guide walks you through getting the Social Productivity Dashboard up and running with Airtable and n8n. The instructions assume you already have accounts for the required services.

## 1. Copy the Airtable Base

1. Open the [`airtable/`](../airtable/) folder of this repository and review the `base-schema.json` to understand the table structure.
2. Log in to Airtable and create a new **workspace**.
3. Click **Add a base → Import a spreadsheet → Upload a JSON file** and select `base-schema.json`.
4. After import, verify the following tables exist:
   - `saves`
   - `tasks`
   - `projects`
   - `notes`
   - `prompts`
   - `sops`
   - `focus_logs`
5. Open the **Interface Designer** and create the kanban and timeline views to match your workflow.

## 2. Import n8n Workflows

1. Deploy n8n either in the cloud or locally. Refer to [n8n.io](https://n8n.io) for installation instructions.
2. Once n8n is running, open the editor and click **Import**.
3. Import the workflow files from the [`n8n-workflows/`](../n8n-workflows/) directory:
   - `social-capture.json`
   - `task-generation.json`
   - `calendar-sync.json`
   - `weekly-digest.json`
4. Each workflow contains placeholder environment variables. Update them under **Settings → Credentials** with your API keys and Airtable base ID.
5. Activate the workflows to start listening for incoming webhooks.

## 3. Configure Integrations

The system relies on several integrations to capture data and generate tasks.

### Raindrop.io

1. Create an API token in your Raindrop.io profile settings.
2. In n8n, add a new **Raindrop** credential using the token.
3. Set the `RAINDROP_TOKEN` variable in the `social-capture` workflow.

### Google Workspace

1. Enable the Calendar and Gmail APIs in the Google Cloud console.
2. Create OAuth credentials and download the `credentials.json` file.
3. Upload this file to your n8n instance and configure **Google** credentials.
4. Update the `calendar-sync` workflow with your calendar ID.

### OpenAI

1. Generate an API key from your OpenAI account.
2. Add a new **OpenAI** credential in n8n and supply the key.
3. Set the `OPENAI_API_KEY` variable in the `task-generation` workflow.

### iOS Shortcuts & Browser Extension

1. Install the shortcut files from the [`ios-shortcuts/`](../ios-shortcuts/) folder on your device.
2. If you prefer desktop capture, load the extension from [`browser-extension/`](../browser-extension/) in developer mode.
3. Set the webhook URL from the `social-capture` workflow as the destination in the shortcut or extension.

## 4. Test the Workflow

1. Use the installed shortcut or extension to save a link.
2. Confirm that a new record appears in the Airtable `saves` table.
3. Check that the `task-generation` workflow creates a matching task in the `tasks` table.
4. Review the dashboard views to ensure everything is connected.

You now have the basics of the Social Productivity Dashboard running. Customize the workflows and Airtable views to suit your needs.
