# Embedding a Morf Form into a Web Page 

You may want your Morf form to appear as part of a web page where there are other links, navigation controls and content.  Embedding a Morf form is easy...

<ul>
<li>Step 1
<li>Step 2
<li>Step 3
</ul>


## Testing the embed manually (client side)

```
[
    {
        "text": "window.morfConfig=" + JSON.stringify({
            //root: 'https://render.getmorf.io/v1',
            root: 'http://localhost:8080',
            siteKey: '0494157d3abf4b018fff21d239472533',
            targetId: 'morfcontent',
            definition: {"config":{"submit":"","successUrl":"","theme":"","externalId":""},"head":{"title":"Basic Enrollment Form","logo":"https://tailwindui.com/img/logos/workflow-mark-indigo-600.svg"},"body":{"items":[{"type":"text","label":"First name","placeholder":"E.g. Jane"},{"type":"text","label":"Last name","placeholder":"E.g. Doe","required":true},{"type":"panel","width":"full","label":"Repeating Section (up to 10)","min":1,"max":10,"items":[{"type":"text","placeholder":"Enter a name"},{"type":"text","placeholder":"Enter an email"}]},{"type":"radio","label":"Enrollment type","options":[{"label":"Full-time","value":"full"},{"label":"Part-time","value":"part"},{"label":"As needed","value":"needed"}],"required":true},{"type":"textarea","label":"Enter lots of info","placeholder":"E.g. Some really long content...","width":"full","value":"Lot's of content here\n\n...even more here in fact...\n\n...and here too"},{"type":"submit","label":"Submit"}]}}
        })
    },
    {
        "src": "http://localhost:8080/js/embed.js"
    }
].forEach((script) => {
    const el = document.createElement("script");
    if (script.text) el.innerText = script.text;
    else if (script.src) el.src = script.src;
    document.getElementsByTagName("body")[0].appendChild(el);
});
```