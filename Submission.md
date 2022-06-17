# Submitting a Morf Form to a Service

Morf makes it easy to submit your form data to another application for processing using HTTP POST. To specify where a Morf form should submit the data, include the destination URL in the `submit` property of the `config` section of the form design.
You'll need to ensure the application you are submitting to can accept an HTTP POST and knows how to process the JSON data payload.



```
"config": {
    "submit": "https://someapplication/someendpoint",
    "siteKey": "4fbfd303f2f74c6ea2ec3bc9ab44d454",
    "successUrl": "getmorf.io",
    "theme": "",
    "externalId": ""
}
```     
Also consider providing a `successUrl` which is where the browser will redirect to after a successful submission. 

Morf will submit a `multipart/form-data` POST call to the endpoint and submit 2 parameters, a `data` parameter containing the form's JSON data, and a multi-value `files` parameter containing an array of file attachments.


   
