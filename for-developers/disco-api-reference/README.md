---
description: How do I get started building with Disco?
---

# ⚒ Getting Started with Disco's API

## Requirements

You will likely need the following:

* an onboarded Disco Profile
* Any library capable of making http requests (fetch, axios, httpie, etc)
* A valid API token (more below)

### Getting Started

<details>

<summary>Request an API Key</summary>

Please fill out [this](https://discoxyz.typeform.com/requestapi) typeform here and we'll get you an API key as soon as possible.&#x20;

</details>

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
More info on how to make a credential public here
{% endhint %}





