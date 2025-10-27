#n8n set up

This file contains only concise setup and run instructions for the n8n workflow exported as `Appointment_booking_final.json`.

Prerequisites
-------------
- n8n (self-hosted or n8n cloud) running and accessible.
- Google Cloud project with the Google Calendar API enabled.
- OAuth2 credentials (Client ID & Client Secret) for Google Calendar to use in n8n credentials.
- (Optional) Google PaLM/Gemini API credentials if you want to use the Google language model node included in the workflow.

Important configuration values
------------------------------
- Calendar account: replace the example calendar (e.g. `test@gmail.com`) in the Google Calendar nodes with your target calendar address.
- Timezone: the workflow uses `Asia/Colombo` (UTC+5:30). Adjust if you need a different timezone.
- Webhook: the chat trigger node is a webhook — ensure your n8n instance is reachable by the service that will POST chat messages.

How to import and run the workflow in n8n
----------------------------------------
1. Open your n8n editor UI.
2. Workflows → Import from file → select `Appointment_booking_final.json`.
3. In the imported workflow, open the Credentials panel and configure:
   - Google Calendar OAuth2 credential: create or select OAuth2 credentials with calendar scopes.
   - Google Palm / Gemini credential (if using the model node): add your API key/credential.
4. Update node fields as needed (calendar email, any placeholder IDs, webhook settings).
5. Save the workflow.
6. Activate the workflow (toggle the activation switch) or run it manually for testing.

Testing and verification
------------------------
- To test the webhook trigger, send a POST request from your chat frontend or use a tool like Postman to POST to the webhook URL shown on the chat trigger node.
- Confirm Google Calendar actions by checking the target calendar for created events.

Security & notes
----------------
- Do not commit credentials or secrets to this repository. Use n8n's credential storage.
- Ensure OAuth2 credentials have the required calendar scopes (read/write) for event creation.


Troubleshooting
---------------
- If webhook requests don't reach n8n, verify network access, reverse proxy, and webhook URL.
- If calendar operations fail, re-check the OAuth2 credential and calendar email.

That's all — this README contains only the setup and run instructions for the n8n workflow.
