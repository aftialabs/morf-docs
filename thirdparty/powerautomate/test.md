1. Create a new Power Automate Flow.
2. (Optional) Add a "When an HTTP Request is received" trigger. Configure the trigger to accept "GET" requests
3. Add the **Morf Transform JSONata (V1)** operation to the flow
4. Configure the connector authentication by using the provided API Key.
5. Configure the action to use the JSON provided in the attached `morf-test.txt` as a string provided via the `JSON Data` parameter of the action
6. Configure the action to use the content provided in the attached `transform.txt` as a string provided via the `JSONata Expression` parameter of the action
7. Add a new **Morf Render (V1)** operation to the flow
8. Configure the action to use the `Response Result` from the **Morf Transform JSONata (V1)** operation via the Form parameter of the action
9. (Optional) Add an "HTTP Response" action at the end of the flow. Configure the action to return a "Status" of "200", a "Content-Type" header with "text/html", and a "Body" containing the Morf Render action's body.
10. Save and invoke the flow. The result of the Morf Render action should contain an HTML document.
11. (Optional) Once saved, copy the URL from the "When an HTTP Request is received" trigger and paste it in a new browser tab. The Morf form should be presented to the user.