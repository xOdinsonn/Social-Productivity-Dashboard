# Troubleshooting

This page lists common problems encountered while setting up or running the Social Productivity Dashboard and how to resolve them.

## Workflow Does Not Trigger

- **Symptom:** You run the capture shortcut but nothing appears in Airtable.
- **Fix:** Verify that the webhook URL in the shortcut or extension matches the URL shown in the n8n editor. Make sure the workflow is **active** in n8n.

## Airtable API Authentication Errors

- **Symptom:** n8n executions fail with a 401 error.
- **Fix:** Check that your Airtable API key or access token is correct. Update the credential in n8n and test the connection under **Settings → Credentials**.

## OpenAI Responses Are Empty

- **Symptom:** The task generation workflow runs but does not produce any tasks.
- **Fix:** Confirm that your OpenAI API key is valid and that you have sufficient quota. Review the workflow logs in n8n for any error messages.

## Google Calendar Events Missing

- **Symptom:** Calendar events do not show up in Airtable after the sync workflow runs.
- **Fix:** Ensure the Google credential in n8n has access to your calendar. Double‑check the calendar ID used in the workflow and that the scheduled trigger is enabled.

## General Tips

- Look at the execution logs inside n8n for detailed error messages.
- Test each integration individually before connecting them together.
- When in doubt, deactivate a workflow, duplicate it, and re‑import the original JSON file from this repository.

If an issue persists, open an issue in the repository with as much detail as possible.
