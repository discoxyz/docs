---
description: How do I get started building with Disco?
---

# ⚒ Get started with Disco's API

## Requirements

You will likely need the following:

* an onboarded Disco Profile
* Any library capable of making http requests (fetch, axios, httpie, etc)
* A valid API token (more below)

## Generate an API Key

Generating an API key is self-service now! **It is no longer a requirement to hold an Organization Credential.**

Simply navigate to your _Profile > Settings ⚙️ > Api Keys > + Create API Key_

<figure><img src="../../.gitbook/assets/Screen Shot 2023-06-28 at 11.14.43 AM.png" alt=""><figcaption></figcaption></figure>

Click “_Create API Key_” to generate your first API key, and enter a Descriptive Name. Remember, each key requires a unique name that reflects its purpose.

When you generate your API key, make sure to copy it as soon as it appears for the first time. The dashboard also provides you with the flexibility to delete existing API keys and create new ones whenever you need to.

<figure><img src="../../.gitbook/assets/Screen Shot 2023-06-28 at 11.16.37 AM.png" alt=""><figcaption><p>Manage your existing API keys</p></figcaption></figure>

## Current Capabilities

* Get all [credentials](credentials.md), by DID or Ethereum Address
* Get a specific [credential](credentials.md) for a Disco Profile&#x20;
* Get a Disco [profile](profiles.md), by DID or Ethereum address
* Fetch a Disco’s [profile](profiles.md) (account linkages, PFP, bio, eth Address)
* Verify a [Credential](credentials.md), either JWT or JSON-LD
* (**NEW**) [Issue a Credential](issue-a-credential-programmatic-issuance.md) to a DID or Ethereum Address

{% hint style="info" %}
**Note:** At Disco we take privacy very seriously. The API will only return credentials that are made _public_ by the user. Credentials are by default, private. \
\
More info on how to make a credential public by toggling the eye icon [here](../../learn-more/faqs.md#does-disco-only-work-for-ethereum).
{% endhint %}



**Sample Request, in curl:**

```sh
curl --location 'https://api.disco.xyz/v1/profile/address/0xc5e46e48f1ef5f305afba45c3122021dd09ed3de' \
--header 'Authorization: Bearer <token>'
```

**Javascript**:

<pre class="language-javascript"><code class="lang-javascript"><strong>var myHeaders = new Headers();
</strong>myHeaders.append("Authorization", "Bearer &#x3C;token>");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://api.disco.xyz/v1/profile/address/0xc5e46e48f1ef5f305afba45c3122021dd09ed3de", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
</code></pre>
