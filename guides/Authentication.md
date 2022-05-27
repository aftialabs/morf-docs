# Authenticating with Morf Services

In order to use any Morf Service (API), you must provide a token for authentication.   This token is known as a siteKey and is tied to a specific domain. In the [Morf Editor](https://editor.getmorf.io/#/), you'll notice the siteKey in the config section at the top of the Morf form JSON.

    {
      "config": {
        "submit": "",
        "siteKey": "4fbfd303f2f74c6ea2ec3bc9ab44d454",
        "successUrl": "",
        "theme": "",
        "externalId": ""
      },


This siteKey (4fbfd303f2f74c6ea2ec3bc9ab44d454) is tied to the getmorf.io domain.   Your are prevented from rendering and submitting a Morf form using this siteKey on a domain other than getmorf.io.   In order to render and submit forms on other domains, you'll need to [request a valid siteKey](#requesting-a-siteKey) that is tied to that domain.

## Authentication Mechanisms:

There are two ways of using the siteKey token.  
<UL>
 <li>as part of an API call where the token is present in the header; and 
 <li>as part of a query where the token is present as a parameter in the URL.
</UL>
    
## Requesting a siteKey <a name="requesting-a-siteKey"></a>

In order to request a siteKey, email the Morf team at [morf@aftia.com](mailto:morf@aftia.com?subject=Morf%20siteKey%20Request).  
You'll need to provide: 
<ul>
    <li>your name;
    <li>your organization's name; and
    <li>a valid domain from where the siteKey will be used.
</ul>

Any form submissions using this siteKey will consume one of your organization's licensed submission transactions.   If you are using the Morf free trial a submission will consume one of your 1,000 free transactions.
