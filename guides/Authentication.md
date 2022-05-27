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

Authentication Mechanisms:

## Requesting a siteKey <a name="requesting-a-siteKey"></a>

In order to request a siteKey, email the Morf team at [morf@aftia.com]("mailto:morf@aftia.com?subject=Morf siteKey Request") 


Requesting a token, needs:

Valid domains from where the site-key can be used

Header: API-Key

Query Param: site-key

Form configuration (used for render and submission):

"config": {
  "siteKey": "4fbfd303f2f74c6ea2ec3bc9ab44d454",
}
