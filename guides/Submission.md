# Submitting a Morf Form to a Service

Morf makes it easy to submit your form data to another application for processing using HTTP POST. To specify where a Morf form should submit the data, include the destination URL in the `submit` property of the `config` section of the form definition.

You'll need to ensure the application you are submitting to can accept an HTTP `POST` and is able to process the JSON data payload.

```
{
    "config": {
        "submit": "https://someapplication/someendpoint",
        "siteKey": "4fbfd303f2f74c6ea2ec3bc9ab44d454",
        "successUrl": "https://getmorf.io"
    }
}
```     

Morf will submit a request following construct:

* HTTP Verb: `POST`
* Headers: 
    * `Content-Type`: `multipart/form-data`
    * `X-Proxy-Referer`: `Referer` header value provided during the form submission
    * `X-Proxy-Origin`: `Origin` header value provided during the form submission
    * `X-Proxy-User-Agent`: `User-Agent` header value provided during the form submission
* Body:
    * `data`: `{...}` - parameter containing the form's JSON data
    * `files` `example1.pdf, example2.pdf, ...` - a multi-value parameter containing an array of file attachments.


Also consider providing a `successUrl` in the form definition or in the JSON reponse of your application which will be used to redirect browser after a successful submission.

```
{
    "successUrl": "https://getmorf.io"
}
```
   
