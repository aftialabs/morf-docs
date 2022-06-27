# Embedding a Morf Form into a Web Page 

You may want your Morf form to appear as part of an existing web page where there are other links, navigation controls and content.  Embedding a Morf form is easy, to start head over to the [Morf Editor](http://editor.getmorf.io/) and follow the steps below:

1. Create or convert a form using the editor
2. If you do not have one already, request a new `siteKey` using the option available in the Editor. For more information, visit the [Authentication](./Authentication.md) documentation
3. Configure the editor to use your `siteKey` using the option available in the Editor
4. Use the Editor option to get a new website embed tag. Have a look at the [Embed tag composition](#embed-tag-composition) section to gain an understanding of the tag structure
5. Copy the tag and add it to any of your existing web pages or application by editing the source HTML content. If you do not have access to the source HTML, have a look at the [Embed demonstration](#embed-demonstration) section to see how the same behavior can be achived when testing locally
6. Refresh or reload the page in question and you should see the Morf form be loaded within the page


## Using the Embed API

For users who are looking for more control of the embedded experience, you may choose to simply invoke the `embed.js` functionality yourself. By adding the following Morf script tag to the current webpage, you will now have access to the embed functionality listed below.

```html
<script src="https://cdn.getmorf.io/js/embed.js"></script>
```

### fetch
`morf.fetch(config: MorfEmbedConfig)` - Fetches, injects, and loads the Morf experience at the specified location    
#### Input
```typescript
{
    siteKey: string; //Site key used for identification
    targetSelector: string; //Injection target selector
    definition: Form; //Local form definition
}
```
#### Output
```
void
```

### load
`morf.load(content: Document, target: HTMLElement)` - Loads a prefetched Morf experience at the specified location
#### Input
```typescript
content: Document; //The prefetched Morf experience
target: HTMLElement; //The target HTML element where the form will be injected
```
#### Output
```
void
```

## Embed tag composition
```html
<div id="morfembed"> <!-- Parent container -->
    <div id="morfcontent"></div> <!-- Injection target. The Morf form will be loaded here -->
    <script type="text/javascript">
    window.morfConfig = {
        siteKey: 'AbC123', //Site key used for identification
        targetSelector: '#morfcontent', //Injection target selector resolved using https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector
        definition: {} //Local form definition (embedded in the current tag)
    };
    </script>
</div>
```


## Embed demonstration

For demonstration purposes, you may not be able to edit the source HTML page as described in step 6. of the [Embedding a Morf Form into a Web Page](#embedding-a-morf-form-into-a-web-page). By following the steps below you can achieve the same behavior when testing locally.

1. Visit the target web page in your browser where you would like to embed the Morf form
2. Using the browser's console, inspect the structure of the current webpage to identify a section where the Morf form should be injected.
3. Fill the required values in the snippet of code below:
    1. `siteKey` - Gather the required `siteKey` configuration by following the steps defined in the [Embedding a Morf Form into a Web Page](#embedding-a-morf-form-into-a-web-page) section
    2. `targetSelector` - Get the section's ID or class attribute in order to formulate a selector. Have a look at the [querySelector](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector) documentation if you are unfamiliar with this syntax.
    3. `definition` - The Morf form JSON object for the form in question
    ```javascript
    [
        {
            "text": "window.morfConfig=" + JSON.stringify({
                siteKey: '', //TODO
                targetSelector: '', //TODO, e.g. #morfcontent
                definition: {} //TODO
            })
        },
        {
            "src": "https://cdn.getmorf.io/js/embed.js"
        }
    ].forEach((script) => {
        const el = document.createElement("script");
        if (script.text) el.innerText = script.text;
        else if (script.src) el.src = script.src;
        document.getElementsByTagName("body")[0].appendChild(el);
    });
    ```
4. Using the browser's console, copy this code snippet in the `Console` tab and execute it to see the Morf form load in the current page
5. *(Optionally)* You can use a browser extention to run this code snippet everytime you visit a certain URL. [Scriptly](https://chrome.google.com/webstore/detail/scripty-javascript-inject/milkbiaeapddfnpenedfgbfdacpbcbam) has been particularily useful in that regard for Google Chrome users.