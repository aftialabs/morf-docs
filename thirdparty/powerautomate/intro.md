## Morf Connector
Morf is a lightweight API-driven platform for automatically generating forms that can easily be embedded into existing systems, apps, and sites. Morf provides a REST API that can be used to dynamically generate user interfaces and capture information to power your digital processes. Morf simplifies authoring, publishing, and deployment of web based forms allowing businesses to rapidly roll out seamlessly integrated and branded data capture solutions. IT professionals will find that unlike many SaaS forms solutions, Morf easily integrates into their development workflow. Morf allows PowerAutomate users to take advantage of dynamic routing and rendering capabilities and to trigger new flow submissions leveraging a wide range of Microsoft and non-Microsoft products. Morf is an excellent way to trigger and drive forms and document based flows that empower PowerAutomate users to reach new heights in terms of digital maturity.

## Prerequisites
Before using this connector, you will need a **Morf API Key** and a **form definition**. Refer to the [Obtaining Credentials](#obtaining-credentials) and [Getting Started](#getting-started) sections below to get started. 

## Obtaining Credentials
To get started, head over to our [Morf Editor](https://editor.getmorf.io/) and request access keys. You will be granted one (1) site and one (1) API key. As described in our [authentication documentation](https://github.com/aftialabs/morf-docs/blob/main/guides/Authentication.md), use the provided API key when configuring your new Power Platform connection. Our free usage terms are available [here](https://github.com/aftialabs/morf-docs/blob/main/guides/termsandconditions.md#product-description).

## Getting Started
1. To get started, start by creating a Morf form definition. This can be done by using our [Morf Editor](https://editor.getmorf.io/) and creating a new form from scratch or by converting an existing document.
2. With your form definition handy, you can now create a new Power Platform Flow leveraging the Morf Render operation.
3. Configure a new connection if one is not present by adding your Morf API key to the connection configuration. 
4. Configure the action to pass your form definition and optionally data to it, and after invoking your flow you will receive a rendered Morf form.
5. This form can be sent to a user by using many different delivery mechanisms or it can be presented to a user directly using the HTTP Response action.
6. For more information on submitting a form to a Power Platform Flow, have a look at our [documentation](https://github.com/aftialabs/morf-docs/blob/main/guides/PowerAutomate.md).

## Known Issues and Limitations
* Free tier users may experience slower response times during periods of increased usage due to provisioning standards

## Common Errors and Remedies

* Users with a misconfigured or invalid API key will receive an invalid key exception (Error Status: `401`) when calling the service
* In the case of an invalid form definition, the `default` Power Automate retry policy may continue making calls to the render service resulting in multiple errors (Error Status: `500`) until a timeout is reached. Setting the retry policy to `none` or to a defined maximum threshold can help avoid this behavior.

## Frequently Asked Questions

### How are new forms created?
This can be done by using our [Morf Editor](https://editor.getmorf.io/) and creating new forms from scratch or by converting existing documents.

### Can Morf forms be embedded?
Absolutely. Morf forms can be embedded into any web property without the use of inline frames (`iframe`). Get started by heading over to our [Morf Editor](https://editor.getmorf.io/) to generate an embed tag. 

### What makes Morf forms different?
Morf forms use a concept called generational interfaces which allows form definitions to be dynamically modified in real-time when calling our render APIs. This allows for advanced dynamic behavior as part of render logic and operations.

### How do I submit a Morf form?
Morf forms can be submitted to any API that accepts a POST request. Information on submissions can be found [here](https://github.com/aftialabs/morf-docs/blob/main/guides/Submission.md).

### Can Morf forms be submitted to a Power Platform Flow?
Yes! Follow this [guide](https://github.com/aftialabs/morf-docs/blob/main/guides/PowerAutomate.md) to set up your own submission flow.

## Testing the Connector


1. Create a new Power Automate Flow.
2. (Optional) Add a "When an HTTP Request is received" trigger. Configure the trigger to accept "GET" requests
3. Add the Morf Render (V1) operation to the flow
4. Configure the connector authentication by using the provided API Key.
5. Configure the action to use the JSON content provided in the attached morf-test.json as a string provided via the Form parameter of the action
6. (Optional) Add an "HTTP Response" action at the end of the flow. Configure the action to return a "Status" of "200", a "Content-Type" header with "text/html", and a "Body" containing the Morf Render action's body.
7. Save and invoke the flow. The result of the Morf Render action should contain an HTML document.
8. (Optional) Once saved, copy the URL from the "When an HTTP Request is received" trigger and paste it in a new browser tab. The Morf form should be presented to the user.