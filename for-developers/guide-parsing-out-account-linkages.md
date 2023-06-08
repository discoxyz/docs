---
description: >-
  The following guide will help you read credentials from our API, and surface
  them in your DApp, and contains code samples in Javascript.
---

# Guide: Parsing out Account Linkages

**Prerequisites**: This assumes that you already have an existing API key, and you've read the Getting Started guide [here](disco-api-reference/).&#x20;

## To parse out Account Linkages

This also assumes that you have a DApp that uses a wallet connection, to be able to grab the user's ETH Address.\


### Setup

**Make sure you have axios or fetch installed.**&#x20;

`npm install axios`

**Then import it via**&#x20;

```javascript
import axios from 'axios';
```

### Set up Request Headers

```javascript
let config = {
  method: 'get',
  url: 'api.disco.xyz/v1/profile/address/0xc5e46e48f1ef5f305afba45c3122021dd09ed3de',
  headers: { 
    'Authorization': 'Bearer <YOUR_API_KEY_HERE>'
  }
};
```

### &#x20;**Fetch a user's profile via Disco API**

```javascript
axios.request(config)
.then((response) => {
  body = JSON.stringify(response.data)
  console.log(body);
})
.catch((error) => {
  console.log(error);
});
```

Using axios in the example above, the response body will contain a JSON array `linkages`, which will store the Twitter, Discord, and Domain linkages if they exist.

### Save Account Linkage

**To grab an account linkage, we modify the above request:**

```javascript
axios.request(config)
  .then((response) => {
    const body = response.data;
    if (body["linkages"] && body["linkages"]["twitter"]) {
      const twitterAccount = body.linkages.twitter;
      console.log("Twitter Account Linked", twitterAccount);
      //print to console, or save to display in your DApp 
    } else {
      console.log('No Twitter account linkage found.');
    }
...
```

**To check for Discord and/or Domain linkages**, replace the "twitter" key with discord or domain:&#x20;

`body["linkages']["domain"].`

**The following is the JSON body when parsing the result, for a discord account linkage.**

```javascript
"discord": {
            "id": "carlf#3326",
            "host": "discord.com",
            "claim": "https://discord.com/channels/947857036257935390/975763597529600041/1047969370833440858",
            "protocol": "https",
            "attestations": [
                {
                    "did-json-vc": "{\"@context\":[\"https://www.w3.org/2018/credentials/v1\"],\"type\":[\"VerifiableCredential\",\"AccountLinkageCredential\"],\"issuer\":{\"id\":\"did:3:kjzl6cwe1jw147em2rs0sekomnapwb1s4rym9mnib0trdwzr2njq0vgak9ugwxo\"},\"issuanceDate\":\"2022-12-01T20:16:34.918Z\",\"id\":\"did:3:kjzl6cwe1jw147em2rs0sekomnapwb1s4rym9mnib0trdwzr2njq0vgak9ugwxo#e66df33f-df0d-43ec-a7e3-964f9ff88878\",\"credentialSubject\":{\"id\":\"did:3:kjzl6cwe1jw147em2rs0sekomnapwb1s4rym9mnib0trdwzr2njq0vgak9ugwxo\",\"type\":\"Discord\",\"username\":\"carlf#3326\"},\"credentialSchema\":{\"id\":\"https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/AccountLinkageCredential/1-0-0.json\",\"type\":\"JsonSchemaValidator2018\"},\"proof\":{\"verificationMethod\":\"did:3:kjzl6cwe1jw147em2rs0sekomnapwb1s4rym9mnib0trdwzr2njq0vgak9ugwxo#controller\",\"created\":\"2022-12-01T20:16:34.925Z\",\"proofPurpose\":\"assertionMethod\",\"type\":\"EthereumEip712Signature2021\",\"proofValue\":\"0x991fd9e834bca98f033ec25ec5e0d82b20aafa72620616187c72cb9005e10576217aad7b6f2e5f64e266af2ccc663db71d8a1bdd5ed5fa28bad9e0cf242b02a51c\",\"eip712Domain\":{\"domain\":{\"chainId\":1,\"name\":\"Sign to link this account to your identifier\",\"version\":\"1\"},\"messageSchema\":{\"EIP712Domain\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"version\",\"type\":\"string\"},{\"name\":\"chainId\",\"type\":\"uint256\"}],\"CredentialSchema\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"}],\"CredentialSubject\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"},{\"name\":\"username\",\"type\":\"string\"}],\"Issuer\":[{\"name\":\"id\",\"type\":\"string\"}],\"Proof\":[{\"name\":\"created\",\"type\":\"string\"},{\"name\":\"proofPurpose\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"},{\"name\":\"verificationMethod\",\"type\":\"string\"}],\"VerifiableCredential\":[{\"name\":\"@context\",\"type\":\"string[]\"},{\"name\":\"credentialSchema\",\"type\":\"CredentialSchema\"},{\"name\":\"credentialSubject\",\"type\":\"CredentialSubject\"},{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"issuanceDate\",\"type\":\"string\"},{\"name\":\"issuer\",\"type\":\"Issuer\"},{\"name\":\"proof\",\"type\":\"Proof\"},{\"name\":\"type\",\"type\":\"string[]\"}]},\"primaryType\":\"VerifiableCredential\"}}}"
                }
            ]
        }
```













