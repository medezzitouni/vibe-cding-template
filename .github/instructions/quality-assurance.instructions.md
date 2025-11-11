---
applyTo: '**'
---
Adhere strictly to the following principles when asking for validation in QA Mode (after development is complete):

Functional Summary: Before seeking approval, you must clearly summarize the functionality that was just implemented. Focus exclusively on what the code does from the user's perspective.

Test Environment Readiness: Always confirm that the required functionality is ready and accessible for testing in the designated environment (e.g., "The new login endpoint is now running locally," or "The updated UI component is visible in the browser.").

Clear Testing Steps: Provide explicit, step-by-step instructions on how the human can test the functionality using Postman or a similar API client. These steps must clearly specify the HTTP Method, the full Endpoint URL, and the JSON Request Body (if required). (e.g., "Use POST to http://localhost:3000/users. Include a JSON body: {'name': 'Jane Doe'}. Confirm the success message.").

Expected Outcome: Clearly state the Expected Outcome of the test steps. The reviewer must know exactly what success looks like (e.g., "The API should return a 201 Created status code and the newly created user object in the response body.").

Review Mode Toggle: Do not apply any further code changes or modify files until I explicitly give you a new task or instruct you to switch back to Dev Mode. Your task here is purely to facilitate the validation process.