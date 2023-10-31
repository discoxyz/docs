---
description: General steps to implement based on events in applications and onchain
---

# Automatically Issue Verifiable Credentials

**Automatically Issue Verifiable Credentials (VCs)**

Issue credentials automatically when certain events occur, such as when a user completes specific actions, swaps a token, completes a level in a game, or mints an NFT. Set up logic and by programmatically issuing VCs to their ETH address or DID.

**Prerequisites**&#x20;

Generate a [did:web](https://docs.disco.xyz/disco-docs/for-organizations/did-web-for-organizations?utm\_source=substack\&utm\_medium=email) to ensure credentials are signed with keys that you control

**How it works:**

1. Select event(s) that will results in credential issuance&#x20;
2. Leverage our API endpoint and set up logic in your platform to issue credentials
   * Determine if a credential is issued to a user's Eth address or DID&#x20;
3. &#x20;User receives credentials&#x20;

<img src="../../.gitbook/assets/file.excalidraw (1).svg" alt="" class="gitbook-drawing">



## API Endpoint  &#x20;

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/credential" method="post" expanded="true" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

### Usage example

{% tabs %}
{% tab title="Curl" %}
```bash
curl --location 'https://api.disco.xyz/v1/credential' \
--header 'Content-Type: application/json' \
--header 'Accept: */*' \
--header 'Authorization: Bearer <your Disco API key>' \
--data '{
    "issuer": "did:3:123abcexample",
    "schemaUrl": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json",
    "recipientDID": "did:3:456defexample",
    "subjectData": {
        "memberId": "123XYZ",
        "membershipDescription": "Demo membership to showcase Disco API",
        "membershipLevel": "Permanent",
        "membershipType": "Developer",
        "organization": "Disco.xyz"
    },
    "expirationDate": ""
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Accept", "*/*");
myHeaders.append("Authorization", "Bearer <your Disco API key>");

var raw = JSON.stringify({
  "issuer": "did:3:123abcexample",
  "schemaUrl": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json",
  "recipientDID": "did:3:456defexample",
  "subjectData": {
    "memberId": "123XYZ",
    "membershipDescription": "Demo membership to showcase Disco API",
    "membershipLevel": "Permanent",
    "membershipType": "Developer",
    "organization": "Disco.xyz"
  },
  "expirationDate": ""
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.disco.xyz/v1/credential", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
{% endtab %}
{% endtabs %}

###

```
```
